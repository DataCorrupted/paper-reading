# [Neutaint.Efficient.Dynamic.Taint.Analysis.with.Neural.Networks](https://www.cs.columbia.edu/~dongdong/publication/neutaint/)

## Summary

This paper talks about NN training, yet is seems like they are using gradient just as Angora do.
It's unclear why they added relu & sigmoid to their network(Appx.A)

## Insights

Fig 2 gave us some pretty good insights of what and where hot bytes are.
If we are thinking using GD to do taint tracking like REDQUEEN or GREYONE did, this heatmap is basically confirming that this is do-able.