# [50.Ways.to.Leak.Your.Data.An.Exploration.of.Apps’.Circumvention.of.the.Android.Permissions.System](https://www.ftc.gov/system/files/documents/public_events/1415032/privacycon2019_serge_egelman.pdf?partner=switch)

This is a paper in ECS251(winter 20) reading list.

## Summary

This paper recognizes the issue of privacy abuse in Android.
In this paper, the authors proposed a scale approach to examine over 88k apps in Google Play Store.

The approach is following.
They instrumented the Android platform and underling kernel to monitor all network level monitoring.
They have automatic app execution and used [Monkey](https://developer.android.com/studio/test/monkey) as the UI fuzzer.
After they monitored personal information flow or other findings, they reverse engineer this app and try to pinpoint the location where the information is leaked.

In the Sec 4 the found real-world problems including IMEI and MAC address leak.

## Takeaways

- [Covert Channel](https://en.wikipedia.org/wiki/Covert_channel)
- [Side Channel](https://en.wikipedia.org/wiki/Side-channel_attack)

## [Video](https://www.youtube.com/watch?v=twf-sgWp5bs)

## External Links

[Blog](https://blog.appcensus.io/)

## bib
```
@inproceedings{reardon201950,
  title={50 Ways to Leak Your Data: An Exploration of Apps' Circumvention of the Android Permissions System},
  author={Reardon, Joel and Feal, {\'A}lvaro and Wijesekera, Primal and On, Amit Elazari Bar and Vallina-Rodriguez, Narseo and Egelman, Serge},
  booktitle={28th $\{$USENIX$\}$ Security Symposium ($\{$USENIX$\}$ Security 19)},
  pages={603--620},
  year={2019}
}
```