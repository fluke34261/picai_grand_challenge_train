# U-net data-preprocessing and training step

## Run data prepare
note: 
- Because this code prepare_data.py default labels must replace labelsdir from /input/picai_labels to /input/labels  	[Link](https://grand-challenge.org/forums/forum/pi-cai-607/topic/u-net-training-array-size-error-821/)
- Because this code did not set default size matrix (image size) for training [Link](https://github.com/DIAGNijmegen/picai_baseline/blob/main/unet_baseline.md#u-net---data-preparation)

Script
```
python3 src/picai_baseline/prepare_data.py --matrix_size 20 256 256 --spacing 3.0 0.5 0.5 --labelsdir /input/labels
```

## Run Plan data
```
python3 src/picai_baseline/unet/plan_overview.py
```

## Train U-net
```
python3 -u src/picai_baseline/unet/train.py --weights_dir='/workdir/results/UNet/weights/' --overviews_dir='/workdir/results/UNet/overviews/Task2201_picai_baseline' --folds 0 --max_threads 4 --enable_da 1 --num_epochs 250 --validate_n_epochs 1 --validate_min_epoch 0
```
