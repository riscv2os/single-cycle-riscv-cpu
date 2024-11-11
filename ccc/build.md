

```
(base) cccimac@cccimacdeiMac ccc % ./build.sh
riscv64-unknown-elf-gcc -c -march=rv32i -mabi=ilp32 main.S
riscv64-unknown-elf-gcc -c -march=rv32i -mabi=ilp32 setup.S
riscv64-unknown-elf-gcc main.o setup.o -static -nostdlib -nostartfiles -march=rv32i -mabi=ilp32 -Tlink.ld -lgcc -o main
riscv64-unknown-elf-objdump -xsd main > main.log
riscv64-unknown-elf-objcopy -O verilog main -i 4 -b 0 main0.hex
riscv64-unknown-elf-objcopy -O verilog main -i 4 -b 1 main1.hex
riscv64-unknown-elf-objcopy -O verilog main -i 4 -b 2 main2.hex
riscv64-unknown-elf-objcopy -O verilog main -i 4 -b 3 main3.hex
iverilog -o tb.vvp top.v top_tb.v
vvp tb.vvp
VCD info: dumpfile tb.vcd opened for output.
WARNING: top_tb.v:55: invalid file descriptor (0x0) given to $feof.

Done





        ****************************               
        **                        **       |__||  
        **  Congratulations !!    **      / O.O  | 
        **                        **    /_____   | 
        **  Simulation PASS!!     **   /^ ^ ^ \  |
        **                        **  |^ ^ ^ ^ |w| 
        ****************************   \m___m__|_|


top_tb.v:76: $finish called at 15135000 (10ps)
```
