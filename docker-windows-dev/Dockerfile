# escape=`

# ARG BASE_TAG=windowsservercore-ltsc2016

FROM sunt05/docker-windows-python-msys2

SHELL ["powershell", "-command"]

# install necessary python packages
RUN pip install numpy pathlib


# set make as visible from mingw-make
RUN Copy-Item -Path C:\msys64\mingw64\bin\mingw32-make.exe -Destination C:\msys64\mingw64\bin\make.exe

# set path for MinGW64 bin
RUN $path = $env:path + ';c:\msys64\mingw64\bin'; Set-ItemProperty -Path 'HKLM:\SYSTEM\CurrentControlSet\Control\Session Manager\Environment\' -Name Path -Value $path


CMD ["powershell"]
