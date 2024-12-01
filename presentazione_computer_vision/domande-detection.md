- Why do we need object detetors? Weren't image classifiers enough?
> Image classifiers assign scores to whole images, object detectors find different objects in whole scenes
- How do we handle the huge amount of windows we would get by using a sliding window approach?
> By considering less windows of different fixed sizes, see RPN
- Is everything we get out of the RPN golden?
> No, "bad" boxes might get out of the RPN, these will be likely ranked less positively by the classifier and suppressed at later stages
- How can we feed boxes of different sizes to a fixed-size CNN? 
> We use ROI pooling
- How does ROI pooling actually work? Does it take averages of values?
> There are different pooling methods, we can both take maximum/minimum values or averages
- Are the boxes we get out of non-maximum suppression perfect?
> Not really, we can still perform bounding box regression to shrink the boxes to contain only the intendend object
