# Ćwiczenia 18 - serwer DHCP + DHCPv6

💡 Założenia: 
- praca w parach. 
- Konfiguracja klient -- serwer. 
- Ubuntu server + stacje: windows i ubuntu desktop

1)  Zaloguj się na konto administrator i dodaj swoje konto do grupy
    sudo:
```bash
sudo usermod nazwa_konta -G sudo
```
2)  Na stacji windows od internetu.
3)  Zaloguj się na swoje konto na minimum 6 terminalach:  

    <kbd>Alt</kbd>+<kbd>F1</kbd>, na komendy lub edycję pliku 
    <kbd>Alt</kbd>+<kbd>F2</kbd>, na komendy   
    <kbd>Alt</kbd>+<kbd>F3</kbd>, na edycję pliku   
    <kbd>Alt</kbd>+<kbd>F4</kbd>, na dokumentację  
    <kbd>Alt</kbd>+<kbd>F5</kbd>, na restart usługi  
    <kbd>Alt</kbd>+<kbd>F6</kbd>, na logi     

4)  Przed przystąpieniem do pracy trzeba odinstalować serwer dhcp:
```bash
sudo apt *remove isc-dhcp-server --purge -y*
```
5)  Zainstaluj serwer DHCP. 
```bash
sudo apt install isc-dhcp-server
```
6)  Sprawdź czy jest zainstalowana paczka w systemie: 
```bash
sudo apt list --installed | grep dhcp
```
![](media/image2.png)

7)  Skopiuj plik _**/etc/dhcp/dhcpd.conf**_ do swojego katalogu domowego
    __/home/twoje_konto/__
8)  Skonfiguruj plik __*/etc/dhcp/dhcpd.conf*__ . Przykładowy plik znajduje
    się w:

![](media/image3.png)

_/usr/share/doc/isc-dhcp-server/examples/dhcpd.conf.example_
otwórz go na 4 terminalu)

9)  Otwórz plik dhcpd.conf w vi lub nano lub mcedit, np.:
```bash
    sudo mcedit /etc/dhcp/dhcpd.conf
```
10) Skonfiguruj serwer tak, aby:

*  był serwerem podrzędny
*  automatyczne aktualizacje ddns ustaw na none
*  poziom logów ustaw na 7
*  określ domenę na „klasaXY.example.org"
*  ustaw DNSy: 8.8.8.8, 8.8.4.4
*  czas dzierżawy 1 minuta, maksymalny czas 3 minuty
*  pracował na podsieci:
   - złożonej z 8 adresów IP, którą wyznaczysz z sieci 172.21.194.128/25.  
     Klient powinien uzyskać adres ip z końcówką 179 lub 181.

---

 ![](media/image4.png)

11) Ustaw kartę sieciową dolną **( w sali 70: eno1 lub enp3s0** ) tak,
    aby serwer DHCP mógł na niej pracować, użyj komendy ip, np.:

![](media/image5.png)

12) Podaj na jakim interfejsie pracuje usługa DHCP w pliku
    __*/etc/default/isc-dhcp-server*__:

![](media/image6.png)

13) Zrestartuj usługę dhcp poleceniem:
```bash
sudo systemctl restart isc-dhcp-server
```
14) W logach nie może być błędów, szukamy wpisu:

![](media/image7.png)

15) Jeśli wystąpią błędy podczas uruchamiania to popraw plik
    __*/etc/dhcp/dhcpd.conf*__, i zrestartuj usługę.

16) Sprawdź czy istnieje proces dla serwera DHCP poleceniem: 
```bash
    sudo ps aux | grep isc-dhcp-server
```

![](media/image8.png)

oraz
```bash
sudo htop -> F3 wpisać dhcp i enter, wyjście q
```

![](media/image9.png)

17) Sprawdź zawartość logów poleceniem na 6 terminalu:
```bash
    sudo journalctl -f (preferowana metoda)
```
lub 
```bash
sudo journalctl -u isc-dhcp-server --since today (klawisz Page Down)
```

18) Na kliencie windows pobierz ustawienia na dolną kartę z serwera
    dhcp.

19) Na stacji windows spradź ustawienia:

    *route print,*  
    *ipconfig /all*

![](media/image10.png)

![](media/image11.png)

*oraz graficznie*

![](media/image12.png)

20) Sprawdź zawartość logów na serwerze:

![](media/image13.png)

21) Wykonaj w sekcji host rezerwację dla stacji windows.  
Dodaj DNS: `8.8.8.8` oraz `1.1.1.1` w sekcji host,   
a **domyślny** czas dzierżawy ustaw na 2 minuty,  
**maksymalny** czas dzierżawy ustaw na 6 minuty,  

![](media/image14.png)

22) Pobierz nowe ustawienia na stacji, a następnie sprawdź trasę na windows

![](media/image15.png)

23) Zmień kolejność dnsów. Pobierz nowe ustawienia na stacji.

24) Sprawdzenie trasy ze stacji windows i linux.

25) Na kliencie ubuntu desktop wydaj komendę: 
```bash
ip -c a
```
, jeśli brakuje nowych ustawień wydaj komendę:
```bash
sudo dhclient 
```
w celu ich pobrania.

26) Na kliencie ubuntu desktop wydaj komendy: 
```bash   
    ip a
    ip r 
    nmcli
    route
    resolvectl
```

  Efekt użycia polecenia nmcli:

![](media/image16.png)

27) Sprawdzenie dnsów:
```bash
systemd-resolve --status | grep 'DNS Servers' -A2
```

lub 
```bash
sudo resolvectl 
```
i 
```bash
 cat /etc/resolv.conf
```

28) Wykonaj w sekcji host rezerwację dla stacji ubuntu.  
    Dodaj DNSy: `8.8.8.8`, `1.1.1.1`, `1.0.2.1` w sekcji host, 
    a **domyślny** czas dzierżawy ustaw na 2 minuty,
    **maksymalny** czas dzierżawy ustaw na 8 minut.

29) Pobierz nowe ustawienia na stacji.

30) Zmień kolejność dnsów. Pobierz nowe ustawienia na stacji.

31) Sprawdź czas dzierżawy: 
```bash
 sudo cat /var/log/syslog | grep dhcp
```

![](media/image17.png)

lub

```bash
sudo nmcli -f dhcp4 device show 
```
 poszukać frazy: _dhcp_lease_time_ wyrażone w sekundach:

![img.png](media/image31_1.png)

32) Sprawdzenie trasy ze stacji ubuntu:

```bash
 mtr wp.pl
```

![img.png](media/image22_1.png)

---

33) Włącz masquerade w celu przekazania internetu na stację:

_*/etc/sysctl.conf*_ ustaw, odkomentuj:
`net.ipv4.ip_forward=1`  
`net.ipv6.conf.default.forwarding=1` (dla wersji 6 , opcjonalnie)  

```bash
sudo sysctl -p 
cat /proc/sys/net/ipv4/ip_forward
```
```bash
sudo iptables -t nat -A POSTROUTING -s 172.21.194.176/29 -j MASQUERADE
```

Powyższe polecenia powinny wystarczyć!!! Jeżeli nie użyj dla iptables
poniższego:
![](media/image19.png)
W powyższym:  
`enp0s3` to karta górna z dostępem do internetu,  
`enp0s8` to karta dolna dla sieci lokalnej

34) Uruchom przeglądarkę na stacji roboczej w celu sprawdzenia dostępu
    do internetu.
35) Sprawdź listę dzierżaw na serwerze:

![](media/image20.png)

---

36) Zadanie 2: Skonfiguruj serwer tak, aby:

*  był serwerem podrzędny
*  automatyczne aktualizacje ddns ustaw na none
*  poziom logów ustaw na 5
*  określ domenę na „klasaXY.example.net"
*  ustaw DNSy: 1.1.1.1, 158.75.22.164, 8.8.4.4
*  czas dzierżawy 1 minuta, maksymalny czas 10 minut
*  pracował na dwóch podsieciach:
   - złożonej z 32 adresów IP, którą wyznaczysz z sieci 10.20.30.192/26.
     Klient powinien uzyskać adres ip z końcówką 230 lub 238.
   - złożonej z 16 adresów IP, którą wyznaczysz z sieci 192.168.70.64/27.
     Klient powinien uzyskać adres ip z końcówką 100 lub 101.
   
37) Na stacji roboczej sprawdź pobrane ustawienia.

---

38) Skonfiguruj serwer do pracy w ipv6
39) Skopiowanie skryptu:
![](media/image21.png)
40) Skopiowanie pliku:
![](media/image22.png)
41) Konfiguracja /etc/default/isc-dhcp-server6:
![](media/image23.png)
42) Plik konfiguracyjny
![](media/image24.png)
43) Ustawienie karty:
![](media/image25.png)
44) Uruchomienie
![](media/image26.png)
45) Sprawdzenie procesów:
![](media/image27.png)
46) Log:
![](media/image28.png)
47) Ustawienia pobrane na stacji windows:
![](media/image29.png)
48) Ustawienia pobrane na stacji ubuntu:
![](media/image30.png)
49) Graficznie:
![](media/image31.png)
50) Log dla stacji ubuntu z serwera:
![](media/image32.png)
51) Sprawdzenie dzierżaw:
![](media/image33.png)
52) Dzierżawy dla wersji 4:
![](media/image34.png)
53) Koniec
