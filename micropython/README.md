## Micropython build

Micropython is not included in any of the raspbian repositories.  It's in most Unbuntu repositories and the debian unstable sid, but that one seg-faults on RPi0Wr1.  I've choosen the build tag "v1.21.0", but you can choose a later one.

1. sudo apt-get install build-essential git libffi-dev cmake gcc-arm-none-eabi libnewlib-arm-none-eabi
2. cd ~/src && git clone --branch "v1.21.0" https://github.com/micropython/micropython.git
3. cd ~/src/micropython/ports/unix && git checkout -b "local/v1.21.0"
4. make submodules && make
5. make test && make install
6. cd ~/src/micropython
7. make -C ports/rp2 submodules
8. make -C mpy-cross
9. cd ports/rp2 && make
10. cp build-RPI_PICO/firmware.uf2 /media/RPI-RP2

