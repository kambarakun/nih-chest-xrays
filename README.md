# Pre-trained model of [NIH Chest X-rays](https://www.kaggle.com/nih-chest-xrays/data)

Dataset is available on Kaggle, [https://www.kaggle.com/nih-chest-xrays/data](https://www.kaggle.com/nih-chest-xrays/data)

## Model

* fastai
* efficientnet_pytorch b0
* input shape is `224x224x1`

## AWS instance used

* Deep Learning AMI (Ubuntu 18.04) Version 27.0
* `p3.2xlarge` or `p3dn.24xlarge`
* 240 GB storage
* open 8888 port

### Set up

```
conda install -y -c fastai fastai opencv
pip install -y efficientnet_pytorch kaggle pydicom
```

```
mkdir /home/ubuntu/.kaggle
echo '{"username":"kambarakun","key":"**********"}' > /home/ubuntu/.kaggle/kaggle.json
chmod 600 /home/ubuntu/.kaggle/kaggle.json
```

```
kaggle datasets download -d nih-chest-xrays/data
unzip -d data data.zip
mkdir /home/ubuntu/nih-chest-xrays
mkdir /home/ubuntu/nih-chest-xrays/input
mkdir /home/ubuntu/nih-chest-xrays/working
mv    /home/ubuntu/data /home/ubuntu/nih-chest-xrays/input/
```

```
mkdir /home/ubuntu/nih-chest-xrays/input/alias
ln -s /home/ubuntu/nih-chest-xrays/input/data/images_001/images/*.png /home/ubuntu/nih-chest-xrays/input/alias
ln -s /home/ubuntu/nih-chest-xrays/input/data/images_002/images/*.png /home/ubuntu/nih-chest-xrays/input/alias
ln -s /home/ubuntu/nih-chest-xrays/input/data/images_003/images/*.png /home/ubuntu/nih-chest-xrays/input/alias
ln -s /home/ubuntu/nih-chest-xrays/input/data/images_004/images/*.png /home/ubuntu/nih-chest-xrays/input/alias
ln -s /home/ubuntu/nih-chest-xrays/input/data/images_005/images/*.png /home/ubuntu/nih-chest-xrays/input/alias
ln -s /home/ubuntu/nih-chest-xrays/input/data/images_006/images/*.png /home/ubuntu/nih-chest-xrays/input/alias
ln -s /home/ubuntu/nih-chest-xrays/input/data/images_007/images/*.png /home/ubuntu/nih-chest-xrays/input/alias
ln -s /home/ubuntu/nih-chest-xrays/input/data/images_008/images/*.png /home/ubuntu/nih-chest-xrays/input/alias
ln -s /home/ubuntu/nih-chest-xrays/input/data/images_009/images/*.png /home/ubuntu/nih-chest-xrays/input/alias
ln -s /home/ubuntu/nih-chest-xrays/input/data/images_010/images/*.png /home/ubuntu/nih-chest-xrays/input/alias
ln -s /home/ubuntu/nih-chest-xrays/input/data/images_011/images/*.png /home/ubuntu/nih-chest-xrays/input/alias
ln -s /home/ubuntu/nih-chest-xrays/input/data/images_012/images/*.png /home/ubuntu/nih-chest-xrays/input/alias
```

```
jupyter notebook --generate-config -y
jupyter notebook password
# password
# password
```

```
echo "c.NotebookApp.ip = '*'"             >> /home/ubuntu/.jupyter/jupyter_notebook_config.py
echo "c.NotebookApp.open_browser = False" >> /home/ubuntu/.jupyter/jupyter_notebook_config.py
echo "c.NotebookApp.port = 8888"          >> /home/ubuntu/.jupyter/jupyter_notebook_config.py
```

```
nohup jupyter lab &
```
