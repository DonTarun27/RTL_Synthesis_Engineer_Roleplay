# Introduction
Yosys Tool is part of the Tabby CAD Suite and the OSS CAD Suite! The easiest way to use yosys is to install the binary software suite, which contains all required dependencies and related tools.
1. Contact YosysHQ for a **Tabby CAD Suite** Evaluation License and download link  
OR go to https://github.com/YosysHQ/oss-cad-suite-build/releases to download the free **OSS CAD Suite**.
2. OSS CAD Suite is a binary software distribution for a number of open source software used in digital logic design. You will find tools for RTL synthesis, formal hardware verification, place & route, FPGA programming, and testing with support for HDLs like Verilog, Migen, and Amaranth.
3. Make sure to get a Tabby CAD Suite Evaluation License if you need features such as industry-grade SystemVerilog and VHDL parsers!
4. For more information about the difference between Tabby CAD Suite and the OSS CAD Suite, please visit https://www.yosyshq.com/tabby-cad-datasheet
5. Many Linux distributions also provide Yosys binaries, some more up to date than others. Check with your package manager!
# Installation
As I am using WSL (Windows Subsytem Linux) - Ubuntu 24.04.2 LTS for all the Open-Source Tools Installation, I checked the Yosys Tool Version in the apt package manager and found it to be v0.33 which is a very old version compared to the latest v0.56  
So, I have chosen to download and setup the free **OSS CAD Suite** by following the below steps:
1. Download an archive matching your OS from the releases page - https://github.com/YosysHQ/oss-cad-suite-build/releases by running the below command:
```
wget https://github.com/YosysHQ/oss-cad-suite-build/releases/download/2025-08-11/oss-cad-suite-linux-x64-20250811.tgz
```
2. Extract the archive to a location of your choice. I have extracted it to my user home directory (\~) by running the below commands:
```
cd ~
tar -xf oss-cad-suite-linux-x64-20250811.tgz
```
3. Remove the archive to free disk space by running the below command:
```
rm oss-cad-suite-linux-x64-20250811.tgz
```
4. Now to setup the **OSS CAD Suite** environment in our terminal, run the below command:
```
vi ~/.bashrc
```
And then insert the below line at the end of the file:
```
alias oss='source /home/$USER/oss-cad-suite/environment'
```
5. Log Out & Log Back In or run the below command in the current terminal:
```
source ~/.bashrc
```
Now, whenever you open a new terminal, you can run **oss** as command to setup the **OSS CAD Suite** environment and then run **Yosys Tool** in the terminal.

6. Check the Yosys Tool Version by running the below commands:
```
oss
```
To setup the **OSS CAD Suite** environment.
```
yosys --version
```
or
```
yosys -V
```
Prints **Yosys 0.56+30 (git sha1 8c71226d0, clang++ 18.1.8 -fPIC -O3)**.
