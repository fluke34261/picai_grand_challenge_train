# PICAI Grand Challenge Training
PICAI Grand challenge training model step

## Read all from baseline
[baseline](https://github.com/DIAGNijmegen/picai_baseline)

## Create folder
```
sudo -i
mkdir /input
mkdir /workdir
mkdir /output
```

## Clone baseline
### can place any where
```
git clone https://github.com/DIAGNijmegen/picai_baseline
cd picai_baseline
pip install -e .
```

## Download dataset
```
curl -C - "https://zenodo.org/record/6624726/files/picai_public_images_fold0.zip?download=1" --output picai_public_images_fold0.zip
curl -C - "https://zenodo.org/record/6624726/files/picai_public_images_fold1.zip?download=1" --output picai_public_images_fold1.zip
curl -C - "https://zenodo.org/record/6624726/files/picai_public_images_fold2.zip?download=1" --output picai_public_images_fold2.zip
curl -C - "https://zenodo.org/record/6624726/files/picai_public_images_fold3.zip?download=1" --output picai_public_images_fold3.zip
curl -C - "https://zenodo.org/record/6624726/files/picai_public_images_fold4.zip?download=1" --output picai_public_images_fold4.zip
```

## Unzip all folds
```
unzip picai_public_images_fold0.zip -d /input/images/
unzip picai_public_images_fold1.zip -d /input/images/
unzip picai_public_images_fold2.zip -d /input/images/
unzip picai_public_images_fold3.zip -d /input/images/
unzip picai_public_images_fold4.zip -d /input/images/
```

## Clone labels
```
git clone https://github.com/DIAGNijmegen/picai_labels /input/labels/
```

## Generate work dir
```
python3 -m picai_baseline.splits.picai_nnunet --output "/workdir/splits/picai_nnunet"
```


## Then choose Model
- [U-net](U-net)
- [nnU-net](nnU-net)
