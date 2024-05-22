# Learning to Tranform Dynamically for Better Adversarial Transferability 

Adversarial examples, crafted by adding perturbations imperceptible to humans, can deceive neural networks. Recent studies identify the adversarial transferability across various models, \textit{i.e.}, the cross-model attack ability of adversarial samples. To enhance such adversarial transferability, existing input transformation-based methods diversify input data with transformation augmentation. However, their effectiveness is limited by the finite number of available transformations. In our study, we introduce a novel approach named Learning to Transform (L2T). L2T increases the diversity of transformed images by selecting the optimal combination of operations from a pool of candidates, consequently improving adversarial transferability. We conceptualize the selection of optimal transformation combinations as a trajectory optimization problem and employ a reinforcement learning strategy to effectively solve the problem. Comprehensive experiments on the ImageNet dataset, as well as practical tests with Google Vision and GPT-4V, reveal that L2T surpasses current methodologies in enhancing adversarial transferability, thereby confirming its effectiveness and practical significance.

![Overview](./figs.png)



## Usage

### Installation
- Python >= 3.6
- PyTorch >= 1.21
- Torchvision >= 0.13.1
- timm >= 0.6.12

```bash
pip install -r requirement.txt
```
### Import clean examples
Following from previous works, we randomly selecte 1,000 images from ImageNet validation set to run our experiments. All images can be classified properly. You can also construct you own example sets by contrust your folder in the following format. You can also download our prepared dataset from [Google Drive](https://drive.google.com/file/d/1C-XZioCi32VOwpTuaOkLzTbr_YIOA4vP/view?usp=sharing).
```
data
├─images
│  ├─ILSVR2012_val_00000051.JPEG
│  ├─...
│  └─ILSVR2012_val_00001501.JPEG
└─labels.csv
```
labels.csv is a two colums table folloing the (filename,label) format as below
```
filename,label
ILSVRC2012_val_00013716.JPEG,0
```

### Generate adversarial examples
You can run the following command to generate the adversarial examples.
```
python main.py --input_dir /path/to/data --output_dir path/to/advsample --attack l2t --model=resnet18
```
or simply 
```
python main.py 
```
if you put the data under the same directory and use the default settings

### Run for Evaluation
We run the evaluation across 10 models to verify the adversarial transferability of the generated examples by following command.
```
python main.py --eval
```
You can modify the **utils.py** to add or delete models.

## Credits
This repo is modified from [TransferAttack](https://github.com/Trustworthy-AI-Group/TransferAttack). Great Thanks!


