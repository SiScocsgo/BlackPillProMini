#Open Settings (JSON)

"cortex-debug.armToolchainPath": "${env:VSARM}\\armcc\\bin\\"

Edit Projects, (Add project file)

{
    "name": "template_F3",
    "rootPath": "c:\\Users\\cristi.dbr\\Desktop\\STM32_Projects\\template_F3",
    "paths": [],
    "group": ""
  },
  
#C/CPP: Edit Configurations

{
    "configurations": [
    {
    "name": "STM32 Debug",
    "includePath": [
        "${env:VSARM}/armcc/arm-none-eabi/include/c++/7.3.1",
        "${env:VSARM}/armcc/arm-none-eabi/include/c++/7.3.1/arm-none-eabi",
        "${env:VSARM}/armcc/arm-none-eabi/include/c++/7.3.1/backward",
        "${env:VSARM}/armcc/lib/gcc/arm-none-eabi/7.2.1/include",
        "${env:VSARM}/armcc/lib/gcc/arm-none-eabi/7.2.1/include-fixed",
        "${env:VSARM}/armcc/arm-none-eabi/include",
        "${workspaceRoot}/Drivers/CMSIS/Include/",
        "${workspaceRoot}/Drivers/CMSIS/Include/",
        "${workspaceRoot}/Drivers/CMSIS/Device/ST/STM32F3xx/Include/",
        "${workspaceRoot}/Core/Inc",
        "${workspaceRoot}/Core/Src",
        "${workspaceRoot}/Inc",
        "${workspaceRoot}/Src",
        "${workspaceRoot}/Drivers/STM32F3xx_HAL_Driver/Inc",
        "${workspaceRoot}/Drivers/STM32F3xx_HAL_Driver/Inc/Legacy/",
        "${workspaceRoot}/Drivers/STM32F3xx_HAL_Driver/Src",
		"${workspaceRoot}/**"
    ],
    "defines": [
        "DEBUG",
        "DEFAULT_STACK_SIZE=2048",
        "HSE_VALUE=8000000",
        "OS_INCLUDE_STARTUP_INIT_MULTIPLE_RAM_SECTIONS",
        "PB_MSGID",
        "STM32F303",
        "STM32F303x8",
        "USE_DEVICE_MODE",
        "USE_FULL_ASSERT",
        "USE_HAL_DRIVER",
        "USE_USB_OTG_FS"
    ],
    "intelliSenseMode": "clang-x64",
    "browse": {
    "path": [
        "${workspaceRoot}",
        "${env:VSARM}/armcc"
    ],
    "limitSymbolsToIncludedHeaders": false,
    "databaseFilename": ""
    }
    }
    ],
    "version": 4
}

#Tasks, Configure Tasks (create JSON from template: other)

{
    // See https://go.microsoft.com/fwlink/?LinkId=733558
    // for the documentation about the tasks.json format
    "version": "2.0.0",
    "tasks": [
        {
            "label": "Make Firmware",
            "type": "shell",
            "command": "mingw32-make -j8 all TARGET=vsarm_firmware OPT=\"-O2\" BINPATH=\"${env:VSARM}armcc\/bin\"",
            "options": {
                "cwd": "${workspaceRoot}"
            }, 
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "problemMatcher": []
        },
        {
            "label": "Load Firmware",
            "type": "shell",
            "command": "st-flash write ./build/vsarm_firmware.bin 0x08000000",
            "options": {
                "cwd": "${workspaceRoot}"
            },
            "group": {
                "kind": "build",
                "isDefault": true
            },
            "problemMatcher": []
        }
    ]
}

#Launch: Debug: Open launch.json, Cortex Debug

{
    // Use IntelliSense to learn about possible attributes.
    // Hover to view descriptions of existing attributes.
    // For more information, visit: https://go.microsoft.com/fwlink/?linkid=830387
    "version": "0.2.0",
    "configurations": [
    {
        "type": "cortex-debug",
        "request": "launch",
        "servertype": "stutil",
        "cwd": "${workspaceRoot}",
        "executable": "./build/vsarm_firmware.elf",
        "name": "Debug (ST-Util)",
        "device": "STM32F303K8",
        "v1": false,
        "svdFile": "${workspaceRoot}/STM32F103xx.svd"
        }
    ]
}

