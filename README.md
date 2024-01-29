# STM32F103C8T6 (Blue Pill) Startup and Linker Script Example

This repository provides an example of a startup code and linker script for the STM32F103C8T6 (Blue Pill) microcontroller. The example includes a basic application (`app.c`) with a main loop, a linker script (`STM32F103C8TX_FLASH.ld`), and a startup code (`startup_stm32f103c8tx.c`).

## Project Structure

- `app.c`: Simple application demonstrating the use of startup code and linker script.
- `STM32F103C8TX_FLASH.ld`: Linker script defining memory layout and sections.
- `startup_stm32f103c8tx.c`: Startup code containing vector table and initialization functions.
- `app.map`: Map file generated during the linking process.
- `startup_stm32f103c8tx.elf`: ELF executable file.
- `startup_stm32f103c8tx.bin`: Binary file for flashing.
- `startup_stm32f103c8tx.hex`: Intel Hex file for flashing.

## Compilation Process

To compile and build the project, follow these steps:

1. **Compile App and Startup Code:**

    arm-none-eabi-gcc -c -mcpu=cortex-m3 -mthumb app.c -o app.o
    arm-none-eabi-gcc -c -mcpu=cortex-m3 -mthumb startup_stm32f103c8tx.c -o startup_stm32f103c8tx.o

2. **Link Object Files:**

    arm-none-eabi-ld -Map app.map -T LinkerScript.ld startup_stm32f103c8tx.o app.o -o startup_stm32f103c8tx.elf

3. **Generate Binary File:**

    arm-none-eabi-objcopy -O binary startup_stm32f103c8tx.elf startup_stm32f103c8tx.bin

4. **Generate Hex File:**

    arm-none-eabi-objcopy -O ihex startup_stm32f103c8tx.elf startup_stm32f103c8tx.hex


## Flashing and Debugging

Use your preferred method to flash the generated binary (`startup_stm32f103c8tx.bin`) to the STM32F103C8T6 microcontroller. You can use tools like ST-Link Utility or OpenOCD for this purpose.

## Memory Layout

The linker script (`LinkerScript.ld`) defines the memory layout for the microcontroller:

- FLASH: 64 KB (Starting at 0x08000000)
- RAM: 20 KB (Starting at 0x20000000)

## Checking Addresses

After flashing the firmware, you can use ST-Link Utility or similar tools to verify that the vector table and other sections are correctly located in the Flash memory.

"# LinkerScript-File-and-StartUpCode-for-Stm32f103c8T6-BluePill-" 
