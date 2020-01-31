# How.Safe.Is.Safe.An.Empirical.Study.on.Rust.Safety.and.Unsafe.Mechanisms

## Summary

This paper did extensive research on current rust projects and summarized the known bugs in it.
First, this paper did a review of rust safety mechanisms and then dive into unsafe usages and found that unsafe can be used as a marker and sometimes can be removed.

It also discovered three main bugs: Memory errors, Un-blocking bugs and Blocking bugs.

### Memory Issues

**Buffer overflow**

**Null pointer dereference**

**Reading uninitialized memory**

**Invalid free**
```rust
1 pub struct FILE {
2       buf: Vec<u8>,
3 }
4
5 pub unsafe fn _fdopen(...) {
6       let f = alloc(size_of::<FILE>()) as * mut FILE;
7 -     *f = FILE{buf: vec![0u8; 100]};
8 +     ptr::write(f, FILE{buf: vec![0u8; 100]});
9 }
```

**Use after free**

```rust
1  pub fn sign(data: Option<&[u8]>) {
2  -    let p = match data {
3  -        Some(data) => BioSlice::new(data).as_ptr(),
4  -        None => ptr::null_mut(),
5  -    };
6  +    let bio = match data {
7  +        Some(data) => Some(BioSlice::new(data)),
8  +        None => None,
9  +    };
10 +    let p = bio.map_or(ptr::null_mut(),|p| p.as_ptr());
11
12      unsafe {
13           let cms = cvt_p(CMS_sign(p));
14      }
15 }
```
**Double free**


### Non-blocking bugs

```rust
1  pub struct EpochState {
2       pub garbage: ConcBag,
3  }
4  static EPOCH: AtomicUsize = //addr of EpochState object
5  //how to share the global EpochState
6  pub fn get() -> &’static EpochState {
7       let mut addr = EPOCH.load(Relaxed);
8       unsafe { &*(addr as *mut EpochState) }
9  }
10 //effect of the bug
11 impl ConcBag {
12      pub unsafe fn collect(&self) {
13 -        let mut head = self.head.load(Relaxed);
14 -        self.head.store(ptr::null_mut(), Relaxed);
15 +        head = self.head.swap(ptr::null_mut(), Acquire);
16          while head != ptr::null_mut() {
17              //free the linked list
18          }
19      }
20 }
21 //how to trigger the bug
22 //try_collect can be called by multiple threads
23 pub fn try_collect(...) {
24      ...
25      get().garbage.collect();
26 }
```

```rust
1  - static CHECKED: AtomicBool = false;
2  + static CHECKER: Once = ONCE_INIT;
3  static AVAILABLE: AtomicBool = false;
4  fn is_getrand_available() -> bool {
5  -    if !CHECKED.load(Ordering::Relaxed) {
6  +    CHERKER.call_once(|| {
7           let result = getrand(...);
8           let available = if result == -1 {
9               ...
10              } else {
11                  true
12              };
13 -            CHECKED.store(true, Ordering::Relaxed);
14              AVAILABLE.store(available, Ordering::Relaxed);
15 -            available
16 -    } else {
17 -        AVAILABLE.load(Ordering::Relaxed)
18      }
19      AVAILABLE.load(Ordering::Relaxed)
20 }
```

### Blocking bugs

```rust
1 fn do_request() {
2       //client: Arc<RwLock<Inner>>
3 -     match connect(client.read().unwrap().m) {
4 +     let result = connect(client.read().unwrap().m);
5 +     match result {
6           Ok(_) => {
7               let mut inner = client.write().unwrap();
8               inner.m = mbrs;
9           }
10          Err(_) => {}
11      }
12 }
```

## Further reading

[Fearless Concurrency? Understanding Concurrent Programming Safety in Real-World Rust Software](https://arxiv.org/pdf/1902.01906.pdf)

## bib

This is a paper still under review. 

This paper is published by [Zhang Yiying](https://cseweb.ucsd.edu/~yiying) in UCSD.