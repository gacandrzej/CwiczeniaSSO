Ćwiczenia 13 -Instalacja i konfiguracja serwera SAMBA
Założenia: praca w parach. Konfiguracja klient -- serwer. Ubuntu
server + stacje:
> windows i ubuntu desktop
Zachowaj na koniec zajęć plik konfiguracyjny smb.conf w swoim katalogu
domowym!!!
1)  Zaloguj się na konto administrator i dodaj swoje konto do grupy
    sudo:
> *sudo usermod nazwa_konta -G sudo*
2)  Na stacji windows otwórz stronę samba.org z dokumentacją.
3)  Zaloguj się na swoje konto na minimum pięciu terminalach. (Alt+F2,
    Alt+F3, ...
na logi, na edycję pliku ,na komendy, , na restart usługi, na
dokumentację )
4)  Sprawdź zawartość logów poleceniem na 1 terminalu: *sudo journalctl
    -f (preferowana metoda)*
*lub sudo journalctl -u smbd \--since today (klawisz Page Down)*
5)  Sprawdzić połączenie z internetem, ewentualnie pobrać ustawienia z
    serwera dhcp na górną kartę enp4s0
poleceniem: sudo dhclient enp4s0
6)  Przed przystąpieniem do pracy trzeba odinstalować serwer samby:
sudo apt *remove samba-common \--purge -y*
![](media/image1.png)
7)  Zainstaluj serwer samba: *sudo apt install samba samba-client -y*
![](media/image2.png)
8)  Sprawdź czy jest zainstalowana paczka w systemie: *sudo apt list
    \--installed \| grep samba*
![](media/image3.png)
9)  Po instalacji założyć w swoim katalogu domowym katalog samba z
    podkatalogami:
![](media/image4.png)
10) Skopiuj plik /etc/samba/smb.conf na nazwę
    /etc/samba/smb.conf.twoje_imie oraz drugą kopię do swojego katalogu
    domowego /home/twoje_konto/samba/backup ( cp -p)
![](media/image5.png)
11) Otwórz plik smb.conf w vi lub nano lub mcedit ( przykładowe
    polecenie: *sudo vi /etc/samba/smb.conf* )
12) Edytuj plik /etc/samba/smb.conf zgodnie z wykładem:
<!-- -->
a)  podaj nazwę serwera jako swoje imię
b)  ustaw plik logów i poziom logów na 6
c)  ustaw pracę samby na dolnej karcie sieciowej oraz lo
d)  itd.
<!-- -->
13) Dodatkowe przykładowe plik z których możesz skorzystać znajduje się
    w:
![](media/image6.png)
14) Ustaw kartę sieciową dolną **( w sali 70: eno1 lub enp3s0** ), górna
    to enp4s0 tak, aby serwer SAMBA mógł na niej pracować, użyj komendy
    ip, np.:
sudo ip addr add 10.20.30.177/29 dev enp0s8
sudo ip link set enp0s8 up
ip a
Lub skorzystaj z netplan: ( UWAGA: poniższa konfiguracja dla virtualbox)
![](media/image7.png)
15) Ustaw dolną kartę na stacji windows.
16) Podaj na jakim interfejsie pracuje usługa SAMBY
![](media/image8.png)
17) Zrestartuj usługę smbd i nmbd poleceniem:
*sudo systemctl restart smbd nmbd*
18) W logach nie może być błędów, szukamy wpisu:
![](media/image9.png)
19) Sprawdź status usługi
![](media/image10.png)
20) Sprawdź konfigurację narzędziem testparm
![](media/image11.png)
21) Jeśli wystąpią błędy podczas uruchamiania to popraw plik
    /etc/samba/smb.conf, i zrestartuj usługę.
22) Sprawdź czy istnieje proces dla serwera samby poleceniem: *ps aux \|
    grep smbd*
![](media/image12.png)
oraz
*htop -\> F3 wpisać smbd i enter, wyjście q*
![](media/image13.png)
23) Utwórz w sambie konto root: **pdbedit --a --u root** z hasłem
    ZAQ!2wsx
24) Utwórz w sambie konto twoje_imię: **pdbedit --a --u twoje_imię** z
    hasłem ZAQ!2wsx ( w poniższych marek)
25) Udostępnij zasób anonimowy na końcu pliku smb.conf o nazwie
    \[zas_ano\] dla użytkownika nobody
> Dodaj wpis guest ok = yes w zasobie
>
> ![](media/image14.png)
26) Przetestuj mapowanie zasobu na stacji windows i ubuntu desktop.
![](media/image15.png)
27) Utwórz w nim katalog lub plik
![](media/image16.png)
28) Zawartość na serwerze, zwróć uwagę na właściciela i grupę
    utworzonych plików, katalogów:
![](media/image17.png)
29) Udostępnij zasób, nie anonimowy na końcu pliku smb.conf:
![](media/image18.png)
30) Przetestuj mapowanie zasobu na stacji windows i ubuntu desktop.
![](media/image19.png)
31) Utwórz w nim katalog lub plik
![](media/image20.png)
32) Zawartość na serwerze, zwróć uwagę na właściciela i grupę
    utworzonych plików, katalogów:
![](media/image21.png)
33) Udostępnij zasób tylko dla siebie oraz wszystkich w grupie smbusers
![](media/image22.png)
34) Dodaj dwa konta
![](media/image23.png)
35) Przetestuj mapowanie zasobu na stacji windows i ubuntu desktop.
(po lewej brak możliwości zalogowania się spoza grupy smbusers, po
prawej konto marka )
![](media/image24.png)
![](media/image25.png)
36) Zawartość na serwerze, zwróć uwagę na właściciela i grupę
    utworzonych plików, katalogów:
![](media/image26.png)
37) Sprawdź czy zasób jest widoczny
![](media/image27.png)
38) Na stacji windows zamapuj zasob pod literę M:
![](media/image28.png)
39) Efekt końcowy:
![](media/image29.png)
40) Dodaj na stacji do zasobu plik i katalog:
![](media/image30.png)
41) Sprawdź zawartość zasobu na serwerze:
![](media/image31.png)
42) Dla powyższego zawartość sekcji \[global\]:
![](media/image32.png)
43) Na kliencie ubuntu desktop wydaj komendę: smbclient
![](media/image33.png)
44) Na kliencie ubuntu desktop uruchom przeglądarkę plików i sprawdź
    zasób:
![](media/image34.png)
I klikamy w zasób
![](media/image35.png)
45) Sprawdź połączenia:
![](media/image36.png)
46) Dodaj zasób 3
![](media/image37.png)
47) Test z konta monika:
![](media/image38.png)
![](media/image39.png)
48) Test z konta marek:
![](media/image40.png)
49) Dodatkowe zadania:
<!-- -->
a)  Zezwól na korzystanie z samby tylko z jednego ip, przetestuj
    działanie
b)  Zezwól na korzystanie z samby dla danej sieci z wyłączeniem jednego
    ip, przetestuj działanie
c)  Zarchiwizuj plik smb.conf 7-zipem w zasobie3
d)  Zarchiwizuj katalog /usr/share/doc
> ![](media/image41.png)
e)  Ukryj w zasobie drugim pliki z rozszerzeniem txt
f)  Pokaż w zasobie drugim pliki ukryte ( rozpoczynające się od .)
g)  zmień porty na których słucha serwer samba lub wpisz jawnie 445 i
    139
h)  utwórz różne pliki konfiguracyjne dla dwóch komputerów
<!-- -->
50) Przywrócić konfigurację netplan na dhcp.
51) Koniec.
