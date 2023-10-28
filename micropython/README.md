## Micropython build

Micropython is not included in any of the raspbian repositories.  It's in unstable sid, but that one seg-faults.  I've choosen the build tag "v1.21.0", but you can choose a later one.

1. sudo apt-get install build-essential git libffi-dev
2. cd ~/src && git clone --branch "v1.21.0" https://github.com/micropython/micropython.git
3. cd ~/src/micropython/ports/unix && git checkout -b "local/v1.21.0"
4. make submodules && make
5. make test && make install

