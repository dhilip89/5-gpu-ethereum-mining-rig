# ETHEREUM MINING

### 6 GPU Ethereum Mining Rig Build Guide

![Image of 6 GPU RIG](https://github.com/fogonthedowns/ethereum-guides/blob/master/images/rig.png)

#### Power Supply 

 * [1000 Watt Power Supply](https://jet.com/product/CORSAIR-VALUE-SELECT-CP-9020084-NA-RM1000I-HIGH-PERFORMANCE-POWER/edec544f997f422eb943ce3b234cc68b) & 500 Watt Power Supply - You'll need two power supplies. Be very careful. Use electrical tape, do all work with the power supplies unplugged. Note I do not warrent this video, I'm not an electrician so hire a professional. [Video Instructions](https://youtu.be/xZiWciJLK3o)

#### Motherboard/CPU 

 * MSI Pro Z170A SLI Plus Motherboard |  Intel G3900 Dual Core CPU
￼
#### GPUs 

 * 6x Graphics Cards (GPUs) – Nvidia GTX 1070 – The efficient Nvidia GTX 1070 can produce 25Mh/s using only 150 watts of electricity.

#### RAM

 * RAM (System Memory) –  4 GB RAM – You don’t need a lot of system memory to mine ethereum effectively.

#### GPU cables

 * [USB Riser Cables](https://www.amazon.com/MintCell-6-Pack-Powered-Adapter-Extension/dp/B01GU94QSQ/ref=pd_lpo_vtph_147_bs_t_1?_encoding=UTF8&psc=1&refRID=D0HP0K39ZVGXD997G2YN) –  (6 pack) USB Riser Cables – Used to connect the 6 graphics cards to the motherboard and allow spacing between cards for heat dissipation. These are necessary when building a rig with this many GPU’s.

#### Hard Disk

 * 1x Hard Drive (SSD)  –  Solid State Drive  for installing operating system and your mining software.

#### Rig Case

 * 1x Custom Mining Case –  I’d recommend an Open Air 6 GPU Mining Case.I’ve built several of these 6 GPU rigs for family and friends using this particular mining case works quite well for airflow and ease of building.

#### On/Off Switch

 * [Power Button](https://www.amazon.com/gp/product/B01FM62DTC/ref=oh_aui_detailpage_o00_s00?ie=UTF8&psc=1)

#### Other stuff

 * Keyboard/Mouse/HDMI cable for montior
 * 8GB USB stick
 * [usb wifi adaptor ](https://www.amazon.com/gp/product/B00EQT0YK2/ref=oh_aui_detailpage_o05_s00?ie=UTF8&psc=1)


# Build Guide 

1. Un-package everything
2. Build / assemble Open Air 6 GPU Mining Case
3. Install processor and RAM on motherboard
4. Plug in all riser cables
5. Place motherboard in custom open air mining rig case and connect motherboard PSU connector (leaving PSU unplugged from the wall of course)
6. Plug in SATA hard drive (or optional Linux on USB stick)
7. Connect all GPUs to riser cables and fasten them to custom case. You might need to experiment for optimal spacing to keep the cards cool.
8. Plug in all power supply connections.
9. Connect mouse, monitor and keyboard and an internet connection (I use a USB WiFi adapter)
10. Check all connections once more
11. Fire it up! Install Ubuntu 17.04
12. Make sure fans are fully functional. Start the mining software, tweak settings for maximum hash rates and let it run!
Motherboard, Windows and Mining Software Configuration
1. Update the motherboard to the latest BIOS using a USB thumb drive. You can find the latest BIOS for the Z170 SLI Plus motherboard here.
2. Configure Motherboard BIOS with the following settings changes:
    * Settings > Advanced > PCI subsystem Setting: PEG 0 and PEG 1 set to Gen1
    * Above 4G Decoding (cryptocurrency mining) should be set to Enabled
    * Save and reboot
3. OS / DRIVERS / MINING Setup:
    1. Boot from USB install media
    2. Ubuntu 17.04

### install cuda

exit ubuntu gui:
`ctl` + `alt` + `f1`

stop ubuntu GUI:
```
sudo service lightdm stop
sudo init 3
```
Nvidia Cuda drivers [https://developer.nvidia.com/cuda-downloads]
```
sudo sh [NVIDIA .run file]
```
be sure to set PATH variables as noted by the output. Add to the `PATH` of `.bashrc`:
```
sudo vi ~/.bashrc
PATH="/some/new/path:$PATH"
```
save. exit. and source the environment variables: `source ~/.bashrc`

Next, enter `sudo init 5`. And restart your system with `sudo restart`

```
sudo apt-get purge nvidia*
sudo add-apt-repository ppa:graphics-drivers/ppa
sudo apt-get update
sudo apt-get install nvidia-367
```
### restart your system

```
nvidia-smi
+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID  Type  Process name                               Usage      |
|=============================================================================|
|    0      1111    G   /usr/lib/xorg/Xorg                             249MiB |
|    0      1832    G   compiz                                         164MiB |
+-----------------------------------------------------------------------------+
watch -n0 nvidia-smi
+-----------------------------------------------------------------------------+
| NVIDIA-SMI 375.82                 Driver Version: 375.82                    |
|-------------------------------+----------------------+----------------------+
| GPU  Name        Persistence-M| Bus-Id        Disp.A | Volatile Uncorr. ECC |
| Fan  Temp  Perf  Pwr:Usage/Cap|         Memory-Usage | GPU-Util  Compute M. |
|===============================+======================+======================|
|   0  GeForce GTX 1070    Off  | 0000:01:00.0      On |                  N/A 
+-------------------------------+----------------------+----------------------+

+-----------------------------------------------------------------------------+
| Processes:                                                       GPU Memory |
|  GPU       PID  Type  Process name                               Usage      |
|=============================================================================|
|    0      1111    G   /usr/lib/xorg/Xorg                             249MiB |
|    0      1832    G   compiz                                         159MiB |
+-----------------------------------------------------------------------------+


sudo apt-get install vim
```

Download [Ethminer](https://github.com/ethereum-mining/ethminer#build)
```
mkdir build; cd build
cmake .. -DETHASHCUDA=ON -DETHASHCL=OFF
cmake --build .
sudo make install
```

In my case the build is in cpp-thereum-master directory Run:

```
~/Downloads/cpp-ethereum-master/build/ethminer/ethminer -G -F http://eth-us2.dwarfpool.com/0x00c02245d47e1ee134b67c8a4e035c0a063fce2d/github_worker
```

Replacing your wallet id, and worker name with yours. But feel free to tip me in order to test results. 
