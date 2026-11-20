# Introduction
**Yosys Open-Source Tool** is part of the Tabby CAD Suite and the OSS CAD Suite! The easiest way to use yosys is to install the binary software suite, which contains all required dependencies and related tools.
1. Contact **YosysHQ** for a **Tabby CAD Suite Evaluation License** and download link  
OR go to https://github.com/YosysHQ/oss-cad-suite-build/releases to download the free **OSS CAD Suite**.
2. **OSS CAD Suite** is a binary software distribution for a number of open source software used in digital logic design. You will find tools for RTL synthesis, formal hardware verification, place & route, FPGA programming, and testing with support for HDLs like Verilog, Migen, and Amaranth.
3. Make sure to get a **Tabby CAD Suite Evaluation License** if you need features such as industry-grade SystemVerilog and VHDL parsers!
4. For more information about the difference between the Tabby CAD Suite and the OSS CAD Suite, please visit https://www.yosyshq.com/tabby-cad-datasheet
5. Many Linux distributions also provide Yosys binaries, some more up to date than others. Check with your package manager!
# Installation
As we are using **WSL (Windows Subsytem Linux) - Ubuntu 26.04.1 LTS** for all the Open-Source EDA Tools Installation, checking the **Yosys Tool** package in Ubuntu's apt repository (apt show yosys) shows v0.52+2.

Because Ubuntu freezes apt package versions at release time, the repository version trails behind upstream development (currently v0.71+59). Instead of installing an outdated version via apt, we use the OSS CAD Suite binary bundle—which provides the latest Yosys alongside matching, up-to-date versions of Nextpnr, Verilator, Icarus Verilog, GTKWave, and openFPGALoader in one self-contained directory.

So, follow the below steps to download and setup the free **OSS CAD Suite**:
1. Download the latest linux-x64 archive from the YosysHQ OSS CAD Suite Releases page - https://github.com/YosysHQ/oss-cad-suite-build/releases (look for oss-cad-suite-linux-x64-<YYYYMMDD>.tgz) by running the below command:
```
cd ~
wget https://github.com/YosysHQ/oss-cad-suite-build/releases/download/2026-11-20/oss-cad-suite-linux-x64-20261120.tgz
```
2. Extract the archive and move it to /opt. I have extracted it to my **user home directory (\~)** by running the below commands:
```
tar -xf oss-cad-suite-linux-x64-*.tgz
sudo mv oss-cad-suite /opt/
```
3. Remove the archive to free disk space by running the below command:
```
rm oss-cad-suite-linux-x64-*.tgz
```
4. Now to set up the OSS CAD Suite environment in our terminal and apply it immediately, run the below commands:
```
echo 'export PATH="/opt/oss-cad-suite/bin:$PATH"' >> ~/.bashrc
echo "alias oss='source /opt/oss-cad-suite/environment'" >> ~/.bashrc
source ~/.bashrc
```
Now, in your current terminal and any new terminal you open:
• Core CLI tools (such as yosys, iverilog, verilator, nextpnr, and gtkwave) are available immediately without any extra setup.
• Python-based HDL tools and full environment variables (such as Amaranth, LiteX, or yosys-config) can be activated on demand by running **oss** as command in your terminal.

5. Check the Yosys tool version directly by running the below command:
```
yosys --version
```
or
```
yosys -V
```
Prints **Yosys 0.71+59 (git sha1 d9358f38c, Release, Clang /usr/bin/clang++ 21.1.8)**.

6. **(Optional)** If you want to verify the full environment alias for Python HDL tools, run the below commands:
```
oss
which python3
```
This activates the **OSS CAD Suite** environment and points python3 to /opt/oss-cad-suite/py3bin/python3.
# Tool Experiment Setup
The **Yosys Tool Github Repository** has some Verilog design files and liberty files in **examples, techlibs & tests** directories to experiment with the tool. So, you can follow the below steps to clone the repository and then using git sparse-checkout to limit the directories & files downloaded to only the specified ones:
1. Initialize a sparse checkout:
```
git clone --no-checkout https://github.com/YosysHQ/yosys.git
cd yosys
git sparse-checkout init --no-cone
```
2. Specify the directories & files you want to access:
```
git sparse-checkout set examples techlibs /tests /README.md
```
Here **tests** directory is explicitly described as **/tests** specifying its directory path since there is a sub-directrory named **tests** present inside both **docs & passes** directories. And **README.md** file is explicitly described as **/README.md** specifying its file path since we want a single file.

3. Checkout the specified directories & files:
```
git checkout main
```
