Captures of JTAG signals while connecting/programming bl602 for use with sigrok/pulseview
All captures done at 24Mhz sample rate using fx2 based logic analyzer

JTAG signals map to the following channels
```
TDI = D1
TDO = D5
TCK = D2
TMS = D3
```

#### Using segger commander(jlinkexe) to connect/halt/upload to ram using the following commands
```
connect
h
loadbin nevergonna.bin 0x42030000
```
- jlink_connect_10khz.sr
- jlink_halt_10khz.sr
- jlink_upload_10khz.sr

#### Using ozone to upload the elf file "bl602-rust-guide" and then halt
- jlink_upload_bl602-rust-guide.sr

#### Using probe-rs/examples/ram_download using the command line, with the 2 different outcomes seen:
```
RUST_LOG=trace ./ram_download --chip riscv --address 0x42030000 --speed 10 --size 1 --protocol jtag
```
-
  - ram_download_target_10khz_w_trace.sr
  - ram_download_target_10khz_w_trace_console.log

- 
  - ram_download_target_10khz_w_trace2.sr
  - ram_download_target_10khz_w_trace2_console.log
  
#### Other files:
  ```pulseview.png``` showing how to configure JTAG protocol decoder after loading .sr file
  ```nevergonna.bin``` text file to show uploading to RAM function
  ```bl602-rust_guide``` blinky/uart example program from https://github.com/sipeed/bl602-rust-guide
