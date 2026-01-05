![](media/image1.png)
Ćwiczenia 22 -- instalacja i konfiguracja serwera Apache
1.  Zaloguj się na swoje konto.
2.  Sprawdź czy zainstalowany jest pakiet openssl
![](media/image2.png)
3.  Utwórz katalog /home/twoje_konto**/apache/**, a w nim podkatalog
    **download**
4.  Źródła można pobrać ze strony
    <https://dlcdn.apache.org/httpd/httpd-2.4.63.tar.bz2> narzędziem
    wget.
5.  Sumę kontrolną gpg pobieramy ze strony
    [https://downloads.apache.org/httpd/httpd-2.4.63.tar.bz2.asc](https://downloads.apache.org/httpd/httpd-2.4.54.tar.bz2.asc)
narzędziem wget.
6.  Sumę kontrolną pobieramy:
    [https://downloads.apache.org/httpd/httpd-2.4.63.tar.bz2.sha256](https://downloads.apache.org/httpd/httpd-2.4.54.tar.bz2.sha256)
    narzędziem curl.
> ![](media/image3.png)
7.  Sprawdzić sumę kontrolną narzędziem sha256sum httpd-2.4.63.tar.bz2 i
    cat httpd-2.4.63.tar.bz2.sha256
lub shasum -a 256 -c httpd-2.4.63.tar.bz2.sha256
![](media/image4.png)
8.  ![](media/image5.png)
    Sprawdzić numer klucza (pierwsza
    poniższa komenda go wyświetli ) i go ściągnąć:
9.  gpg \--verify httpd-2.4.63.tar.bz2.asc httpd-2.4.63.tar.bz2
![](media/image6.png)
10. Sprawdzamy na stronie <https://people.apache.org/keys/committer/>
    odcisk palca.
![](media/image7.png)
11. Rozpakować plik **httpd-2.4.63.tar.bz2** komendą tar.
12. następnie przejść do katalogu httpd-2.4.63
13. Wydać komendę:
**./configure \--prefix=/home/twoje_konto/apache
\--with-ssl=/usr/bin/openssl \--enable-ssl \--enable-so**
14. W przypadku braku APR zainstaluj potrzebne pakiety komendą:
sudo apt-get install libapr1-dev libaprutil1-dev -y
15. W przypadku braku kompilatora c: build-essential lub gcc i g++
16. W przypadku braku pcre3: zainstaluj pakiet pcre: **sudo apt install
    libpcre3-dev libpcre3 -y**
17. libssl-dev - \> openssl is too old
18. Wydać komendę: **make -j\$(nproc)**
19. Wydać komendę: **make install**
![](media/image8.png)
20. Sprawdź czy jest APR: apache/bin/**httpd -V**
21. Przejdź do katalogu /home/twoje_konto/apache i sprawdź czy powstały
    katalogi
22. ![](media/image9.png)
    Uruchomić serwer komendą: sudo
    **bin/apachectl restart**
23. ![](media/image10.png)
    Jeśli wystąpią błędy odkomentuj i zmień wpis
24. Sprawdź czy istnieje proces dla serwera komendą: ps aux \| grep
    apache
![](media/image11.png)
25. Uruchomić przeglądarkę i sprawdzić działanie wpisując: **localhost
    lub ip serwera**
![](media/image12.png)
26. Sprawdź konfigurację poleceniem: apachectl configtest.
27. W chrome w górnym pasku DevTools kliknij i wybierz **Lighthouse**
28. Sprawdź działanie strony narzędziem curl:
![](media/image13.png)
29. Sprawdź logi: cat \~/apache/logs/error_log i cat
    \~/apache/logs/access_log
![](media/image14.png)
30. Jeśli nie działa serwer to sprawdź uprawnienia na katalogu
    /home/twoje_konto powinno być 751
31. Analogicznie przetestuj serwer linksowy sąsiada.(wpisz ip sąsiada w
    przeglądarce lub narzędziem curl -v ip)
32. Jeśli nie możesz skorzystać z serwera sąsiada to należy otworzyć
    porty **80 i 443**.
33. Sprawdź połączenie z pomocą wireshark.
34. Sprawdź zawartość logów.
35. Popraw wygląd swojej strony. ( plik: \~/apache/htdocs/index.html )
36. Wygeneruj certyfikat dla servera z pomocą openssl ( patrz wykład).
37. Klucz prywatny serwera:
38. ![](media/image15.png)
    Certyfikat:
39. Zdjęcie hasła:
> ![](media/image17.png)
40. Odkomentuj linię: *Include conf/extra/httpd-ssl.conf* w pliku
    \~/apache/conf/httpd.conf
41. Zrestartuj serwer : sudo bin/apachectl restart
42. Uruchomić przeglądarkę i sprawdzić działanie wpisując:
    [https://localhost](https://localhost/)
![](media/image18.png)
43. Sprawdź działanie strony narzędziem curl:
![](media/image19.png)
44. Powinien powstać plik \~/apache/logs/ssl_request_log
![](media/image20.png)
45. Sprawdź aktywne połączenia ze swoim serwerem komendą: netstat lub ss
    -anp \| grep 443
![](media/image21.png)
46. Sprawdź aktywne połączenia ze swoim serwerem
![](media/image22.png)
47. Dodać możliwość tworzenia stron www przez użytkowników systemowych:
    np. <https://localhost/~twoje_konto> ( wskazówka: public_html )
![](media/image23.png)
wskazówka 2:
![](media/image24.png)
wskazówka 3:
![](media/image25.png)
48. Dodatkowe:
<!-- -->
a)  Utwórz własne usługi dla apache: apache-twoje-imię
> \- Utwórz nowy plik serwisowy: sudo nano
> /etc/systemd/system/apache_imie.service
>
> \- Zawartość pliku apache_imie.service:
>
> ![](media/image26.png)
>
> \- nadaj uprawnienia i odświeź systemd:
>
> ![](media/image27.png)
>
> \- Uruchom nową usługę: sudo systemctl start apache_imie
b)  dsd
<!-- -->
49. KONIEC
