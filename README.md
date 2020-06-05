# STM32F4xx Template Repository

## Prerequisites

### Hardware

* Raspberry PI 2B
* Target Board (STM32F4xx based)

### Software

* [GNU Arm Embedded Toolchain](https://developer.arm.com/tools-and-software/open-source-software/developer-tools/gnu-toolchain/gnu-rm/downloads)
* [STM32CubeProgrammer](https://www.st.com/en/development-tools/stm32cubeprog.html)
* [Visual Studio Code](https://code.visualstudio.com/)
* [C/C++ for Visual Studio Code](https://github.com/microsoft/vscode-cpptools)
* [Cortex Debug](https://github.com/Marus/cortex-debug)

### Windows

Windows users should install Cygwin and use `make` tool for project build

## Setup

1. Check if gnu arm embedded toolchain's bin folder is added to the `PATH`
2. Optionally run `git submodule update --init --recursive` to download OpenOCD configuration.
3. Wiring diagram can be found [here](https://github.com/piotrserafin/openocd_configs)

### Environment

![Environment Setup](/Doc/ocd_setup.png)

### Build & Run
Assuming BlackPill board and SWD is used.
#### On the RPi (via SSH)
```bash
$ sudo openocd -f rpi2_stm32blackpill_swd.cfg -c "bindto 0.0.0.0"
```

#### On the Host PC
```bash
$ make
$ arm-none-eabi-gdb -ex="target remote 192.168.0.2:3333" build\hello.elf
```
In GDB
```bash
> load #loads the binary
> b main #sets breakpoint to main
> c #continues program execution
```
Alternatively hit `F5` in Visual Studio Code to start debugging session.

## Resources

* https://iosoft.blog/2019/01/28/raspberry-pi-openocd/
* https://www.youtube.com/channel/UCTRqh7AJx8zckPWdhVA1YIA
* https://www.st.com/en/microcontrollers-microprocessors/stm32f411ce.html
