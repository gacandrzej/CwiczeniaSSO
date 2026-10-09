# Ćwiczenia 11 -- firewall, budowa i konfiguracja

 <img src="media/image1.png" width="5%" /> </p>

1. Zaloguj się na swoje konto.
1. Na pierwszym terminalu:

   ![image2](media/image2.png)

1. Na 5 terminalu :

 ```bash
    man iptables
 ```

1. Wyczyścić wszystkie reguły w tablicy filter i nat oraz mangle

   ![image3](media/image3.png)

1. Sprawdź stan zapory.

   ![image4](media/image4.png)

1. Ustawić dolne karty i ping do sąsiada. (Powinien działać)

1. Ustaw politykę na DROP w tablicy filter dla łańcuchów `INPUT` i
    `FORWARD`

   ![image5](media/image5.png)

1. Ustaw politykę na `ACCEPT` w tablicy filter dla łańcucha `OUTPUT`

   ![image6](media/image6.png)

   Sprawdzenie:

   ![image7](media/image7.png)

1. Dopuścić połączenia związane i
    ustanowione. Dopuścić ruch dla aplikacji działających na maszynie
    lokalnej. (loopback lo)

   ![image8](media/image8.png)

1. Otworzyć możliwość sprawdzenia
    poleceniem ping (icmp echo reply request , kody 0 i 8) dla adresów z
    podsieci lokalnej.

    ![image9](media/image9.png)
    ![image10](media/image10.png)

1. Sprawdź połączenie ssh:

    ![image11](media/image11.png)

1. Na serwerze musi być zainstalowany
    pakiet openssh-server. Sprawdź działanie usługi ssh:

    ```bash
    sudo apt install openssh-server -y
    ```

   ![image12](media/image12.png)

1. Otwórz port 22, na którym ma słuchać serwer ssh.

    ```bash
    sudo iptables -A INPUT -p tcp -m state --state NEW --dport 22 -j ACCEPT
    ```

   ![image13](media/image13.png)

1. Sprawdź połączenie na tym porcie z komputera sąsiada.

   ![image14](media/image14.png)

1. Zapisz ustawienia w pliku
    _*/home/twoje_konto/iptables_rules_ddmmrrrr_hh:mm*_

   ![image15](media/image15.png)

1. Ruch wychodzący do portu 80 i 443 TCP ma być zablokowany.

   ![image16](media/image16.png)

1. Test w przeglądarce: lynx zsmeie.torun.pl (strona nie powinna się
    ładować)

1. Przywrócić ruch wychodzący po portach 80, 443.

   ![image17](media/image17.png)

1. Test w przeglądarce: lynx zsmeie.torun.pl (strona powinna się
    ładować)

1. Dopuścić ruch dla serwerów DNS dla cloudflare.  
   Dla iptables:  

   ![image18](media/image18.png)  

   Sprawdzenie:  

   ![image19](media/image19.png)

1. Zapisz ustawienia w pliku  _*/home/twoje_konto/iptables_rules_ddmmrrrr_hh:mm*_

   ![image20](media/image20.png)

1. Otworzyć port dla pracy serwera:

    - ftp-data,
    - ftp,
    - tftp,
    - mysql,
    - postfix(4 porty),
    - dhcp
    - dhcpv6,
    - http,
    - https

    ![image21](media/image21.png)

1. Zapisz ustawienia w pliku _*/home/twoje_konto/iptables_rules_ddmmrrrr_hh:mm*_

1. Zbuduj nat źródłowy dla sieci **10.11.12.0/24**

   ![image22](media/image22.png)

   ![image23](media/image23.png)

1. Włącz forwardowanie pakietów tak, aby działało tylko do najbliższego restartu.

   ![image24](media/image24.png)

1. Wyczyścić wszystkie reguły w tablicy filter

   ![image25](media/image25.png)

1. Przywróć reguły z pliku:

   ![image26](media/image26.png)

1. Sprawdzenie:

   ![image27](media/image27.png)

1. Zablokować ruch do Rosji i Chin. Zainstaluj pakiet dla whois.

   Sprawdź działanie:

   ![image28](media/image28.png)  

   ![image29](media/image29.png)

1. Monitorować ruch narzędziem tcpdump. ( W drugim terminalu uruchomić
    ping do dowolnej strony)

   ![image30](media/image30.png)

1. Monitorować ruch narzędziem wireshark na stacji ubuntu-desktop dla
    karty dolnej.

   Instalacja:

   ![image31](media/image31.png)  

   Uruchomienie na stacji:  

   ![image32](media/image32.png)  

   Niebieska płetwa:  

   ![image33](media/image33.png)  

   Zapisz ruchu do pliku o nazwie test.pcapng.  

   ![image34](media/image34.png)

1. Monitorować ruch narzędziem zen-map z poziomu stacji windows.  

   ![image35](media/image35.png)

1. Sprawdzić otwarte porty na maszynie z
    pomocą narzędzia nmap np. port 22 dla ssh.

   ![image36](media/image36.png)

1. Sprawdzić otwarte porty na maszynie z pomocą narzędzia netcat.
   Na stacji ubuntu:

   ![image37](media/image37.png)

1. Sprawdź pozostałe otwarte porty na swoim serwerze.

2. KONIEC. 🔚
