# The One-Stop Solution to Low CPU Frequency

*ThrottleStop, the Linux way*

## Why?

When CPU be limited and runs at a low frequency, e.g. 0.4 or 0.8 GHz, it takes tanks of time to fix... ...if your OS is not Windows and can not run [ThrottleStop](https://www.techpowerup.com/download/techpowerup-throttlestop/).
So I list all the solutions to save your time.

## 1. Some Hardware Wrong?
  -[x] Power Supply 
  -[x] Battery
  -[x] Fan
  -[x] Wind Tube
  -[x] etc

## 2. Remove Static Electricity

  -[x] Unplug ALL Supplies
  -[x] Then Hold Down PowerKey for 60 sec

## 3. Reset and Update BIOS
  -[x] Click PowerKey and Hold Down F2 to Enter BIOS to Reset it
  -[x] Go to OEM(Acer Asus Dell...) Official Site to Update BIOS

## 4. Set CPU Frequency

```bash
sudo update -y
sudo apt install cpupower-gui -y
cpupower-gui  
# Max Frequency == Base Frequency maybe Better
```

## 5. Set Successfully?

```bash
watch -n1 "grep \"^[c]pu MHz\" /proc/cpuinfo"
```
## 6. Secure Boot Disable?

```bash
sudo apt install mokutil -y
sudo mokutil --sb-state
```
## 6.5. Disable Secure Boot in BIOS

## 7. Reset CPU via MSR

```bash
sudo apt install msr-tools -y
sudo modprobe msr
sudo rdmsr -a -d 0x1FC  # 2359389
sudo wrmsr 0x1FC 2359388
```

## 8. Everything Fine?

```bash
watch -n1 "grep \"^[c]pu MHz\" /proc/cpuinfo"
```

## Thanks To:
[kitsunyan](https://github.com/kitsunyan/intel-undervolt) | 
[DivyanshuVerma](https://github.com/DivyanshuVerma/throttlestop-linux) | 
[Debian Wiki](https://wiki.debian.org/CpuFrequencyScaling)
