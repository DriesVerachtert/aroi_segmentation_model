# Fine-tuning of a model for segmentation of retinal optical coherence tomography images (AROI)

While looking for a intesting dataset to try some fine-tuning of models for segmentation of images, I stumbled upon https://ipg.fer.hr/ipg/resources/oct_image_database which mentions that this dataset of annotated images can be used free of charge for research and educational purposes. I mailed Martina Melinščak and maybe half an hour later she already gave me access to the dataset.

If you would like to use the dataset, then you'll have to contact Martina.

## Citations

Information about the dataset can be found in the following publications:

M. Melinščak, M. Radmilović, Z. Vatavuk, and S. Lončarić, "Annotated retinal optical coherence tomography images (AROI) database for joint retinal layer and fluid segmentation," Automatika, vol. 62, no. 3, pp. 375-385, Jul. 2021. doi: 10.1080/00051144.2021.1973298

M. Melinščak, M. Radmilović, Z. Vatavuk, and S. Lončarić, "AROI: Annotated Retinal OCT Images database," in 2021 44th International Convention on Information, Communication and Electronic Technology (MIPRO), Sep. 2021, pp. 400-405. 

M. Melinščak, "Attention-based U-net: Joint segmentation of layers and fluids from retinal OCT images," in 2023 46th International Convention on Information, Communication and Electronic Technology (MIPRO), Sep. 2021, pp. 391-396. 

The base nvidia/mit-b0 model has the following citations:

```
@article{DBLP:journals/corr/abs-2105-15203,
  author    = {Enze Xie and
               Wenhai Wang and
               Zhiding Yu and
               Anima Anandkumar and
               Jose M. Alvarez and
               Ping Luo},
  title     = {SegFormer: Simple and Efficient Design for Semantic Segmentation with
               Transformers},
  journal   = {CoRR},
  volume    = {abs/2105.15203},
  year      = {2021},
  url       = {https://arxiv.org/abs/2105.15203},
  eprinttype = {arXiv},
  eprint    = {2105.15203},
  timestamp = {Wed, 02 Jun 2021 11:46:42 +0200},
  biburl    = {https://dblp.org/rec/journals/corr/abs-2105-15203.bib},
  bibsource = {dblp computer science bibliography, https://dblp.org}
}
```

## Contents

* Notebook '01_load_patient_images.ipynb' checks all the images and creates a list of 'PatientImage' objects which contain a raw image and its labeled images.
* Notebook '02_create_huggingface_dataset.ipynb' creates splits the images in a test and a training set and creates a HuggingFace dataset. The dataset is not uploaded to the HuggingFace Hub as I don't own the copyright on the images.
* Notebook '03_finetune_semantic_segmentation_model.ipynb' uses the dataset to fine-tune some model for semantic segmentation. The base model is nvidia/mit-b0.
* Notebook '04_segment_images_with_model.ipynb' does some inference: it uses the model to segment some of the images.


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
* https://xieenze.github.io/segformer.pdf