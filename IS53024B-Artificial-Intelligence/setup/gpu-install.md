Reference [here](https://www.tensorflow.org/install/pip#linux).

```bash
conda install -c conda-forge cudatoolkit=11.8.0
python3 -m pip install nvidia-cudnn-cu11==8.6.0.163 tensorflow==2.13

# automatic setting of LD_LIBRARY_PATH upon `conda activate`
mkdir -p $CONDA_PREFIX/etc/conda/activate.d
echo 'CUDNN_PATH=$(dirname $(python -c "import nvidia.cudnn;print(nvidia.cudnn.__file__)"))' >> $CONDA_PREFIX/etc/conda/activate.d/env_vars.sh
echo 'export LD_LIBRARY_PATH=$CONDA_PREFIX/lib/:$CUDNN_PATH/lib:$LD_LIBRARY_PATH' >> $CONDA_PREFIX/etc/conda/activate.d/env_vars.sh

# nice option: tensorrt (optimisation)
# see here: https://stackoverflow.com/a/73703547/9638108
pip install nvidia-pyindex
pip install --upgrade nvidia-tensorrt

# we need to add tensorrt to the path
# !! works for Python 3.11, go check the directory below (tensorrt_libs) !!
echo 'export LD_LIBRARY_PATH=$CONDA_PREFIX/lib/python3.11/site-packages/tensorrt_libs:$LD_LIBRARY_PATH' >> $CONDA_PREFIX/etc/conda/activate.d/env_vars.sh

source $CONDA_PREFIX/etc/conda/activate.d/env_vars.sh

# automatic unsetting when deactivating
mkdir -p $CONDA_PREFIX/etc/conda/deactivate.d
echo 'unset LD_LIBRARY_PATH' >> $CONDA_PREFIX/etc/conda/deactivate.d/env_vars.sh

# Verify install:
python3 -c "import tensorflow as tf; print(tf.config.list_logical_devices())"
```
