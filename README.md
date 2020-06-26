﻿# Wii U Plugin Loader Backend
This is the Backend for the [WiiUPluginSystem](https://github.com/Maschell/WiiUPluginSystem). Check out the readme for more information about the Plugin System.

## Usage
Put the `PluginBackend.wms` in the `sd:/wiiu/modules` folder of your sd card and load it via the [SetupPayload](https://github.com/wiiu-env/SetupPayload).

Plugins needs to be placed into the following folder:

```
sd:/wiiu/plugins
```


Plugins can be disabled/enabled using the [WiiUPluginSystemGUI](https://github.com/wiiu-env/WiiUPluginLoaderGUI).

## Building
In order to be able to compile this, you need to have devkitPPC installed
[devkitPPC](https://devkitpro.org/wiki/Getting_Started) with the following
pacman packages installed.

```
pacman -Syu devkitPPC
```

Make sure the following environment variables are set:
```
DEVKITPRO=/opt/devkitpro
DEVKITPPC=/opt/devkitpro/devkitPPC
```

Also make sure to install [wut](https://github.com/decaf-emu/wut), [WiiUPluginSystem](https://github.com/wiiu-env/WiiUPluginSystem) and the [WiiUModuleSystem](https://github.com/wiiu-env/WiiUModuleSystem).
It requires the [FunctionPatcherModule](https://github.com/wiiu-env/FunctionPatcherModule) to be running at the same time and it's linking aginst [libfunctionpatcher](https://github.com/wiiu-env/libfunctionpatcher).

## Building using the Dockerfile

It's possible to use a docker image for building. This way you don't need anything installed on your host system.

```
# Build docker image (only needed once)
docker build . -t wiiupluginloaderbackend-builder

# make 
docker run -it --rm -v ${PWD}:/project wiiupluginloaderbackend-builder make

# make clean
docker run -it --rm -v ${PWD}:/project wiiupluginloaderbackend-builder make clean
```

# Credits
- Maschell
- orboditilt
- https://github.com/serge1/ELFIO