Dataset for Authenticity of Visual Relationships(VRs) between Objects in an Image
------

### Introduction
There exists visual relationship between the physical objects in an image. Recognizing these relationships leads to  understanding the entire image. The datasets released priorly for the recognition of VRs do not take in to account the authenticity of the VRs. Our dataset contains the information about the authenticity or trueness of VRs. Correctly recognizing true VR is necessary for tasks like extraction of paraphrases via an image(Chu *et al*., 2018). Our dataset is also expected to have better accuracy with syntactic depenency analysis of noun clauses.  

### Construction of dataset
The annotation of the authenticity of VR is done in following two stages.
1. Automatic annotation via Dependency Analysis and preprocessing
2. Human Annotation
All the candidates for visual relationships are extracted from the Flickr30K Entity Dataset through preprocessing(see the paper for details). 

### True and false visual relationships
Let's consider the following sentence   
```Two bikers in bike gear are sitting on a bench.```
The entities in this image are `two bikers`, `bike gear` and `a bench`.
Possible VR candidates are 
```
Two bikers in bike gear
Two bikers are sitting on a bench
bike gear are sitting on a bench
```
The first two are VRs and the last one isn't. 
### Reference:
Yuto Takebayashi, Chenhui Chu, Yuta Nakajima [画像内物体間の視覚的関係の真偽判定データセット](https://www.anlp.jp/proceedings/annual_meeting/2019/pdf_dir/P7-36.pdf) 言語処理学会 第25回年次大会 , Mar. 2019

