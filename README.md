# Zephyr Example Application

This repository contains a ASK Zephyr example application. The main purpose of this
repository is to serve as a reference on how to structure Zephyr based
applications. Some of the features demonstrated in this example are:

- Basic [Zephyr application][app_dev] skeleton
- [Zephyr workspace applications][workspace_app]
- [West T2 topology][west_t2]

## input directories:
- application/app    (application)

## output directories:
- build         (application)

## Getting Started

Before getting started, make sure you have a proper Zephyr development
environment. You can follow the official
[Zephyr Getting Started Guide](https://docs.zephyrproject.org/latest/getting_started/index.html).

## Initialization

The first step is to initialize the workspace folder (``workspace_name``) where
all ``applications`` and all modules will be cloned. You can do that by running:


### initialize <workspace_name> for the example-application (main branch)
```shell
west init -m https://ask-pdas-platform@dev.azure.com/ask-pdas-platform/zephyr_playground/_git/zephyr_hello_ask --mr main <workspace_name>
```

### update all Zephyr modules  (git sync)
```shell
cd <workspace_name>
west update
```

### init Zephyr workspace to support multiple workspaces
```shell
cd <workspace_name>
west zephyr-export
```


## Build and configuration commands , all west commands shall be called from <workspace_name>
### all images shall be build first time with pristine (ensure deleting previous build output)
```shell
west build --pristine -b esp32_devkitc_wroom application/app
``` 
or with generating eclipse project
```shell
west build --pristine -b esp32_devkitc_wroom application/app -- -G"Eclipse CDT4 - Ninja"
``` 

### rebuild all images
```shell
west build
```

### flash esp32
```shell
west flash
```

### monitor esp32
```shell
west flash
```


### run kconfig gui for application
```shell
west build -t guiconfig 
```



