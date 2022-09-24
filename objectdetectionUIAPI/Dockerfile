FROM python:3.8-slim-buster

RUN apt-get update -y
RUN apt-get install ffmpeg libsm6 libxext6  -y

WORKDIR /app
ADD . /app
RUN pip install -r requirements.txt

EXPOSE 8081

CMD ["python", "web.py", "--port=8080"]

# CMD ["python", "api.py", "--port=8081"]