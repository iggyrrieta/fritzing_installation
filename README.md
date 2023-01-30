# Fritzing

Guide to test ``Fritzing` and play around before buying it.

## Requirements

> Library `libgit2` must be at same level folder than `fritzing-app`.

Build `libgit2`:

```bash
sudo apt-get install libssl-dev libssh2-1-dev
git clone https://github.com/libgit2/libgit2
cd libgit2
mkdir build && cd build
cmake .. -D BUILD_SHARED_LIBS=OFF
sudo cmake --build . --target install
```

## Build Fritzing app

```bash
sudo apt-get install build-essential git cmake libssl-dev libudev-dev libqt5serialport5-dev libqt5svg5-dev
```

```bash
git clone https://github.com/fritzing/fritzing-app
git clone https://github.com/fritzing/fritzing-parts
cd fritzing-app
```

Add the following lines on top of `fritzing-app/phoenix.pro`:

```bash
QMAKE_LFLAGS += "-Wl,--copy-dt-needed-entries"
QMAKE_LFLAGS += "-lssh2"
```

Compile:

```bash
qmake
make
```

## Running Fritzing

```bash
./fritzing
```

## Add desktop app to shared applications

```bash
sudo cp Fritzing.desktop /usr/share/applications/
```

> Now you can easily find Fritzing when looking inside applications
