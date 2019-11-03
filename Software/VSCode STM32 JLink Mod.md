## keybindings.json

```
[
    {
        "key": "f5",
        "command": "workbench.action.tasks.runTask",
        "args": "Make Firmware"
    },
    {
        "key": "f6",
        "command": "workbench.action.tasks.runTask",
        "args": "Load Firmware"
    }
]
```

## tasks.json 

```
{
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
            // "command": "st-flash write ./build/vsarm_firmware.bin 0x08000000", //stlink
            "command": "JLink -device STM32F103C8 -if SWD -speed 4000 -CommanderScript ./.vscode/JLinkCommand.jlink", // jlink
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
```

## launch.json 

```
{
    "version": "0.2.0",
    "configurations": [
    {
		//stlink
//         "type": "cortex-debug",
//         "request": "launch",
//         "servertype": "stutil",
//         "cwd": "${workspaceRoot}",
//         "executable": "./build/vsarm_firmware.elf",
//         "name": "Debug (ST-Util)",
//         "device": "STM32F103C8",
//         "v1": false,
//         "svdFile": "${workspaceRoot}/STM32F103xx.svd"

		//jlink
        "type": "cortex-debug",
        "request": "launch",
        "servertype": "jlink",
        "cwd": "${workspaceRoot}",
        "executable": "./build/vsarm_firmware.elf",
        "name": "Debug (J-Link)",
        "device": "STM32F103C8",
        "interface": "swd",
        "ipAddress": null,
        "serialNumber": null,
        "v1": false,
        }
    ]
}
```

## make a new file in .vscode folder: JLinkCommand.jlink
## JLinkCommand.jlink

```
h
loadbin ./build/vsarm_firmware.bin, 0x08000000
r
q
```

## c_cpp_properties.json 

```
includePath:
"C:\\Program Files (x86)\\SEGGER\\JLink",
```

## settings.json

```
if debug cant find JLinkGDBServerCL
"cortex-debug.JLinkGDBServerPath": "C:/Program Files (x86)/SEGGER/JLink/JLinkGDBServerCL",
```
