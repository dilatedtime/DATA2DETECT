# Traffic Sign Detection

`Traffic.ipynb` is a Google Colab workflow for finding traffic signs in road images. It converts eight-point text annotations into YOLO boxes, trains an Ultralytics YOLO detector, validates the model, and runs inference on the validation set. The notebook also contains a TensorFlow image-classification experiment built from the same project data.

## Saved training run

The notebook records a 50-epoch YOLO run on a Tesla T4. Its best saved validation result used 250 images and 129 sign instances:

- Precision: 0.84
- Recall: 0.776
- mAP50: 0.819
- mAP50-95: 0.324

These are notebook outputs from one run, not a benchmark across datasets or hardware.

## Data layout

The dataset and trained weights are not committed. The notebook expects a Google Drive folder named `YOLO_sign_detection` with this general structure:

```text
YOLO_sign_detection/
  dataset/
    train/
      images/
      labels/
    val/
      images/
      labels/
  classification_raw/
  models/
  results/
```

The original labels contain polygon coordinates. Early cells convert them into YOLO label files and generate `data.yaml` before training.

## Run it

1. Open `Traffic.ipynb` in Google Colab.
2. Put the dataset in your Google Drive using the layout above.
3. Check the `DRIVE_ROOT` and `DR` path variables.
4. Run the conversion and preview cells before starting training.
5. Use a GPU runtime if you plan to reproduce the 50-epoch detector run.

The notebook installs large machine-learning packages and writes models and results back to Drive. Run the setup cells in a fresh Colab session instead of treating this repository as a ready-to-run local package.

