# Learning to Tranform Dynamically for Better Adversarial Transferability 


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
Following from previous works, we randomly selecte 1,000 images from ImageNet validation set to run our experiments. All images can be classified properly. You can also construct you own example sets by contrust your folder in the following format. You can also download our prepared dataset from [Google Drive]().
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


