# KEST2LG05DU_Lokaverkefni
```
su -
nano /etc/network/interfaces
```
![interfaces](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/interfaces.PNG?raw=true)

```
nano /etc/hosts
```
![hosts](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/hosts.PNG?raw=true)

```
nano /etc/hostname
```
![hostname](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/hostname.PNG?raw=true)

```
adduser --force-badname AleRag
```
![adduser](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/adduser.PNG?raw=true)

```
ls -l /home
```
![homedir](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/homedir.PNG?raw=true)

```
sudo groupadd IT
sudo groupadd Management
sudo groupadd Accounting
sudo groupadd Manufacturing
```
![groupadd](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/groupadd.PNG?raw=true)

```
usermod -a -G IT AleRag
usermod -a -G IT AndHau
usermod -a -G Management GudSte
usermod -a -G Management HalJon
usermod -a -G Management HarHja
usermod -a -G Accounting HraAra
usermod -a -G Accounting IngGud
usermod -a -G Manufacturing IsaLei
usermod -a -G Manufacturing JohKri
usermod -a -G Manufacturing JohHaf
usermod -a -G Manufacturing KriSva
usermod -a -G Manufacturing LarGun
usermod -a -G Manufacturing LinMag
usermod -a -G Manufacturing RudBjo
usermod -a -G Manufacturing SigSte
usermod -a -G Manufacturing SigJen
```
![usermod](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/usermod.PNG?raw=true)

```
sudo apt install samba
nano /etc/samba/smb.conf
```
![samba](https://github.com/Douchebag/KEST2LG05DU_Lokaverkefni/blob/master/myndir/smbcnf.PNG?raw=true)
