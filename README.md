# Roll Right

Roll Right uses a TensorFlow Lite image-classification model to distinguish
doors from other images. It can classify an image or process a video and return
the label predicted for its final frame.

## Project files

- `app/main.py` contains the image preprocessing and prediction functions.
- `models/model_unquant.tflite` is the model loaded for inference.
- `data/` contains sample images, and `tests/` contains test images and a video.

## Setup

From the repository root, install the Python dependencies:

```bash
python -m pip install -r requirements.txt
```

Keep the model at `models/model_unquant.tflite` and run the examples from the
repository root, since the model is loaded using a relative path.

## Classify an image

Import `predict_label` and pass it an image path:

```python
from app.main import predict_label

label = predict_label("data/door.jpeg")
print(label)  # "Door" or "Not Door"
```

## Classify a video

Use `predict_label_from_video` with a video path. The function processes each
frame and returns the prediction for the final frame:

```python
from app.main import predict_label_from_video

label = predict_label_from_video("tests/test.mp4")
print(label)  # "Door" or "Not Door"
```

## Run the tests

From the repository root:

```bash
python -m unittest discover -s tests
```
