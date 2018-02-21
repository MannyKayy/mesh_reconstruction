# Single-Image 3D Mesh Reconstruction using Neural Renderer

This is the code for 3D reconstruction in the paper [Neural 3D Mesh Renderer (CVPR 2018) ](http://hiroharu-kato.com/projects_en/neural_renderer.html) by Hiroharu Kato, Yoshitaka Ushiku, and Tatsuya Harada.

Related repositories:
* [Neural Renderer](https://github.com/hiroharu-kato/neural_renderer)
    * [Single-image 3D mesh reconstruction](https://github.com/hiroharu-kato/mesh_reconstruction)
    * [2D-to-3D style transfer](https://github.com/hiroharu-kato/style_transfer_3d)
    * [3D DeepDream](https://github.com/hiroharu-kato/deep_dream_3d)


## Requirements
Please install neural renderer.
```
# install neural_renderer
git clone https://github.com/hiroharu-kato/neural_renderer.git
cd neural_renderer
python setup.py install --user
# or, sudo python setup.py install
```

## Testing pre-trained models
First, you need download pre-trained models.
```
bash download_models.sh
```

You can reconstruct a 3D model (*.obj) and multi-view images by the following commands.
```
python mesh_reconstruction/reconstruct.py -d ./data/models -eid singleclass_02691156 -i ./data/examples/airplane_in.png -oi ./data/examples/airplane_out.png
python mesh_reconstruction/reconstruct.py -d ./data/models -eid singleclass_02958343 -i ./data/examples/car_in.png -oi ./data/examples/car_out.png
```

You can evaluate voxel IoU of a model on test set by the following command.
```
python mesh_reconstruction/test.py -d ./data/models -eid multiclass
```

## Training models
First, you need download datasets rendered using ShapeNet dataset.
```
bash download_dataset.sh
```

You can train models by the following command. 
```
bash train.sh
```
This produces almost the same models as the pre-trained models. It takes about three days on Tesla P100 GPU.


## Citation
```
@inproceedings{kato2018renderer
    title={Neural 3D Mesh Renderer},
    author={Kato, Hiroharu and Ushiku, Yoshitaka and Harada, Tatsuya},
    booktitle={The IEEE Conference on Computer Vision and Pattern Recognition (CVPR)},
    year={2018}
}
```