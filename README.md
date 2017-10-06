# RPN Triggered Object Tracking via LSTM

**Author: Chengxi Li (cicelyli) , Ren Li (li2515)**


## Goals:
Region Proposal Network(RPN) is firstly introduced by the paper Faster R-CNN which looks at the entire image feature map and generates thousands of object proposals associated with objectness scores. 

Long Short-Term Memory networks (LSTM) is a recurrent neural network architecture that remembers values over arbitrary intervals. Due to this unique property, LSTM is especially suited to process time sequence signals with various duration like audios, videos etc. Inspired by this, we propose the LSTM may have potential in object tracking.

In my proposed network, the RPN will generate proposals for the first frame of which I will only keep K highest scoring proposals. Then an LSTM will start tracking each of these proposals. The input to this LSTM will be slightly larger than the region predicted by it at the previous time step. So basically, the LSTM only needs to refine its input to snuggly fit whatever it is tracking. It will also produce a tracking confidence score which is a measure of how well it is tracking a given object.

1. Design a network architecture consisting of RPN and LSTM in order to do the object tracking.
2. Train the net on a small subset of ILSVRC 2015 VID training dataset.
3. Evaluate the algorithm by testing the model on the small subset of  ILSVRC 2015 VID test dataset.
4. If time allows, we will do : train and test the net on the entire ILSVRC 2015 VID dataset and compare our results with other state-of-art algorithms.


## Challenges:

1.The difficulty of object tracking arises from object occlusion,  rotation, transformation and lighting changes. How to overcome these problems will be one of the challenges in our project.

2.In some videos, the tracked objects may disappear in the midway through the video. Sometimes even new objects appear in the midway through the video. Our algorithm needs the capability of addressing this issue.

3.We suspect that the LSTM may remembers the object’s class feature to aid for tracking. However, it is not what we want. We have to think of a way of letting LSTM only remember the class-independent feature.
