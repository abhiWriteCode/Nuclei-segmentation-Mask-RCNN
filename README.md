I modified **[Matterport's](https://github.com/matterport/Mask_RCNN)** implementation of **Mask-RCNN** deep neural network for object instance segmentation. I adapted the existing model configurations to detect small nuclei in images with varying size and modality and fine-tuned with [pre-trained](https://www.dropbox.com/s/1kql7tsug876xfn/kaggle_bowl.h5?dl=0) model trained by a kaggler.

I trained and fine-tuned the pre-trained model in [colab](https://colab.research.google.com).


For train Mask-RCNN, use `mask_rcnn_training_notebook.ipynb` notebook

and for evaluation (**maP**), use `eval_notebook.ipynb` notebook


### Steps

1. First clone mask-rcnn repo `git clone https://github.com/matterport/Mask_RCNN.git`.

2. `cd Mask_RCNN`

3. `pip install -r requirements.txt`

4. `python setup.py install`

5. `cd ..`

6. `mkdir Mask_RCNN/weights`, then move the pre-trained model to `Mask_RCNN/weights` directory

7. `nuclei_datasets` directory under `Mask_RCNN` directory

```bash
Mask_RCNN
|
|-weights
|-nuclei_datasets
|...
```


### To train

open `mask_rcnn_training_notebook.ipynb` on jupyter notebook

or

```bash
python Mask_RCNN/samples/nucleus/nucleus.py train \
    --dataset=Mask_RCNN/nuclei_datasets --subset=stage1_train \
    --weights=Mask_RCNN/weights/kaggle_bowl.h5
```

if you run above code, first 20 epoch train only network's head
and next 20 epoch train hte whole network

### To evaluate 

open `eval_notebook.ipynb` on your jupyter notebook


After training model (`weights/kaggle_bowl.h5`) weight is updated

I send you updated weight