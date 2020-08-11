# Framework for segmenting 3D Ultrasound

## Getting Started
Run the following commands to get the environment setup.
```
conda activate tf2_gpu
```
```
export TF_ENABLE_AUTO_MIXED_PRECISION=1 && export PATH=$PATH:/usr/local/cuda-10.0/bin && export CUDADIR=/usr/local/cuda-10.0 && export CUDA_VISIBLE_DEVICES=0,1 && export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/usr/local/cuda-10.0/lib64 && export TF_FORCE_GPU_ALLOW_GROWTH=true
```


### Running network
Update `config.py` with any configuration settings you wish to change.

#### Create datasets
```
python write.py --augment=True

# Non Augmented
python write.py
```

#### Train and evaluate model
```
python train.py --model=unet --batch_size=10 --num_epochs=50 --multi_modal=True
python train.py --model=unet++ --batch_size=10 --num_epochs=50 --multi_modal=True

# Single modal
python train.py --model=unet --batch_size=10 --num_epochs=50 
```