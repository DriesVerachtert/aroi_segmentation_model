# Fine-tuning of a model for segmentation of retinal optical coherence tomography images (AROI)

While looking for a intesting dataset to try some fine-tuning of models for segmentation of images, I stumbled upon https://ipg.fer.hr/ipg/resources/oct_image_database which mentions that this dataset of annotated images can be used free of charge for research and educational purposes. I mailed Martina Melinščak and maybe half an hour later she already gave me access to the dataset.

I'll upload the model to huggingface. If you would like to use the dataset, then you'll have to contact Martina.

## Citations

Information about the dataset can be found in the following publications:

M. Melinščak, M. Radmilović, Z. Vatavuk, and S. Lončarić, "Annotated retinal optical coherence tomography images (AROI) database for joint retinal layer and fluid segmentation," Automatika, vol. 62, no. 3, pp. 375-385, Jul. 2021. doi: 10.1080/00051144.2021.1973298

M. Melinščak, M. Radmilović, Z. Vatavuk, and S. Lončarić, "AROI: Annotated Retinal OCT Images database," in 2021 44th International Convention on Information, Communication and Electronic Technology (MIPRO), Sep. 2021, pp. 400-405. 

M. Melinščak, "Attention-based U-net: Joint segmentation of layers and fluids from retinal OCT images," in 2023 46th International Convention on Information, Communication and Electronic Technology (MIPRO), Sep. 2021, pp. 391-396. 

## Contents

* Notebook '01_load_patient_images.ipynb' checks all the images and creates a list of 'PatientImage' objects which contain a raw image and its labeled images.
* Notebook '02_create_huggingface_dataset.ipynb' creates splits the images in a test and a training set and creates a HuggingFace dataset. The dataset is not uploaded to the HuggingFace Hub as I don't own the copyright on the images.
* Notebook '03_finetune_semantic_segmentation_model.ipynb' uses the dataset to fine-tune some models for semantic segmentation.



This notebook assumes that you have already downloaded and unpacked that rar file.

This notebook does the following:

* Inspect the images in the dataset.
* Create a Huggingface dataset object.
* Create a training and a test dataset from the complete dataset.
* Transform the dataset so it can be used with a HuggingFace DETR segmentation model.
* Fine-tune the model.
* Use the model on some of the test images: test the inference.

## Disclaimer

Let me be clear: I'm no ophthalmologist, I have no medical background. This model is just provided 'as is' without any warranties, express or implied, including but not limited to the warranties of merchantability, fitness for a particular purpose, or non-infringement.

## Links

* https://huggingface.co/blog/fine-tune-segformer
* https://ipg.fer.hr/ipg/resources/oct_image_database
* https://www.tandfonline.com/doi/full/10.1080/00051144.2021.1973298
* https://huggingface.co/docs/evaluate/a_quick_tour
* https://huggingface.co/docs/datasets/semantic_segmentation
* https://huggingface.co/docs/transformers/tasks/semantic_segmentation
* https://huggingface.co/tasks/image-segmentation