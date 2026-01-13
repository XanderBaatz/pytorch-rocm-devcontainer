# PyTorch ROCm DevContainer
A simple and straight forward PyTorch ROCm DevContainer with CuPy support. Useful for ML and AI workloads on AMD GPUs. Initially made to work with SpaCy.

### Settings
All there is to configure manually is:
- The memory in the `devcontainer.json` file (currently set to `8G`).
- `HCC_AMDGPU_TARGET` and `HSA_OVERRIDE_GFX_VERSION` in the `Dockerfile`.
  - Run `rocminfo | grep gfx` in the terminal to determine the GPU.
- Any additional Python packages you wish to install at initialization in `requirements.txt`.
- For any packages that require NumPy or SciPy, it's a good idea to install them before CuPy. This is because CuPy will replace these packages with GPU-accelerated NumPy and SciPy equivalents.

### Notes when using `uv`
If `uv` is used, add this to the `pyproject.toml` file:
```sh
[tool.uv]
override-dependencies = [
    "torch; sys_platform == 'never'",
    "torchvision; sys_platform == 'never'",
]
```


## Credits
- [Base DevContainer template](https://github.com/mateuspinto/pytorch-amd-devcontainer)
- [Dockerfile CC compile fix](https://gitlab.msu.edu/wibkingb/quokka/-/blob/development/.devcontainer/rocm-container/Dockerfile?ref_type=heads)
