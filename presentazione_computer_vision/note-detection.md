# Object Detectors
- Why do we need them?
    - Classifiers only recognize single objects across whole images
    - Object detectors find objects in scenes 
- What do they output?
    - Bounding boxes
- How do they work?
    - Basic idea: sliding convolutional window (very deep convnets)
    - How do we choose the windows? Regional Proposal Networks (RPNs)
    - These give anchor boxes, stride of anchor boxes
    - After we have our anchors, we rank them on objectness and treshold Regions Of Interest (ROI)
    - ROIs need to be fed to a classifier, but they are of diferent sizes: we need ROI pooling
    - After ROI pooling and classification through a convnet, we need to perform non-maximum suppression (greedy algorithm)
    - Finally, we have to perform bounding box regression to shrink our bounding box the the intendend feature
    - done!

