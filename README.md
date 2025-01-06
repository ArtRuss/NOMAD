# Welcome to NOMAD
A Natural, Occluded, Multi-scale Aerial Dataset, for Emergency Response Scenarios


NOMAD presents a benchmark for human detection under **occluded** aerial views, with five different aerial distances and rich imagery variance. NOMAD is composed of 100 different Actors, all performing sequences of walking, laying and hiding. It includes 42,825 frames, extracted from 5.4k resolution videos, and manually annotated with a bounding box and a label describing 10 different visibility levels, categorized according to the percentage of the human body visible inside the bounding box. This allows computer vision models to be evaluated on their detection performance across different ranges of occlusion. NOMAD is designed to improve the effectiveness of aerial search and rescue and to enhance collaboration between  small Unmanned Aerial Systems (sUAS) and humans, by providing **a new benchmark dataset for human detection under occluded aerial views**.

![nomad](/figures/fig_nomad.jpg)

**NEW!** Explore *Psych-ER*, a human behavioral dataset based on NOMAD!
>The success of Emergency Response (ER) scenarios, such as search and rescue, is often dependent upon the prompt location of a lost or injured person. With the increasing use of small Unmanned Aerial Systems (sUAS) as "eyes in the sky" during ER scenarios, efficient detection of persons from aerial views plays a crucial role in achieving a successful mission outcome. Fatigue of human operators during prolonged ER missions, coupled with limited human resources, highlights the need for sUAS equipped with Computer Vision (CV) capabilities to aid in finding the person from aerial views. However, the performance of CV models onboard sUAS substantially degrades under real-life rigorous conditions of a typical ER scenario, where person search is hampered by occlusion and low target resolution. To address these challenges, we extracted images from the NOMAD dataset and performed a crowdsource experiment to collect behavioural measurements when humans were asked to "find the person in the picture". We exemplify the use of our behavioral dataset, Psych-ER, by using its human accuracy data to adapt the loss function of a detection model. We tested our loss adaptation on a RetinaNet model evaluated on NOMAD against increasing distance and occlusion, with our psychophysical loss adaptation showing improvements over the baseline at higher distances across different levels of occlusion, without degrading performance at closer distances. To the best of our knowledge, our work is the first human-guided approach to address the location task of a detection model, while addressing real-world challenges of aerial search and rescue.
![psych](/figures/fig_psych.jpg)

<hr>

>
__NEWS__
>
>[WACV 2025 accepted paper!](https://arxiv.org/abs/2412.05553) <-- *how do humans perform the search of a person in aerial images?* Explore our new addition: Psych-ER, a human behavioral dataset, as well as our use of a psychophysical loss to improve performance of computer vision models!

>[WACV 2024 accepted paper!](https://openaccess.thecvf.com/content/WACV2024/html/Bernal_NOMAD_A_Natural_Occluded_Multi-Scale_Aerial_Dataset_for_Emergency_Response_WACV_2024_paper.html) <-- the original NOMAD dataset!

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
__ACCESSING PSYCH-ER__
>
Please follow the [Google Drive Link](https://drive.google.com/drive/folders/1zRiOzedR-PzO1bps5I1vb6jtVoQHFWzg?usp=share_link).

- NOMAD
    - psych_er
        - results.json: a json file containing the information of 500 surveys/clusters, every survey/cluster was solved by a different participant. Every survey/cluster is composed of 13 images.  The json file is organized with the following hierarchy:
            - clusterid: a cluster/survey identifier.
            - data: containing the information of 13 images, with every image presenting the following fields:
                - imageid: an image identifier.
                - name: the name of the image, from the NOMAD dataset.
                - bbox: the ground truth bounding box of the person in the image, from the NOMAD dataset.
                - visibility: the level of visibility, from the NOMAD dataset.
                - latency: the response time to solve the image, in miliseconds.
                - circle: the answer from the participant of where the person is in the image, presented as [x,y,radius].
        - heatmaps: a directory organized by clusterid, containing 500 directories/clusters.
            - 0: clusterid = 0. Contains 13 json files, each json file corresponding to the search heatmap of one image.
                - 1.json: imageid = 1. Organized as a list of lists, every inner list representing an attention circle, presented as [x,y,radius,time].  It represents the location and time of the focus of the participant during the search.
                - ...


<hr>

>
__CITATION__
>

To ackowledge all effort taken by the authors of this dataset, please cite our papers accordingly:

[WACV 2025 paper](https://arxiv.org/pdf/2412.05553)

```
@article{russellbernal2024psych,
  title={Psych-Occlusion: Using Visual Psychophysics for Aerial Detection of Occluded Persons during Search and Rescue},
  author={Russell Bernal, Arturo Miguel and Cleland-Huang, Jane and Scheirer, Walter},
  journal={arXiv preprint arXiv:2412.05553},
  year={2024}
}
```

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
__Acknowledgements__
>
The work described in this paper was supported by the USA National Science Foundation under grant CNS-1931962. In addition, we thank all participants and annotators, as well as academic institutions, governmental agencies, private owners and company authorized supervisors for providing locations’ accessibility. We also thank family and friends for their logistics support.

<hr>
