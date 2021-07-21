PyTorch binaries for Raspberry Pi OS (Debian 10 Buster)

# Download `whl` package
- [Show releases](https://github.com/jungin500/pytorch-rpi/releases/tag/210721)

# Build Details
## Environment
- Raspberry Pi 4 Model B (4GB) with [zram](https://ikarus.sg/using-zram-to-get-more-out-of-your-raspberry-pi/) enabled + [overclocked*](https://haydenjames.io/raspberry-pi-3-overclock/)
  → **DON'T TRY UNLESS YOU KNOW ALL DISADVENTAGES**
- OS: Raspberry Pi OS Lite 2021-05-28 ([32bit](https://downloads.raspberrypi.org/raspios_lite_armhf/images/raspios_lite_armhf-2021-05-28/)/[64bit](https://downloads.raspberrypi.org/raspios_lite_arm64/images/raspios_lite_arm64-2021-05-28/), respectively)
- Python: 3.7.3 (OS-specific version of `apt-get install python3 python3-dev`)
- Pip3: 21.1.3 ([removed `python3-pip` package, and clean-installed newer one with `get-pip.py`](https://pip.pypa.io/en/stable/installing/#installing-with-get-pip-py))
- Numpy: 1.16.2

## Build options
```
export NO_CUDA=1
export NO_DISTRIBUTED=1
export NO_MKLDNN=1
export BUILD_TEST=0
export MAX_JOBS=$(nprocs)
export USE_OPENMP=1

python3 setup.py bdist_wheel
```
- After ~4hrs, built wheel file will be in `dist/` folder with  
  filename `torch-${torch_ver}+git${git_hash}-cp37-cp37m-linux_${architecture}.whl`.

## See Also
- Using `zram` is mandatory, as building `pytorch` from source is memory-hungry task(~about 6GB as I know).
- I don't recommend overclocking your Pi (unless you know what you're doing, **as it would void Pi's warrenty!**).  
  → but overclocking Pi will result much faster CXX build process.

# Refer & Thanks to
- [nmilosev/pytorch-arm-builds](https://github.com/nmilosev/pytorch-arm-builds)
- [pytorch/pytorch](https://github.com/pytorch/pytorch#get-the-pytorch-source)
