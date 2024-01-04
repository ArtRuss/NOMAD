# Welcome to NOMAD
A Natural, Occluded, Multi-scale Aerial Dataset, for Emergency Response Scenarios


NOMAD presents a benchmark for human detection under **occluded** aerial views, with five different aerial distances and rich imagery variance. NOMAD is composed of 100 different Actors, all performing sequences of walking, laying and hiding. It includes 42,825 frames, extracted from 5.4k resolution videos, and manually annotated with a bounding box and a label describing 10 different visibility levels, categorized according to the percentage of the human body visible inside the bounding box. This allows computer vision models to be evaluated on their detection performance across different ranges of occlusion. NOMAD is designed to improve the effectiveness of aerial search and rescue and to enhance collaboration between  small Unmanned Aerial Systems (sUAS) and humans, by providing **a new benchmark dataset for human detection under occluded aerial views**.

<hr>

>
__NEWS__
>
>>
[WACV 2024 accepted paper!](https://openaccess.thecvf.com/content/WACV2024/html/Bernal_NOMAD_A_Natural_Occluded_Multi-Scale_Aerial_Dataset_for_Emergency_Response_WACV_2024_paper.html)
>>

<hr>

>
__CITATION__
>

To ackowledge all effort taken by the authors of this dataset, please cite our paper:

[WACV 2024 paper](https://openaccess.thecvf.com/content/WACV2024/html/Bernal_NOMAD_A_Natural_Occluded_Multi-Scale_Aerial_Dataset_for_Emergency_Response_WACV_2024_paper.html)

```
@InProceedings{RussellBernal_2024_WACV,
    author    = {Russell Bernal, Arturo Miguel and Scheirer, Walter and Cleland-Huang, Jane},
    title     = {NOMAD: A Natural, Occluded, Multi-Scale Aerial Dataset, for Emergency Response Scenarios},
    booktitle = {Proceedings of the IEEE/CVF Winter Conference on Applications of Computer Vision (WACV)},
    month     = {January},
    year      = {2024},
    pages     = {8584-8595}
}
```

<hr>

>
__ACCESSING NOMAD__
>
Please follow the [Google Drive Link](https://drive.google.com/drive/folders/1zRiOzedR-PzO1bps5I1vb6jtVoQHFWzg?usp=share_link).

Directories are organized as follows:
- NOMAD
    - videos
        - Actor001 : contains 11 videos per actor (5 distances with true negatives + 1 reference video).
            - Actor001_a10.MP4 : routine video at distance of 10m.
            - Actor001_a10_TN.MP4 : true negative of the routine video.
            - Actor001...
            - Actor001_reference.MP4
        - Actor... 
    - images
        - Actor001
            - Actor001_a10 : contains selected frames for annotation.
            - Actor001...
        - Actor...
    - annotations
        - annotations.json : contains the bounding box and the visibility label of each person in every selected frame/image.  The json file is organized in the Detectron2 format, friendly to the COCO annotations format.
        - metadata.json : contains the environmental, demographic and outfit metadata of every actor.
        - activityLabels.json : divides the selected frames/images into four classes: Walking, Hiding, Laying, and Hiding (Laying).  Every class contains a list of [startFrame, endFrame]. Hiding (Laying) means that the actor will lay-down at some point during their hiding procedure.
        - activityLabels_waterRoutine.json : additional subdivisions for the Hiding class of actors performing a water routine: Walking, Swimming, Drowning.
    - labels
        - Actor001
            - Actor001_a10 : bounding box annotations following the YOLO format for every selected frame/image.
            - Actor001...
        - Actor...

<hr>

>
__Acknowledgements__
>
The work described in this paper was supported by the USA National Science Foundation under grant CNS-1931962. In addition, we thank all participants and annotators, as well as academic institutions, governmental agencies, private owners and company authorized supervisors for providing locations’ accessibility. We also thank family and friends for their logistics support.

<hr>
