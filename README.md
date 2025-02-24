# Welcome
#### *Read original [README](https://github.com/graphdeco-inria/gaussian-splatting/blob/main/README.md) first!*

## Requirements
- [CUDA-ready GPU with Compute Capability 7.0+](https://developer.nvidia.com/cuda-gpus)
- [Ubuntu 22](https://releases.ubuntu.com/jammy/)
- [Conda](https://www.anaconda.com/download/success)

## Cloning the Repository
The repository contains submodules, thus please check it out with 
```shell
# SSH
git clone git@github.com:mohamdlog/gaussian-splatting.git --recursive
```
or
```shell
# HTTPS
git clone https://github.com/mohamdlog/gaussian-splatting --recursive
```

## Setup

Follow these steps to set up the environment:

1. Create the Conda environment using the provided `environment.yml`:

    ```shell
    conda env create --file environment.yml
    ```

2. Activate the Conda environment:

    ```shell
    conda activate gaussian_splatting
    ```

3. Install the required Python packages from the submodules:

    ```shell
    pip install submodules/diff-gaussian-rasterization submodules/simple-knn submodules/fused-ssim
    ```

Once these steps are completed, the environment should be ready to use!

## Helpful Info

To ensure that CUDA-related environment variables are properly set when activating and deactivating the Conda environment,
add the following code to your `~/.bashrc` file:

```bash
# Conda environment activation/deactivation to manage variables
update_cuda_home() {
    if [[ -n "$CONDA_PREFIX" ]]; then
        export CUDA_HOME="$CONDA_PREFIX"
        export PATH=$CONDA_PREFIX/bin:$PATH
        export LD_LIBRARY_PATH="$CUDA_HOME/lib:$LD_LIBRARY_PATH"
    else
        unset CUDA_HOME  # Unset when no environment is active
    fi
}

# Ensure the update function is called every time the shell prompt changes
export PROMPT_COMMAND="update_cuda_home; $PROMPT_COMMAND"

