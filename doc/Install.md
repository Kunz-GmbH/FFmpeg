


Install msys https://www.msys2.org/

# normal msys2 packages
pacman -S make pkgconf diffutils

# mingw-w64 packages and toolchains
pacman -S mingw-w64-x86_64-nasm mingw-w64-x86_64-gcc mingw-w64-x86_64-SDL2
pacman -S yasm
pacman -S make
pacman -S diffutils
pacman -S mingw-w64-x86_64-gdb


add C:\msys64\mingw64\bin to path

run ./confgure in ffmpeg source dir
make



debug:  ./configure --enable-debug=3 --disable-optimizations
https://github.com/neptune46/ffmpeg-vscode



check if we have new frame if not wait for x ms and then we have a connection los -> try to restart connection?
get_video_frame

reconnect? simple just restart connection


Testing:
docker run --rm -it -e RTSP_PROTOCOLS=tcp -p 8554:8554 -p 1935:1935 -p 8888:8888 aler9/rtsp-simple-server
./ffmpeg -f gdigrab -framerate 30 -i desktop -f rtsp rtsp://localhost:8554/mystream
.\ffplay.exe rtsp://localhost:8554/mystream -pipename \\.\\pipe\\pipe1 -x 400 -y 200 -left 50 -top 50 -noborder