很久以前裝在hyperv裡面的系統太老了，新環境要用docker環境，碰了一堆釘子搞不定，還是決定裝新的vm，試了大概十幾個版本終於找到符合需要的組合，實測可用，紀錄一下

需求是：
系統不要太舊或太新
要能跑現在的docker //為了新的build env
要能samba,ssh,vncserver //要跟windows host溝通
要能ssh-keygen //太舊的系統gitlab一直無法認到
要能kscope //太習慣這個了沒它不行，它又依賴舊的KDE，還好q4os有套件，還不用自己build

q4os-4.13-x64.r1.iso

ongoing

過程中還發現docker並非萬能解，在裡面跑的elf實際還是需要外面的系統有搭配，比如這次遇到的vsyscall core dump，雖然重編elf就能避開，但我還是選擇改vm的grub cmdline，不去動docker image的東西。