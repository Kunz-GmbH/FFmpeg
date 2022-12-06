


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

execute ./confgure in ffmpeg source dir
make

full Build: 
    --enable-gpl --enable-version3 --enable-shared --disable-w32threads --disable-autodetect --enable-fontconfig  --enable-iconv --enable-gnutls --enable-libxml2 --enable-gmp --enable-lzma --enable-libsnappy --enable-zlib --enable-librist --enable-libsrt --enable-libssh --enable-libzmq --enable-libbluray --enable-libcaca --enable-sdl2 --enable-libdav1d --enable-libzvbi --enable-librav1e --enable-libsvtav1 --enable-libwebp --enable-libx264 --enable-libx265 --enable-libxvid --enable-libaom --enable-libopenjpeg --enable-libvpx --enable-libass --enable-frei0r --enable-libfreetype --enable-libfribidi --enable-libvidstab --enable-libvmaf --enable-libzimg --enable-amf --enable-cuda-llvm --enable-cuvid --enable-ffnvcodec --enable-nvdec --enable-nvenc --enable-d3d11va --enable-dxva2 --enable-libmfx --enable-libglslang --enable-vulkan --enable-opencl --enable-libcdio --enable-libgme --enable-libmodplug --enable-libopenmpt --enable-libopencore-amrwb --enable-libmp3lame --enable-libshine --enable-libtheora --enable-libtwolame --enable-libvo-amrwbenc --enable-libilbc --enable-libgsm --enable-libopencore-amrnb --enable-libopus --enable-libspeex --enable-libvorbis --enable-ladspa --enable-libbs2b --enable-libflite --enable-libmysofa --enable-librubberband --enable-libsoxr --enable-chromaprint



debug:  ./configure --enable-debug=3 --disable-optimizations
https://github.com/neptune46/ffmpeg-vscode



check if we have new frame if not wait for x ms and then we have a connection los -> try to restart connection?
get_video_frame

reconnect? simple just restart connection


Testing:
docker run --rm -it -e RTSP_PROTOCOLS=tcp -p 8554:8554 -p 1935:1935 -p 8888:8888 aler9/rtsp-simple-server
./ffmpeg -f gdigrab -framerate 30 -i desktop -f rtsp rtsp://localhost:8554/mystream
./ffmpeg -f lavfi -i testsrc=size=1280x720:rate=30 -f rtsp rtsp://localhost:8554/mystream

.\ffplay.exe rtsp://localhost:8554/mystream -pipename \\.\\pipe\\pipe1 -x 400 -y 200 -left 50 -top 50 -noborder