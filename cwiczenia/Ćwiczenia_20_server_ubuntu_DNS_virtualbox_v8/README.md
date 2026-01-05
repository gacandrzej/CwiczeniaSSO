Ćwiczenia 20 -- instalacja i konfiguracja serwera DNS (BIND)
Uruchomić: ubuntu server → ubuntu desktop
1)  Zaloguj się na konto administrator i dodaj swoje konto do grupy
    sudo:
> *sudo usermod nazwa_konta -G sudo*
2)  Odłącz stacje od internetu.
3)  Zaloguj się na swoje konto na minimum pięciu terminalach. (Alt+F2,
    Alt+F3, ...
na logi, na edycję pliku ,na komendy, , na restart usługi, na
dokumentację )
4)  Przed przystąpieniem do pracy trzeba odinstalować serwer dns i
    usunąć pliki:
![](media/image1.png)
5)  ![](media/image2.png)
    Zainstaluj serwer DNS:
6)  Sprawdź czy jest zainstalowana paczka w systemie: *sudo apt list
    \--installed \| grep bind*
> ![](media/image3.png)
7)  Ustaw kartę dolną **enp3s0** na adres 10.20.30.177 z pomocą netplanu
> ![](media/image4.png)
![](media/image5.png)
8)  Sprawdź poleceniem ping ze stacji komunikację z serwerem.
9)  Ustaw pracę usługi named na ipv4
> ![](media/image6.png)
10) W katalogu /etc/bind/ w pliku named.conf.local dodaj strefy
> ![](media/image7.png)
11) Dopisz do pliku konfiguracyjnego:
> ![](media/image8.png)
12) Utwórz plik strefy do przodu kopiując plik /etc/bind/db.empty lub
    db.local:
> ![](media/image9.png)
13) Utwórz plik strefy odwrotnej kopiując plik /etc/bind/db.127:
![](media/image10.png)
14) Zrestartuj usługę i sprawdź logi:
> ![](media/image11.png)
15) Sprawdź poprawność konfiguracji
> ![](media/image13.png)
16) Sprawdź status
> ![](media/image14.png)
17) Dodaj wpisy do /etc/hosts
![](media/image15.png)
18) Dodaj do /etc/systemd/resolved.conf,
![](media/image16.png)
19) ![](media/image17.png)
    a następnie zrestartuj usługę
20) Sprawdzenie ustawień:
![](media/image18.png)
21) Sprawdź działanie serwera narzędziem dig sala70.zsmeie.torun.pl
22) Sprawdź działanie serwera narzędziem host ze stacji ubuntu
> ![](media/image19.png)
23) Sprawdź działanie serwera narzędziem dig ze stacji ubuntu (np.:
    **dig -t txt nazwa_rekordu** )
> ![](media/image20.png)
24) Sprawdź działanie serwera narzędziem nslookup ze stacji windows
    (np.: **nslookup -type=txt nazwa_reko.**)
> ![](media/image21.png)
25) Dodaj alias na adres serwera o nazwie www lub ftp
> ![](media/image22.png)
26) Sprawdzenie na stacji windows
> ![](media/image23.png)
27) Sprawdzenie na stacji ubuntu ( np.: **dig -t txt nazwa_rekordu**)
> ![](media/image24.png)
28) Dodaj 2 rekord poczty z priorytetami 5 i 10 o nazwach poczta i mail
> ![](media/image25.png)
29) ![](media/image26.png)
    Sprawdzenie:
> ![](media/image27.png)
30) Wykonaj zapytania do strefy wstecznej:
> ![](media/image28.png)
31) Dodaj rekord TXT i przetestuj na stacji jego działanie.
32) ![](media/image29.png)
    Dodaj rekord AAAA i przetestuj na
    stacji jego działanie.
33) Dodaj rekord SPF i przetestuj na stacji jego działanie.
34) Stwórz środowisko chroot dla serwera DNS.
35) Przenieś pliki stref do środowiska chroot.
36) Uruchom serwer z opcją dla chroot.
37) Sprawdź logi i działanie serwera narzędziami: host, dig i nslookup.
38) ![](media/image30.png)
    Podsumowanie, strefa do przodu:
39) ![](media/image31.png)
    Podsumowanie strefa do tyłu:
40) Odinstalować serwer:
![](media/image1.png)
41) Usunąć pliki stref.
42) Na stacji windows i ubuntu przywrócić ustawienie kart na dhcp.
43) Zainstalować serwer:
![](media/image2.png)
44) KONIEC 😊
