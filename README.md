# Discrete-Continuous-VLN
Code and Data of the **CVPR 2022** paper: <br>**Bridging the Gap Between Learning in Discrete and Continuous Environments for Vision-and-Language Navigation**<br>
[**Yicong Hong**](http://www.yiconghong.me/), **Zun Wang**, [Qi Wu](http://www.qi-wu.me/), [Stephen Gould](http://users.cecs.anu.edu.au/~sgould/)<br>

[[Paper & Appendices](https://arxiv.org/abs/2203.02764)] [[CVPR2022 Video](https://www.youtube.com/watch?v=caFGVwwSQbg)] [[GitHub](https://github.com/YicongHong/Discrete-Continuous-VLN)]

<p align="left">
<img src="./figures/traj_0.gif" width="47%" height="47%"/>
<img src="./figures/traj_1.gif" width="47%" height="47%"/>
</p>

"*Interlinked. Interlinked. What's it like to hold the hand of someone you love? Interlinked. Interlinked. Did they teach you how to feel finger to finger? Interlinked. Interlinked. Do you long for having your heart interlinked? Interlinked. Do you dream about being interlinked? Interlinked.*" --- [Blade Runner 2049 (2017)](https://www.imdb.com/title/tt1856101/).

<!-- "*Maybe it means something more - something we can't yet understand... I'm drawn across the universe to someone... Love is the one thing we're capable of perceiving that transcends dimensions of time and space. Maybe we should trust that, even if we can't understand it.*" --- [Interstellar (2014)](https://www.imdb.com/title/tt0816692/). -->

## TODOs
- [x] VLN-CE Installation Guide
- [ ] Submitted version of CMA and Recurrent-VLN-BERT with the Candidate Waypoint Predictor (CWP)
- [x] Pre-trained weights of the navigator networks and the CWP
- [ ] Candidate Waypoint Predictor training code
- [ ] Connectivity graphs in continuous environments
- [ ] Graph-walk in continous environments code

## Prerequisites

### Installation

Follow the [Habitat Installation Guide](https://github.com/facebookresearch/habitat-lab#installation) to install [`habitat-lab`](https://github.com/facebookresearch/habitat-lab) and [`habitat-sim`](https://github.com/facebookresearch/habitat-sim). We use version [`v0.1.7`](https://github.com/facebookresearch/habitat-lab/releases/tag/v0.1.7) in our experiments, same as in the [VLN-CE](https://github.com/jacobkrantz/VLN-CE), please refer to VLN-CE git page for more details. In brief:

1. Create a virtual environment. Clone a stable version from the github repository and install `habitat-lab`. We develop this project with Python 3.6. The command below will install the core of Habitat Lab as well as the habitat_baselines along with all additional requirements.
    ```bash
    git clone --branch v0.1.7 git@github.com:facebookresearch/habitat-lab.git
    cd habitat-lab
    python -m pip install -r requirements.txt
    python -m pip install -r habitat_baselines/rl/requirements.txt
    python -m pip install -r habitat_baselines/rl/ddppo/requirements.txt
    python setup.py develop --all # install habitat and habitat_baselines
    ```

2. Install `habitat-sim` for a machine with multiple GPUs or without an attached display (i.e. a cluster):
    ```bash
    conda install -c aihabitat -c conda-forge habitat-sim=0.1.7 headless
    ```

3. Install the learning packages (PyTorch 1.10.1):
    ```bash
    pip3 install torch==1.10.1+cu113 torchvision==0.11.2+cu113 torchaudio==0.10.1+cu113 -f https://download.pytorch.org/whl/cu113/torch_stable.html
    ```
      
4. Install other useful packages in our experiments:
    ```bash
    pip install fastdtw==0.3.4 networkx==2.5.1 dtw==1.4.0 msgpack_numpy==0.4.7.1 jsonlines==2.0.0
    ```

