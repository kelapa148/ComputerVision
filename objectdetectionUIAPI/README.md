# Object Detection With Front-End & Rest API Services
Application of object detection with Front-End and RestAPI services. Detect using library [yolo5](https://github.com/ultralytics/yolov5) object detection model from [pytorch hub](https://pytorch.org/hub/ultralytics_yolov5/) via a [flask](https://flask.palletsprojects.com/en/1.1.x/) api/app.

## Web app
Simple app consisting of a form where you can upload an image, and see the inference result of the model in the browser. Run:

`$ python3 web.py --port 8080`

then visit http://localhost:8080/ in your browser:


## Rest API
Simple rest API exposing the model for consumption by another service. Run:

`$ python3 api.py --port 8081`

Then use [curl](https://curl.se/) to perform a request:

`$ curl -X POST -F image=@tests/image.jpg 'http://localhost:8080/v1/object-detection/v5s'`

The model inference results are returned:

```
[{'class': 0,
  'confidence': ,
  'name': 
  'xmax': 
  'xmin': 
  'ymax': 
  'ymin': }]
```

## Run & Develop locally
Run locally for dev, requirements mostly originate from [yolov5](https://github.com/ultralytics/yolov5/blob/master/requirements.txt):
* `python3 -m venv venv`
* `source venv/bin/activate`
* `(venv) $ pip install -r requirements.txt`
* `(venv) $ python3 api.py --port 8081`

An example python script to perform inference using [requests](https://docs.python-requests.org/en/master/) is given in `tests/test_request.py`

## Docker
The example dockerfile shows how to expose the rest API:
```
# Build
docker build -t object-detection-api .
# Run
docker run -p 8080:8080 object-detection-api:latest
```


