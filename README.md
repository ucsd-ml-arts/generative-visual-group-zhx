# Project 4 Generative Visual

Zhuoqun Xu, zhx068@ucsd.edu

## Abstract

![Result](/result.png)

The idea is to imitatively create the 3d Model without human involved. By feed with large chunk of 3d model data set, 
it becomes vending machine for game creaters or visial designer to easily use the rough models and create a better,
high-definition model from the it.

## Model/Data

Briefly describe the files that are included with your repository: (WIP)
- trained models
- training data (or link to training data)

## Code

Your code for generating your project: (WIP)
- Python: generative_code.py
- Jupyter notebooks: generative_code.ipynb

## Results

Documentation of your results in an appropriate format, both links to files and a brief description of their contents: (WIP)
- image files (`.jpg`, `.png` or whatever else is appropriate)
- move files (uploaded to youtube or vimeo due to github file size limits)
- ... some other form

## Technical Notes

1. Get dataset

```
python download_data.py
```

Choose either 
[Princeton's 10-Class aligned CAD models](http://modelnet.cs.princeton.edu/) 
*bathtub, bed, chair, desk, dresser, monitor, night stand, sofa, table, toilet.*

or 

[Manually aligned 40-Class CAD models](https://github.com/lmb-freiburg/orion) 
*airplane, bathtub, bed, beanch, bookshelf, bottle, bowl, car, chair, cone, cup, curtain, desk, door, dresser, flower pot, glass box, guitar, keyboard, lamp, laptop, mantel, monitor, night stand, person, piano, plant, radio, range hood, sink, sofa, stairs, stool, table, tent, toilet, tv stand, wardrobe, vase, xbox.*

2. Convert (in Windows)
```
python convert_data.py -m ModelNet10/chair -b binvox.exe
```
Convert CAD data to voxel format

3. Train
```
python 64-3D-RaSGan.py -n chair-1 -d ModelNet10/chair/train -e 2500 -b 24 -sample 10 -save 10 -graph 10 -graph3d 10 -glr 0.0025 -dlr 0.00003
```

4. Generate

Either
- 3D graph images
```
python convert_to_graph.py -n chair-1
```

or
- .obj model

or
- Render obj to png (make sure installed Blender)
```
cd render
python render_class_view.py -m ../models/1000.obj -o test.png -b "C:/Program Files/Blender Foundation/Blender/blender.exe"
```

## Reference

- https://github.com/lmb-freiburg/orion
- https://github.com/chenhsuanlin/3D-point-cloud-generation
- https://openai.com/blog/generative-models/
- https://github.com/meetshah1995/tf-3dgan
- https://github.com/optas/latent_3d_points
- http://3dgan.csail.mit.edu/
- http://modelnet.cs.princeton.edu/#
- https://github.com/google/tf_mesh_renderer