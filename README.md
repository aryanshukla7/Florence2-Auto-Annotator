
# Auto Annotations Pipeline Using Florence2

This is an auto-annotations pipeline which takes in a folder of images and returns JSON object containing the annotated labels of the corresponding images in Florence2 format.




## Deployment

To deploy this project simply run each cell in the ```.ipynb``` notebook in order.
(You can skip a few cells if suitable). If running on local system, then you need to install some extra dependencies like, ```pillow```, ```matplotlib```, ```glob```, and ```transformers```, etc.






## Authors

- [Aryan Shukla](https://www.github.com/aryanshukla7)


## Demo

- Following are some examples of the code running:
    ![Annotated Image](https://github.com/aryanshukla7/ASL-Phrase-Detection/assets/79625246/6b9f956a-6888-4aed-a81e-59bcdba0bb39)


- A peculiar thing to notice: The green boxes are ground truth annotations on Microsoft COCO and Pascal VOC Dataset and red boxes are made by the pipeline implemented here with Florence2.

![Annotated_Sample1](https://github.com/aryanshukla7/ASL-Phrase-Detection/assets/79625246/627f77c7-7049-4fde-8269-f89caf16b440)
![Annotated_Sample2](https://github.com/aryanshukla7/ASL-Phrase-Detection/assets/79625246/3eeaea12-4b94-45a2-bd5a-82c7a6808a70)
![Annotated_Sample3](https://github.com/aryanshukla7/ASL-Phrase-Detection/assets/79625246/d646bd70-2475-48df-a5ac-05d0e2110b09)
![Annotated_Sample5](https://github.com/aryanshukla7/ASL-Phrase-Detection/assets/79625246/ffa027a3-b276-4868-8fce-fa10025b3d65)
![Annotated_Sample6](https://github.com/aryanshukla7/ASL-Phrase-Detection/assets/79625246/61431e8d-dd66-4462-aaba-4c85d1536b87)
![Annotated_Sample7](https://github.com/aryanshukla7/ASL-Phrase-Detection/assets/79625246/ff81bb02-e1c1-4342-a114-e8ee899c5629)

### Notes

-  In the picture of an airplane, the pre-labelled annotations (green) just shows one airplane, whereas, the implemented pipeline is able to detect two airplanes. When the IoU was calculated over the common 'airplane' object, it turned out to be 0.8155. Which is a very good score. But it should also be noted that the green box does NOT bound the object completely and hence not a good quality annotation as compared to the red one (Florence2).

- In the picture of the cat, the pre-labeled annotation (green) does not bound the cat completely and hence is a poor annotation, whereas, the red bounding box produced by the custom pipeline (Florence2) bounds the cat perfectly. The IoU turned out to be 0.3548, which is not a good score but it can be attributed to poor ground truth annotation.

- Florence2 is able to detect more objects as compared to given in ground truth.

- The errors in the COCO dataset is explained [here](https://medium.com/@jamie_34747/how-i-found-nearly-300-000-errors-in-ms-coco-79d382edf22b), TL:DR, the dataset has nearly 300k errors.

- Another problem that was observed was the difference in categories given by Florence2 model and other models and datasets. For e.g. in COCO Dataset, the class is 'aeroplane' the same is called 'airplane' in other datasets and models. Similarly, there are way more categories in Florence2 than in other models.

- Due to the above mentioned point, Florence2 almost always has precision = 1.0, as compared to human labels (observed by me, can be verified in the above pictures as well). The model also has a high recall.
