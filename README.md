# docker-windows-dev
Dockerfile for mingw64&python-based development for Windows


This Dockerfile is specifically designed for my personal mingw+python3 development for Windows targets on macOS platform.

# Quickstart for Windows-targeted development on macOS with `mingw`+`python3`

## 1. install Homebrew
``` bash
/usr/bin/ruby -e "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/master/install)"
```
## 2. install `Virtual Box` (free):
``` bash
brew cask install virtualbox
```
## 3. install `vagrant` for virtual machine management
``` bash
brew cask install vagrant
```
## 4. load a prebuilt VM Windows Server 2016 (10.0.14393 LTS channel)
``` bash
git clone https://github.com/StefanScherer/windows-docker-machine
cd windows-docker-machine
vagrant up --provider virtualbox 2016-box
```
## 5. install `Docker`
``` bash
brew install docker
```

## 6. List your new Docker machine
``` bash
docker-machine ls
```

## 7. switch to Windows docker environment
``` bash
eval $(docker-machine env 2016-box)
```

### if you need to switch back to macOS environment
``` bash
eval $(docker-machine env -unset)
```

## 8. use this Docker image (which will be automatically loaded from Docker Hub)
```
docker run -it -v C:$(pwd):C:/io sunt05/windows-dev powershell
```

### all necessary mingw binaries haved been added to `%PATH%`, some essential ones are listed below:
  * `make` (in fact a renamed copy of `mingw32-make` for easier access)
  * `gcc`+`gfortran`
  * `python3`+`numpy`


## References:
1. [StefanScherer/windows-docker-machine](https://github.com/StefanScherer/windows-docker-machine)
2. [mback2k/docker-windows-buildbot-msys2](https://github.com/mback2k/docker-windows-buildbot-msys2)
