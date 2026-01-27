# Ćwiczenia 11 -- firewall, budowa i konfiguracja
 <img src="media/image1.png" width="5%" /> </p>

1.  Zaloguj się na swoje konto.
2.  Na pierwszym terminalu:
    ![](media/image2.png)
3.  Na 5 terminalu : 
 ```bash
    man iptables
 ```
4.  Wyczyścić wszystkie reguły w tablicy filter i nat oraz mangle

5. ![](media/image3.png)

5.  Sprawdź stan zapory.

![](media/image4.png)

6.  Ustawić dolne karty i ping do sąsiada. (Powinien działać)

7.  Ustaw politykę na DROP w tablicy filter dla łańcuchów `INPUT` i
    `FORWARD`

 ![](media/image5.png)

8.  Ustaw politykę na `ACCEPT` w tablicy filter dla łańcucha `OUTPUT`

![](media/image6.png)

Sprawdzenie:    

![](media/image7.png)

9.  Dopuścić połączenia związane i
    ustanowione. Dopuścić ruch dla aplikacji działających na maszynie
    lokalnej. (loopback lo)

![](media/image8.png)

10. Otworzyć możliwość sprawdzenia
    poleceniem ping (icmp echo reply request , kody 0 i 8) dla adresów z
    podsieci lokalnej.

    ![](media/image9.png)
    ![](media/image10.png)

11. Sprawdź połączenie ssh:

    ![](media/image11.png)

12. Na serwerze musi być zainstalowany
    pakiet openssh-server. Sprawdź działanie usługi ssh:

![](media/image12.png)

13. Otwórz port 22, na którym ma słuchać
    serwer ssh.

![](media/image13.png)

14. Sprawdź połączenie na tym porcie z komputera sąsiada.

![](media/image14.png)

15. Zapisz ustawienia w pliku
    _*/home/twoje_konto/iptables_rules_ddmmrrrr_hh:mm*_

![](media/image15.png)

16. Ruch wychodzący do portu 80 i 443 TCP ma być zablokowany.

![](media/image16.png)

17. Test w przeglądarce: lynx zsmeie.torun.pl (strona nie powinna się
    ładować)

18. Przywrócić ruch wychodzący po portach 80, 443.

 ![](media/image17.png)

19. Test w przeglądarce: lynx zsmeie.torun.pl (strona powinna się
    ładować)
20. Dopuścić ruch dla serwerów DNS dla cloudflare.  
Dla iptables:  

![](media/image18.png)  

Sprawdzenie:  

![](media/image19.png)

21. Zapisz ustawienia w pliku
    /home/twoje_konto/iptables_rules_ddmmrrrr_hh:mm

![](media/image20.png)

22. Otworzyć port dla pracy serwera ftp-data, ftp, tftp, mysql,
    postfix(4 porty), dhcp i dhcpv6, http, https
> ![](media/image21.png)
23. Zapisz ustawienia w pliku
    /home/twoje_konto/iptables_rules_ddmmrrrr_hh:mm
24. Zbuduj nat źródłowy dla sieci 10.11.12.0/24
> ![](media/image22.png)
>
> ![](media/image23.png)
25. ![](media/image24.png)
    Włącz forwardowanie pakietów tak, aby
    działało tylko do najbliższego restartu.
26. Wyczyścić wszystkie reguły w tablicy filter
> ![](media/image25.png)
27. ![](media/image26.png)
    Przywróć reguły z pliku:
28. ![](media/image27.png)
    Sprawdzenie:
29. Zablokować ruch do Rosji i Chin. Zainstaluj pakiet dla whois.
> Sprawdź działanie:
>
> ![](media/image28.png)
>
> ![](media/image29.png)
30. Monitorować ruch narzędziem tcpdump. ( W drugim terminalu uruchomić
    ping do dowolnej strony)
![](media/image30.png)
31. Monitorować ruch narzędziem wireshark na stacji ubuntu-desktop dla
    karty dolnej.
> Instalacja:
> ![](media/image31.png)
>
> Uruchomienie na stacji:
> ![](media/image32.png)
>
> Niebieska płetwa:
>
> ![](media/image33.png)
>
> Zapisz ruchu do pliku o nazwie test.pcapng.
>
> ![](media/image34.png)
32. Monitorować ruch narzędziem zen-map z poziomu stacji windows.
> ![](media/image35.png)
33. ![](media/image36.png)
    Sprawdzić otwarte porty na maszynie z
    pomocą narzędzia nmap np. port 22 dla ssh.
34. Sprawdzić otwarte porty na maszynie z pomocą narzędzia netcat.
Na stacji ubuntu:
![](media/image37.png)
35. Sprawdź pozostałe otwarte porty na swoim serwerze.
36. KONIEC.
