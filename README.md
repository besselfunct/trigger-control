# trigger control  
**DISCLAIMER**  
dosen't seem to work atm for ubuntu 20.04 and distros based on it. (see https://github.com/Etaash-mathamsetty/trigger-control/issues/5)   
![image](https://user-images.githubusercontent.com/45927311/163625506-9b2f6ddc-59f1-4fad-be3c-473a107470b4.png)


a quick and dirty project that allows you to control the adaptive triggers of the dualsense controller on linux and windows using a gui  
~~currently only works through usb though the controller is detected through bluetooth~~  

now works through bluetooth and usb (thx ds4windows and dualsensectl for crc32.h)  

libraries:  
libSDL2  
libhidapi  
libgl  
glew  
glib2  

**installing them on arch linux (or any arch based distro):**  
`sudo pacman -S sdl2 hidapi glew libgl base-devel glib2`  

**How to compile**  

`make`  

**run**   
`./trigger-control`  

**install**  
install dependencies first
```
git clone https://github.com/Etaash-mathamsetty/trigger-control.git
cd trigger-control
chmod +x compile.sh
make
sudo cp trigger-control /usr/bin
```

**update**  
enter the directory in which you cloned this repo  
```
git pull
make
sudo cp trigger-control /usr/bin
```

**Cross Compile for Windows**  
I recommend arch linux for this, but you can try your luck with any other distro  
first, clone the repo, then run the following commands(with any AUR helper)  
```
yay -S mingw-w64-glew
yay -S mingw-w64-sdl2
yay -S mingw-w64-hidapi
```
remove glu dependencies from glew.pc  
```
sudo nano /usr/i686-w64-mingw32/lib/pkgconfig/glew.pc
sudo nano /usr/x86_64-w64-mingw32/lib/pkgconfig/glew.pc
```
then run,  
```
./windows-compile.sh
```
you will get a .exe file as an output, but you won't be able to run it without copying the nessessary dll files, so copy  
`libwinpthread-1.dll`  
`libhidapi-0.dll`  
`SDL2.dll`  
`glew32.dll`  
`libstdc++-6.dll`  
`libgcc_s_seh-1.dll`  
from  
`/usr/x86_64-w64-mingw32/bin/`  
to the folder the git repo is in, and now you should be able to run the windows version of the program... hopefully  
  
things I learned from this:  
cross compiling is a pain  
win32 api sucks  
programming on linux is kinda easy  
  
based on https://github.com/flok/pydualsense  
