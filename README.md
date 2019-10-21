Dataset for Authenticity of Visual Relationships(VRs) between Objects in an Image
------

### Introduction
There exists visual relationship between the physical objects in an image. Recognizing these relationships leads to  understanding the entire image. The datasets released priorly for the recognition of VRs do not take in to account the authenticity of the VRs. Our dataset contains the information about the authenticity or trueness of VRs. Correctly recognizing true VR is necessary for tasks like extraction of paraphrases via an image(Chu *et al*., 2018). Our dataset is also expected to have better accuracy with syntactic depenency analysis of noun clauses.  

### Construction of dataset
The annotation of the authenticity of VR is done in following two stages.
1. Automatic annotation via preprocessing and dependency Analysis
All the candidates for visual relationships are extracted from the Flickr30K Entity Dataset through preprocessing(*see paper for details*). Then the captions of the images in the Flickr30K dataset are analysed using dependency analysis. If the entities and relation follow a certain type of relation as described in our paper, then it is collected as a valid candiate for VR. The type of relation to accept are given in our paper. This process of extraction when a match is found with a user defined type is  called Type Extraction. The VR obtained via Type Extraction and also included in the candidates obtained by preprocessing is categorized as true VR.

2. Human annotation using Amazon Mechanical Turk(AMT) 
The VR candidates that were not annotated in the previous step are annotated using AMT. 

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
The first two are VRs but the last one isn't. But the second VR wasn't successfully extracted using automatic annotation because of it's type not being included in the paper. To successfully include such VRs, human annotation was further required. 

### Description of dataset
There are 6 csv files in total. The 'parse' files contain the annotation result obtained after stage 1. Similarly, csv files with 'AMT' are the results of annotation with Amazon mechanical turk. 'parse' files contain the following fields as information. 
* **ImageID**  
The ID of the image in flickr30K dataset which the VR candidate belongs to
* **SentenceNo**  
The caption index of the caption from which the VR candidate 
* **Entity1&Entity2**  
The entities that make up the VR candidate
* **Relation**  
The relation between Entity1 and Entity2  
(*Entity1, Entity2 and Relation make up the VR candidate*)
* **EntityID1&EntityID2**  
The ID of Entity1 and Entity2 in the flickr30K dataset
* **Answer**
The annotation result achieved by Type extraction and preprocessing(stage 1)  
*1* : True VR, *0* : False VR  

The VR candidates having Answer as *0* in the parse file are further annotated with AMT and annotation results are presented in the 'AMT' files. The 'AMT' files contain all the above fields with same meaning as above with one minor exception. *Answer* in the 'parse' file indicates the result of annotaion from stage1 but *Answer* in the 'AMT' file indicates result from human annotation. In addition, 'AMT' file has the following fields.
* **NumberofWorkers**  
The number of workers that annotated that particuar VR candidate  
(*5 for almost all cases*)
* **WorkerAnswer**  
The annotation answer of each worker
* **WorkerAccuracy**  
The overall accuracy of the worker with the dummy questions    
(*See paper for more details*)

### Reference:
Yuto Takebayashi, Chenhui Chu, Yuta Nakajima [画像内物体間の視覚的関係の真偽判定データセット](https://www.anlp.jp/proceedings/annual_meeting/2019/pdf_dir/P7-36.pdf) 言語処理学会 第25回年次大会 , Mar. 2019

