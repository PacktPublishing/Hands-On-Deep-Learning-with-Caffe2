# BlueWhale (Applied Reinforcement Learning @ Facebook)

`BlueWhale` is a Caffe2-based Reinforcement learning library built by Facebook. 

## Install


### Python3

### Caffe2
BlueWhale runs on any platform that supports caffe2. To install caffe2, you can use conda:

```
conda install -c caffe2 caffe2
```


Alternatively, you can build from source outlined in this tutorial: Installing Caffe2.

You may need to override caffe2's cmake defaults to use homebrew's protoc instead of Anaconda's protoc and to use Anaconda's Python instead of system Python. Also add the following switch when running cmake to make sure caffe2 uses python3:
```
cmake -DPYTHON_EXECUTABLE=`which python3`
```
Also make sure cmake is using the homebrew version of glog, etc.. Sometimes caffe2 will try to use the anaconda version of these libraries, and that will cause errors.


### PyTorch
Some of the models are implemented in PyTorch which can be installed via conda:

```
pip install http://download.pytorch.org/whl/torch-0.4.0-cp36-cp36m-macosx_10_7_x86_64.whl
pip install http://download.pytorch.org/whl/torchvision-0.1.6-py3-none-any.whl
```

Alternatively, you can build directly from source as outlined here: Installing Pytorch. Sometimes the latest PyTorch changes are not included in the version conda installs which can lead to errors. In this case building PyTorch from source should mitigate the issue.


### Thrift
Most distributions contain Apache Thrift. Because we are running python3, we need at least thrift 0.10. For OS/X:
```
brew install thrift
```

Then we need the python bindings for thrift, which we can get from anaconda:

```
conda install thrift
```
### OpenAI Gym
Running models in OpenAI Gym environments requires platforms with OpenAI Gym support. Windows support for OpenAI Gym is being tracked here.

OpenAI Gym can be installed using pip which should come with your python installation in the case of linux or with anaconda in the case of OSX. To install the basic environments (classic control, toy text, and algorithmic), run:
```
pip install gym
```

To install all environments, run this instead:

```
pip install "gym[all]"
```

### Installation and setup
clone from the source:
```
git clone https://github.com/bittnt/BlueWhale.git
cd BlueWhale
```

Create thrift generated code within the root directory:
```
thrift --gen py --out . ml/rl/thrift/core.thrift
```

To access caffe2 and import our modules:
```
export PYTHONPATH=/usr/local:./:$PYTHONPATH
```

### Running Unit Tests
From within the root directory, run all of our unit tests with:
```
python -m unittest discover
```

To run a specific unit test:
```
python -m unittest <path/to/unit_test.py>
```

## Experiment with OpenAI Gym Cartpole_v0 using Deep Q Network (DQN)

```
python ml/rl/test/gym/run_gym.py -p ml/rl/test/gym/discrete_pytorch_dqn_cartpole_v0.json
```


![BlueWhale Logo](https://raw.githubusercontent.com/facebookresearch/BlueWhale/master/logo/cover_image_light.png)

Please visit our [website](https://facebookresearch.github.io/BlueWhale/) for more information.
