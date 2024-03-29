P2PaLA
======

:exclamation::exclamation: P2PaLA is deprecated :exclamation::exclamation: 



[![Python Version](https://img.shields.io/badge/python-2.7%2C%203.6-blue.svg)](https://www.python.org/)
[![Code Style](https://img.shields.io/badge/code%20style-black-000000.svg)](https://github.com/ambv/black)

Page to [PAGE](http://www.primaresearch.org/tools/PAGELibraries) Layout Analysis (P2PaLA) is a toolkit for Document Layout Analysis based on Neural Networks.

:boom: Try our new [DEMO](http://prhlt-carabela.prhlt.upv.es/tld/) for online baseline detection. :exclamation::exclamation: 

If you find this toolkit useful in your research, please cite:
```
@misc{p2pala2017,
  author = {Lorenzo Quirós},
  title = {P2PaLA: Page to PAGE Layout Analysis tookit},
  year = {2017},
  publisher = {GitHub},
  note = {GitHub repository},
  howpublished = {\url{https://github.com/lquirosd/P2PaLA}},
}
```
Check this paper for more details [Arxiv](https://arxiv.org/abs/1806.08852).



Requirements
===========

- Linux (OSX may work, but untested.).
- [Python](https://www.python.org/) (2.7, 3.6 under [conda virtual environment](https://www.anaconda.com/download/#linux) is recomended)
- [Numpy](http://www.numpy.org/) <!--- (installed by default using conda) -->
- [PyTorch](http://pytorch.org) (1.0). PyTorch 0.3.1 compatible on this [branch](https://github.com/lquirosd/P2PaLA/tree/PyTorch-v0.3.1)
- [OpenCv](https://github.com/opencv/opencv/releases/tag/3.4.5) (3.4.5.20). <!--- `conda install -c menpo opencv` -->
- NVIDIA GPU + CUDA CuDNN (CPU mode and CUDA without CuDNN works, but is not recomended for training).
- [tensorboard-pytorch](https://github.com/lanpa/tensorboard-pytorch) (v0.9) [Optional]. `pip install tensorboardX` > A diferent conda env is recomended to keep tensorflow separated from PyTorch

Install
=======
```bash
python setup.py install
```

> To install python dependencies alone, use  [requirements file](conda_requirements.yml) `conda env create --file conda_requirements.yml`

Usage
=====
1. Input data must follow the folder structure `data_tag/page`, where images must be into the `data_tag` folder and xml files into `page`. For example:
```bash
mkdir -p data/{train,val,test,prod}/page;
tree data;
```

```
data
├── prod
│   ├── page
│   │   ├── prod_0.xml
│   │   └── prod_1.xml
│   ├── prod_0.jpg
│   └── prod_1.jpg
├── test
│   ├── page
│   │   ├── test_0.xml
│   │   └── test_1.xml
│   ├── test_0.jpg
│   └── test_1.jpg
├── train
│   ├── page
│   │   ├── train_0.xml
│   │   └── train_1.xml
│   ├── train_0.jpg
│   └── train_1.jpg
└── val
    ├── page
    │   ├── val_0.xml
    │   └── val_1.xml
    ├── val_0.jpg
    └── val_1.jpg
```

2. Run the tool.

```bash
python P2PaLA.py --config config.txt --tr_data ./data/train --te_data ./data/test --log_comment "_foo"
```
> :exclamation: Pre-trained models available [here](egs/pre_trained)

3. Use TensorBoard to visualize train status:

```bash
tensorboard --logdir ./work/runs
```
4. xml-PAGE files must be at "./work/results/test/"

> We recommend [Transkribus](https://transkribus.eu/Transkribus/) or [nw-page-editor](https://github.com/mauvilsa/nw-page-editor) 
> to visualize and edit PAGE-xml files.

5. For detail about arguments and config file, see [docs](docs) or `python P2PaLA.py -h`. 
6. For more detailed example see [egs](egs):
    * Bozen dataset [see](egs/Bozen)
    * cBAD complex competition dataset [see](egs/cBAD_complex)
    * OHG dataset [see](egs/OHG)


License
=======
GNU General Public License v3.0
See [LICENSE](LICENSE) to see the full text.

Acknowledgments
===============
Code is inspired by [pix2pix](https://github.com/phillipi/pix2pix) and [pytorch-CycleGAN-and-pix2pix](https://github.com/junyanz/pytorch-CycleGAN-and-pix2pix)


