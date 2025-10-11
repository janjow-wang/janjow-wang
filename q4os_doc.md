## 很多安裝畫面都出不來，原來是hyperv要用type2，可以安裝q4os 5.8了（debian 12的）
### 竟然自帶ffmpeg帶libh264,libh265，連SDL都有，都不用自己編

## 很久以前裝的vm系統太老了，新環境要用docker，另外用script抓docker image回來load，還是不能用，碰了一堆釘子搞不定，還是決定裝新的vm，試了大概十幾個版本，終於找到符合需要的組合，實測可用，紀錄一下

### 需求是：
- 系統不要太舊或太新
- 要能跑現在的docker //為了新的build env
- 要能samba,ssh,vncserver //要跟windows host溝通
- 要能ssh-keygen //太舊的系統gitlab一直無法認到
- 要能kscope //太習慣這個了沒它不行，它又依賴舊的KDE，還好q4os有套件，還不用自己build

### 步驟筆記:

q4os-4.13-x64-tde.r1.iso

sudo apt update
sudo apt install kscope-trinity

sudo apt install docker.io
sudo usermod -aG docker user
sudo reboot

sudo apt install vim

sudo apt install samba
sudo nano /etc/samba/smb.conf
edit home block
sudo systemctl restart smbd
sudo smbpasswd -a user

cp buildks, cscope.proj.basic -> ~/bin

sudo apt install ssh

ssh-keygen
cat .ssh/id_rsa.pub

sudo apt install tigervnc-standalone-server tigervnc-common
vncserver :1 -localhost no -geometry 1900x1000 -depth 16

sudo nano /etc/default/grub
add vsyscall=emulate in BOOT_IMAGE line
sudo update-grub
sudo reboot

nano .bashrc
alias ks='kscope CSCOPE.PROJ ../.$(basename "$PWD")_prj &'
alias vvv='vncserver :1 -localhost no -geometry 1900x970 -depth 16'
export PATH=~/bin:/usr/local/sbin:/usr/sbin:$PATH

### note:
- 新環境make一開始總是超級慢又吃超大量memory，原來是一開始會git diff，因為原來的kscope proj放在目錄中，會被拿去diff，所以修改了一下位置，把prj 搬到上一層，以適合目前的build env.
- 過程中還發現docker並非萬能，在裡面跑的elf實際還是需要外面的系統有搭配，比如這次遇到的vsyscall core dump，雖然重編elf就能避開，但我還是選擇改vm的grub cmdline，不去動docker image的東西.
