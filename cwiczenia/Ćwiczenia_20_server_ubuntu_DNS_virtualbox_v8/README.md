# Ćwiczenia 20 -- instalacja i konfiguracja serwera DNS (BIND)

💡 Uruchomić: ubuntu server → ubuntu desktop

1)  Zaloguj się na konto administrator i dodaj swoje konto do grupy
    sudo:
```bash
sudo usermod nazwa_konta -G sudo
```
2)  Odłącz stacje od internetu.
3)  Zaloguj się na swoje konto na minimum pięciu terminalach. (<kbd>Alt</kbd>+<kbd>F2</kbd>,
    <kbd>Alt</kbd>+<kbd>F3</kbd>, ...
na logi, na edycję pliku ,na komendy, , na restart usługi, na
dokumentację )
4)  Przed przystąpieniem do pracy trzeba odinstalować serwer dns i
    usunąć pliki:
```bash
sudo apt remove bind9 bind9utils bind9-doc --purge -y
```
![](media/image1.png)

5)  Zainstaluj serwer DNS:
```bash
sudo apt install bind9 bind9utils bind9-doc -y
```

   ![](media/image2.png)

6)  Sprawdź czy jest zainstalowana paczka w systemie: 
```bash 
sudo apt list --installed | grep bind
```
 ![](media/image3.png)

7)  Ustaw kartę dolną **enp3s0** na adres 10.20.30.177 z pomocą netplanu
    <p align="center"> <img src="media/image4.png" width="45%" /> </p>
```bash
sudo netplan apply
```
<p align="center"> <img src="media/image5.png" width="45%" /> </p>

```bash
ip -c a
```
8)  Sprawdź poleceniem ping ze stacji komunikację z serwerem.
```bash
ping 10.20.30.177
```
9)  Ustaw pracę usługi named na ipv4

 ![](media/image6.png)

10) W katalogu /etc/bind/ w pliku named.conf.local dodaj strefy
 ![](media/image7.png)
11) Dopisz do pliku konfiguracyjnego, recursion zostaw zakomentowane:

 ![](media/image8.png)

12) Utwórz plik strefy do przodu kopiując plik /etc/bind/db.local:
```bash
cp /etc/bind/db.local /etc/bind/sala70.zsmeie.torun.pl
```

 ![](media/image9.png)

13) Utwórz plik strefy odwrotnej kopiując plik /etc/bind/db.127:
```bash
cp /etc/bind/db.127 /etc/bind/10.20.30
```
![](media/image10.png)

14) Zrestartuj usługę i sprawdź logi:
 ```bash
 sudo systemctl restart bind9
 ````
 lub
 ```bash
 sudo systemctl restart named
 ```
 ```bash
 sudo journalctl -f
 ```

 ![](media/image11.png)

15) Sprawdź poprawność konfiguracji
```bash
cd /etc/bind
sudo named-checkconf
sudo named-checkzone sala70.zsmeie.torun.pl sala70.zsmeie.torun.pl
sudo named-checkzone 10.20.30 10.20.30
```
 ![](media/image13.png)

16) Sprawdź status usługi z pomocą rndc:
```bash
sudo rndc status
```
 ![](media/image14.png)

17) Można wczytać ustawienia z plików
 ```bash
 sudo rndc reload
```
18) Dodaj wpisy do **/etc/hosts**

![](media/image15.png)

18) Dodaj do **/etc/systemd/resolved.conf**

![](media/image16.png)

19) a następnie zrestartuj usługę

![](media/image17.png)
    
20) Sprawdzenie ustawień:

![](media/image18.png)
21) Sprawdź działanie serwera narzędziem dig:
```bash 
dig sala70.zsmeie.torun.pl any
```
22) Sprawdź działanie serwera narzędziem host ze stacji ubuntu

 ![](media/image19.png)

23) Sprawdź działanie serwera narzędziem dig ze stacji ubuntu, np.:
    ```bash 
    dig -t typ_rekordu nazwa_rekordu 
    ``` 
 ![](media/image20.png)

24) Sprawdź działanie serwera narzędziem nslookup ze stacji windows, np.: 
```bash
nslookup -type=typ_rekordu nazwa_rekordu
```
 ![](media/image21.png)

25) Dodaj alias na adres serwera o nazwie www lub ftp

 ![](media/image22.png)

26) Sprawdzenie na stacji windows

 ![](media/image23.png)

27) Sprawdzenie na stacji ubuntu
```bash 
dig -t cname ftp.sala70.zsmeie.torun.pl
```
 ![](media/image24.png)

28) Dodaj 2 rekord poczty z priorytetami 5 i 10 o nazwach poczta i mail

 ![](media/image25.png)

29) Sprawdzenie:
 ```bash
 sudo dig -t MX sala70.zsmeie.torun.pl
 ```
```bash
sudo dig sala70.zsmeie.torun.pl mx +short
```
  ![](media/image26.png)
    
 ![](media/image27.png)

30) Wykonaj zapytania do strefy wstecznej z opcją -x:
```bash
 dig -x 10.20.30.181
```
![](media/image28.png)

31) Dodaj rekord TXT i przetestuj na stacji jego działanie.

![](media/image29.png)
    
32) Dodaj rekord AAAA i przetestuj na stacji jego działanie.
```text
pc2.sala70.zsmeie.torun.pl IN AAAA fe80::9246:2275:658d:b53d
```
```bash
dig -t AAAA pc2.sala70.zsmeie.torun.pl 
```
33) Dodaj rekord SPF i przetestuj na stacji jego działanie, np.:
```text
spf.sala70.zsmeie.torun.pl IN TXT "v=spf1 ipv4:10.20.30.177 mx -all"
```
```bash
dig -t txt spf.sala70.zsmeie.torun.pl 
```
34) Dodaj rekord SRV i przetestuj na stacji jego działanie, np.:
```text
_ftp._tcp.sala70.zsmeie.torun.pl IN SRV 10 5 21 ftp-server.sala70.zsmeie.torun.pl
```
```bash
dig _ftp._tcp.sala70.zsmeie.torun.pl 
```
35) Stwórz środowisko chroot dla serwera DNS.
35) Przenieś pliki stref do środowiska chroot.
36) Uruchom serwer z opcją dla chroot.
37) Sprawdź logi i działanie serwera narzędziami: `host`, `dig` i `nslookup`.
38) Podsumowanie, strefa do przodu:

![](media/image30.png)
    
39) Podsumowanie strefa do tyłu:

![](media/image31.png)
    
40) Odinstalować serwer:
```bash
sudo apt remove bind9 bind9utils bind9-doc --purge -y
```
![](media/image1.png)
41) Usunąć pliki stref.
42) Na stacji windows i ubuntu przywrócić ustawienie kart na dhcp.
43) Zainstalować serwer:
```bash
sudo apt install bind9 bind9utils bind9-doc -y
```
![](media/image2.png)
44) KONIEC 😊
