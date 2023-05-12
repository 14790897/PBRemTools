# Latest Updates
Combine Segment Anything and CLIP and control the generating mask with text has been added!

![スクリーンショット 2023-04-11 115936](https://user-images.githubusercontent.com/48423148/231046410-3322ad98-f972-40cf-b51d-84ff3e91cb2a.png)

Segmentation can also be performed from the PBRemTools tab.

However, to use it, the Segment Anything Model must be added manually.

Download the model from here (https://github.com/facebookresearch/segment-anything#model-checkpoints) and place it under "models"(stable-diffusion-webui/extensions/PBRemTools/models).

This program is prepared with reference to (https://github.com/facebookresearch/segment-anything) and (https://github.com/Curt-Park/segment-anything-with-clip)

# PBRemTools
PBRemTools(Precise background remover tools) is a collection of tools to crop backgrounds from a single picture with high accuracy.

- Base Image
<img src="https://user-images.githubusercontent.com/48423148/229968165-9effdc0e-db85-41d1-bfdb-1031665af88d.png" width="30%">

- PBRemTools(Tile division ABG Remover)
<img src="https://user-images.githubusercontent.com/48423148/229968905-e3ddcb5a-9421-4139-acdb-b9e4429e21e5.png" width="30%">

- PBRemTools(CascadePSP)
<img src="https://user-images.githubusercontent.com/48423148/229969256-d9c2e93f-9767-4ab9-a900-44c4051c281d.png" width="30%">

- ABG Remover
<img src="https://user-images.githubusercontent.com/48423148/229969296-c1367d84-056b-42e6-af5e-761234ae4e7b.png" width="30%">


- RemBG
<img src="https://user-images.githubusercontent.com/48423148/229969693-b7cf06f8-bd01-4dea-b604-f8f98a8c0d5d.png" width="30%">


# Tools
## Tile division ABG Remover
This tool is based on Anime Remove Background(https://huggingface.co/spaces/skytnt/anime-remove-background) and ABG_extension(https://github.com/KutsuyaYuki/ABG_extension).

Post-processing is added for more precise cropping based on the mask image generated by Anime Remove Background.

In this post-processing step, the input image is divided into a specified number of tiles, and the pixels in each tile are clustered based on color information.

<img src="https://user-images.githubusercontent.com/48423148/229971110-2a2e60b2-9ddb-408e-b4c9-0a909ee9b9ae.png" width="30%">


Extract clusters whose mask image content exceeds a threshold value as foreground.

### Parameters
- horizontal split num: Number of horizontal tile divisions.
- vertical split num: Number of vertical tile segments.
- n_cluster: Number of clusters based on color information.
- alpha threshold: Transparency of the mask considered as foreground.
- mask content ratio: Threshold for how much mask a cluster should contain to be considered foreground.


## CascadePSP
This tool is based on CascadePSP(https://github.com/hkchengrex/CascadePSP).

# Installation
- Stable diffusion web ui.
Install from webui's Extensions tab.

## Precautions
This program uses code that contains the Apache License 2.0

# API
Currently, there are two APIs available:
 - To get the currently available SAM model: `GET http://localhost:7861/pbrem/sam-model`
 - To process an image: `POST http://localhost:7861/pbrem/predict`

After launching the web UI API, you can visit the detailed API documentation at `http://localhost:7861/redoc`
