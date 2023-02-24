# nnU-net data-preprocessing and training step

note: I use nnUnet instead of nnunet in picai_baseline

Script Clone
```
git clone https://github.com/MIC-DKFZ/nnUNet.git
cd nnUNet
pip install -e .
```

## This model need to setup environment
```
export nnUNet_raw_data_base="/output"
export nnUNet_preprocessed="/output/nnUNet_preprocessed"
export RESULTS_FOLDER="/output/nnUNet_trained_models"

```

note: `export nnUnet_raw_data_base="/output"` should set only `/output` because the example recommand this structure

    ```
    nnUNet_raw_data_base/nnUNet_raw_data/Task002_Heart
    ├── dataset.json
    ├── imagesTr
    │   ├── la_003_0000.nii.gz
    │   ├── la_004_0000.nii.gz
    │   ├── ...
    ├── imagesTs
    │   ├── la_001_0000.nii.gz
    │   ├── la_002_0000.nii.gz
    │   ├── ...
    └── labelsTr
        ├── la_003.nii.gz
        ├── la_004.nii.gz
        ├── ...
    ```
 You can set only parent of `nnUNet_raw_data`




## Run data prepare
```
python3 -m picai_prep mha2nnunet_settings --structure picai_archive --input /input/images/ --annotations /input/labels/csPCa_lesion_delineations/human_expert/resampled --json /workdir/mha2nnunet_settings.json
```

```
python3 -m picai_prep mha2nnunet --input /input/images --annotations /input/labels/csPCa_lesion_delineations/human_expert/resampled --output /output/nnUNet_raw_data --json /workdir/mha2nnunet_settings.json
```

https://github.com/MIC-DKFZ/nnUNet#how-to-run-nnu-net-on-a-new-dataset
train 0 is fold 0

3D
```
nnUNet_plan_and_preprocess -t 2201 -pl3d ExperimentPlanner3D_v21
nnUNet_train 3d_fullres nnUNetTrainerV2 2201 0
```

2D
```
nnUNet_plan_and_preprocess -t 2201 -pl2d ExperimentPlanner2D_v21
nnUNet_train 2d nnUNetTrainerV2 2201 0
```
