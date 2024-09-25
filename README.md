# PPNG Viewer
Source code repository for PPNG viewer. 

## Training
For training PPNG, please refer to [this repository](https://github.com/leejaeyong7/instant-ngp). 

## Installation & Running the server
To install PPNG, first run 
```bash
npm install
```
to install necessary files required for building a package.

Then, PPNG javascript can be built with:
```bash
npm run build # create dist folder with compiled javascript / CSS files
```
this build `dist` folder that contains compiled javascript files that allows custom `<ppng-viewer>` component in HTML. 
Please refer to the `Usage` section below for details.

We provide example usages that can be run with:
```bash
npm run preview # runs HTML server on the built dist folder.
```

## Usage
PPNG viewer can be nested as HTML components as following:
```html
<head>
    ...
    <script type="module" src="path-to-built-js-files.js"></script>
    ...
</head>
<body>
    <ppng-viewer id="viewer-1" src="https://some_path_to_ppng_binaries.ppng" 
                 width="400" height="400" render_width="200" render_height="200">
</body>
```


## Running my own PPNG files
We provide sample [ppng.html](ppng.html) that loads ppng file obtained from the [training repository](https://github.com/leejaeyong7/instant-ngp). 

Below is an example usage:
```bash
MY_PPNG_FILE=my_experiment.ppng
RESOLUTION=600 # Rendering resolution for PPNG viewer

cd dist # dist folder from npm run build
mkdir -p custom_files
mv $MY_PPNG_FILE custom_files
python -m http.server 8000

# On web browser with Webgl2 support, visit:
http://localhost:8000/ppng.html?src=http://localhost:8000/custom_files/$MY_PPNG_FILE&size=$RESOLUTION
```

## Extending PPNG source code
If you want to extend PPNG viewer files, you can run hot-reloaded development server with:
```bash
npm run devh # runs local server with live updates for debugging the source javascript files.
```
Happy hacking ;) 
## Citation
If you like our work, please cite:
```
@misc{lee2024ppng,
      title={Plenoptic PNG: Real-Time Neural Radiance Fields in 150 KB}, 
      author={Jae Yong Lee and Yuqun Wu and Chuhang Zou and Derek Hoiem and Shenlong Wang},
      year={2024},
      eprint={2409.15689},
      archivePrefix={arXiv},
      primaryClass={cs.CV},
      url={https://arxiv.org/abs/2409.15689}, 
}
```