# Ćwiczenia 21 -- instalacja i konfiguracja serwera FTP - vsFTPd

1. Zaloguj się na swoje konto.
1. Wyłącz zaporę: sudo ufw reset
1. Odinstaluj vsftpd:

   ```bash
   sudo apt remove vsftpd \--purge -y
   ```

1. Usunąć katalog /ftp jeśli istnieje
1. Zainstaluj serwer vsftpd:

   ```bash
   sudo apt install vsftpd -y
   ```

1. Ustaw kartę podłączoną do switcha z pomocą netplanu na adres
    172.17.20.x/28, gdzie x oznacza numer stanowiska (1-16).

   ```yaml
   addresses: [172.17.20.101/28]
   ```

1. Edytuj plik konfiguracyjny np.:

   ```bash
   sudo mcedit /etc/vsftpd.conf
   ```

1. Ustaw w pliku konfiguracyjnym opcję

   ```text
   listen=NO 
   listen_ipv6=YES
   ```

1. Ustaw baner powitalny jako string.

1. Włącz zaporę na serwerze:

   ![image1](media/image1.png)

1. Otworzyć porty 20,21:

   ![image2](media/image2.png)

1. Uruchom serwer komendą:

   ```bash
   sudo systemctl restart vsftpd
   ```

1. Sprawdź czy istnieje proces dla serwera komendą:

   ```bash
   ps aux | grep vsftpd
   ```

1. Uruchom terminal z podglądem logów:

   ```bash
   sudo journalctl -f
   ```

1. Utwórz plik tekstowy o nazwie twoje_imie.txt w katalogu **/srv/ftp**

1. Przetestuj działanie serwera logując
    się do niego anonimowo: [ftp 127.0.0.1]

   ![image3](media/image3.png)

1. W ćwiczeniach skorzystaj, również ze skryptów na ubuntu server do testowania logowania i korzystania z usługi ftp:

   - pierwszy skrypt testuje jednocześnie dwóch użytkowników:

   ```bash
    #!/bin/bash
    # --- Logowanie użytkownika Ania ---
    echo "--- Logowanie: ania ---"
    ftp -inv localhost 21 <<'EOF'
    user ania tajnehaslo_ani
    ls
    quit
    EOF

    echo ""

    # --- Logowanie użytkownika Henryk ---

    echo "--- Logowanie: henryk ---"
    ftp -inv localhost 21 <<'EOF'
    user henryk tajnehaslo_henryka
    ls
    quit
    EOF

   ```

   - drugi skrypt uruchamiaj z parametrem login i hasło, np.:

   ```bash
   bash skrypt2.sh ania ZAQ!2wsx
   ```

   ```bash
    USERNAME="$1"
    PASSWORD="$2"
    HOST="localhost"
    PORT="21"

    echo "--- Logowanie użytkownika: $USERNAME na $HOST:$PORT ---"

    ftp -inv "$HOST" "$PORT" <<EOF
    user "$USERNAME" "$PASSWORD"
    ls
    quit
    EOF

   ```

1. Przetestuj działanie serwera logując się do niego anonimowo ze
    stacji Windows: ftp ip_servera.

   ![image4](media/image4.png)

1. Aby listować zawartość katalogu ftp ustaw:

   ![image5](media/image5.png)

   ![image6](media/image6.png)

1. Przetestuj działanie serwera logując się do niego anonimowo ze
    stacji Windows w eksploratorze

   [ftp://ipserwera](ftp://ipserwera/)

   ![image7](media/image7.png)

1. Ściągnij plik z katalogu pub komendą: get nazwa_pliku najpierw na
    serwerze potem na stacji.

   ![image8](media/image8.png)

1. Sprawdź xferlog:

   ![image9](media/image9.png)

1. Upewnij się,że są odkomentowane pozycje:

   ![image10](media/image10.png)

1. Skopiuj plik testowy na serwer ftp anonimowo komendą put z serwera i
    stacji.

   ![image11](media/image11.png)

1. Ustaw baner z pliku. ( zadanie domowe )

1. Utwórz katalog /ftp a w nim katalog pub, następnie zmień domyślną
    lokalizację z /srv/ftp na katalog /ftp komendą:

   ![image12](media/image12.png)

1. Ustaw prawa i utwórz pliki jak poniżej:

   ![image13](media/image13.png)

1. Analogicznie przetestuj komendy put i get oraz mput, mget dla nowej
    lokalizacji `/ftp` oraz `/ftp/pub`.

1. Sprawdź połączenie z pomocą wireshark.
    Sprawdź czy możesz utworzyć katalog jako anonymous.

   ![image14](media/image14.png)

1. Zezwól na logowanie się tylko wybranym użytkownikom systemowym,
    pozwól im wyjść poza swój katalog domowy.

   ![image15](media/image15.png)

1. Przetestuj działanie serwera logując się na konto z listy oraz swoje
    konto systemowe: [ftp 172.17.20.x]

   ![image16](media/image16.png)

1. Zezwól na logowanie się tylko wybranym użytkownikom systemowym,
    **nie pozwól** im wyjść poza swój katalog domowy.

   ![image17](media/image17.png)

1. Przetestuj działanie serwera logując się na konto z listy oraz swoje
    konto systemowe: [ftp 172.17.20.x]

   ![image18](media/image18.png)

1. Zabroń dostępu do ftp dla konta z listy `/etc/ftpusers`

1. Przetestuj działanie serwera logując się na swoje konto systemowe:

   ```bash
   ftp 172.17.20.x
   ```

1. Sprawdź zawartość logów.

1. Zabroń dostępu do ftp dla użytkowników z pomocą:

   ```text
    userlist_file=/home/twoje_konto/...
    userlist_enable
    userlist_deny=YES | NO
   ```

1. Przetestuj działanie serwera logując się na konto z listy oraz swoje
    konto systemowe: [ftp 172.17.20.x]

1. Przetestuj działanie serwera w filezilli logując się na konto
    anonimowe i swoje:

   ![image19](media/image19.png)

1. Sprawdź zawartość logów.

1. Logowanie po sftp: ( otwórz port 22)

   ![image20](media/image20.png)

1. Skonfigurować serwer dla połączeń szyfrowanych, spróbuj najpierw
    ustawień domyślnych dla certyfikatów:

   ![image21](media/image21.png)

1. II sposób, samodzielna generacja certyfikatu, poniżej 1 polecenie:

   ```bash
   sudo openssl req -x509 -nodes -days 365 -newkey rsa:2048 -keyout /etc/ssl/private/cert.pem -out /etc/ssl/private/cert.pem
    ```

1. W pliku vsftpd.conf

   ![image22](media/image22.png)

1. Otwórz port 990 na zaporze dla połączeń po TLS.

1. Z pomocą klienta ftp np. filezilli
    utwórz połączenie, skopiuj plik, ściągnij plik.

   ![image23](media/image23.png)

1. Wyświetli się certyfikat

   ![image24](media/image24.png)

1. Sprawdź połączenie z pomocą wireshark.

   ![image25](media/image25.png)

1. Sprawdź łączenie się klientem lftp po TLS

   ![image26](media/image26.png)

1. Wyłącz zaporę:

   ```bash
   sudo ufw reset
   ```

1. Odinstaluj vsftpd:

   ```bash
   sudo apt remove vsftpd \--purge -y
   ```

1. Usunąć katalog /ftp jeśli istnieje
1. KONIEC.( lekcje 1-3).😀

---

1. Powtórzenie ( lekcje 4-6 ):

1. Przećwicz zachowanie serwera logując się na konta dla ustawienia
    `userlist_deny=YES|NO`.

1. Zmień porty ftp serwera na `24`. Sprawdź logowanie się do serwera ze
    stacji.

1. Zmień port ftp-data na `23`. Sprawdź logowanie się do serwera ze
    stacji.

1. Ustaw maskę nowo tworzonych plików na 011 zarówno przez użytkowników
    systemowych jak i anonimowych.

1. Zabroń dostępu do plików z rozszerzeniem: `png, jpg i bmp`. Przetestuj
    ze stacji nowe ustawienia.

1. Ukryj pliki z rozszerzeniem: `pdf, docx, xlsx`. Przetestuj ze stacji
    nowe ustawienia.

1. Przetestuj ustawienia `chown_username` i `chown_uploads`.

1. Ustaw maksymalnie dwa połączenia z danego ip.

1. Ustaw maksymalnie trzech klientów, którzy mogą się połączyć z
    serwerem.

1. Ustaw prędkość przesyłania danych na 50KB.

1. Ustaw baner z pliku.

1. Przetestuj ustawienia `anon_root` oraz `local_root`.

1. Zabroń na stałe dostępu do serwera dla użytkownika `Wojtek`.

1. Zabroń wychodzenia poza katalog domowy wszystkim użytkownikom **z
    wyjątkiem** `Moniki` i `Marka`, plik listy utwórz w katalogu domowym.

1. Zabroń dostępu do ftp wszystkim użytkownikom **z wyjątkiem Beaty** i
    **Tomka**, plik listy utwórz w katalogu domowym.

1. Zezwól na wychodzenie poza katalog domowy wszystkim użytkownikom **z
    wyjątkiem** `Moniki` i `Marka`, plik listy utwórz w katalogu domowym.

1. Zezwól na dostępu do ftp wszystkim użytkownikom **z wyjątkiem** `Beaty`
    i `Tomka`, plik listy utwórz w katalogu domowym.

1. Włącz tryb tekstowy przesyłania danych na kliencie ftp.

1. Włącz tryb binarny przesyłania danych na kliencie ftp.

1. Ustaw timeout serwera na 5 minut.

1. Koniec.🔚
