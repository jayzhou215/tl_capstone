## this project is following [alex-lechner tutorial](https://github.com/alex-lechner/Traffic-Light-Classification)

## model
```
mkdir models
cd models
wget http://download.tensorflow.org/models/object_detection/ssd_inception_v2_coco_2017_11_17.tar.gz
tar -xvzf ssd_inception_v2_coco_2017_11_17.tar.gz
```

## dataset
train with [Vatsal's dataset](https://github.com/coldKnight/TrafficLight_Detection-TensorFlowAPI#get-the-dataset) and validate with [alex lechner's dataset](https://www.dropbox.com/s/vaniv8eqna89r20/alex-lechner-udacity-traffic-light-dataset.zip?dl=0)
```
cd path/to/project
mkdir data
cd data
wget https://www.dropbox.com/s/vaniv8eqna89r20/alex-lechner-udacity-traffic-light-dataset.zip?dl=0
unzip alex-lechner-udacity-traffic-light-dataset.zip?dl=0 ## Don't miss the ``?dl=0`` part when unzipping!
```

## env
```sh
# pip install tensorflow==1.4
pip install tensorflow-gpu==1.4
sudo apt-get install protobuf-compiler python-pil python-lxml python-tk
# object_detection
cd ../path/to/project
mkdir tf_models
cd tf_models
git clone https://github.com/tensorflow/models.git
git checkout f7e99c0
cd models/research/
protoc object_detection/protos/*.proto --python_out=.
# add object_detection and slim to python path, 
export PYTHONPATH=$PYTHONPATH:`pwd`:`pwd`/slim
# test valid
python object_detection/builders/model_builder_test.py
```

note, in `train.py` I use following to import dependencies.
```
sys.path.append('../tf_models/models/research/')  # NOQA: E402
sys.path.append('../tf_models/models/research/slim')  # NOQA: E402
```


## train
```
```

## troubleshoot
command not found: protobuf
```sh
wget https://github.com/protocolbuffers/protobuf/releases/download/v3.6.1/protobuf-all-3.6.1.zip
unzip protobuf-all-3.6.1.zip
cd protobuf-all-3.6.1
./configure
make
make check
sudo make install
sudo ldconfig # refresh shared library cache.
```