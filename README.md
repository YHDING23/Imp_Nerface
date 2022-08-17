## An Implementation of NerFACE
This is an implementation of NerFACE: Dynamic Neural Radiance Fields for Monocular 4D Facial Avatar Reconstruction [CVPR 2021]. The project page and video can be found <a href="https://gafniguy.github.io/4D-Facial-Avatars/">here</a>. 

### Dataset and License

Dataset is <a  href="https://syncandshare.lrz.de/getlink/fiBTHis1fS8Zxqd55XCAjjG8/nerface_dataset.zip">available</a>.
Please download the dataset and name it like `nerface_dataset/`
Please do not use it for commercial use and respect the license attached within the zip file. 

### Installation

Originally the project used torch 1.7.1, but this should also run with torch 1.9.0 (cuda 11). This Repo follows `torch=1.7.0, cudatoolkit=10.1, and cudatoolkit-dev=10.1`. If you get any errors related to `torchsearchsorted`, ignore this module and don't bother installing it. 

Create the conda environment via:

```
conda env create -f nerface_code/my_environment.yml
conda activate nerface
pip install -r requiriment_pip.txt
```

Then, use the following to install `pytorch3d`:

`
pip install "git+https://github.com/facebookresearch/pytorch3d.git@stable"
`

The main training and testing scripts are `train_transformed_rays.py` and `eval_transformed_rays.py`, respectively. They are in the main working folder `nerf-pytorch/`. 

The training script expects a path to a config file, e.g.:

`python train_transformed_rays.py --config  --config ./nerface_dataset/person_1/person_1_config.yml `

The eval script will also take a path to a model checkpoint and a folder to save the rendered images:

`python eval_transformed_rays.py --config ./nerface_dataset/person_1/person_1_config.yml --checkpoint /path/to/checkpoint/checkpoint400000.ckpt --savedir ./renders/person_1_rendered_frames`

Please note the nerface_dataset was generated according to `face2face` which is not open-sourced as mentioned by the authors. They also mentioned 2 alternatives like [video-head-tracker](https://github.com/philgras/video-head-tracker) and [AD-NeRF](https://github.com/YudongGuo/AD-NeRF). However, neither of these two repos cannot provide the parameters as this repo requested. 
