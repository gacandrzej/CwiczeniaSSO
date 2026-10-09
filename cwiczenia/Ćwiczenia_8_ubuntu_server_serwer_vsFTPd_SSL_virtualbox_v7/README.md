# Ćwiczenia 8 -- instalacja i konfiguracja serwera FTP ze źródeł

1. Zaloguj się na swoje konto.

1. Sprawdź czy zainstalowany jest pakiet vsftpd

1. Utwórz katalog /home/twoje_konto**/**vsftpd**/**, a w nim podkatalog
    download

1. Źródła pobrać narzędziem wget ze strony

   <https://security.appspot.com/downloads/vsftpd-3.0.5.tar.gz>

1. Sumę kontrolną pobrać narzędziem curl -O ze strony

   <https://security.appspot.com/downloads/vsftpd-3.0.5.tar.gz.asc>

   ![image1](media/image1.png)

1. Pobierz klucz GPG key (67A2 AB4F 41F9
    972C 21F6 BF66 7B89 011B CAE1 CFEA):

   ![image2](media/image2.png)

    Zaimportuj klucz:

1. Sprawdzić poprawność importu klucza komendą:

   ![image3](media/image3.png)

1. Sprawdź klucz komendą gpg --verify:

   ![image4](media/image4.png)

1. Sprawdzamy na stronie

   <https://security.appspot.com/vsftpd.html#download>

   odcisk palca.

   ![image5](media/image5.png)

1. Rozpakować plik **vsftpd-3.0.5.tar.gz** komendą tar.

   ![image6](media/image6.png)

1. Następnie przejść do katalogu vsftpd-3.0.5

1. Przeczytaj zawartość pliku INSTALL.

1. Wydać komendę: **make**

1. Jeśli make zakończy się bez błędów, wydać komendę:

   ![image7](media/image7.png)

1. Przejdź do katalogu /home/twoje_konto/vsftpd i załóż katalogi sbin,
    etc i log.

1. Ustaw uprawnienia:

   ![image8](media/image8.png)

1. Sprawdź czy istnieje konto ftp ( można
    sudo apt install vsftpd)

   ![image9](media/image9.png)

   ![image10](media/image10.png)
1. Ustaw prawa:

1. Uruchom serwer komendą:

   ![image11](media/image11.png)

1. Zaloguj się na serwerze i załóż katalog /usr/share/empty

   ![image12](media/image12.png)

1. Sprawdź czy istnieje proces dla serwera komendą: ps aux \| grep
    vsftpd

   ![image13](media/image13.png)

1. Utwórz plik:

   ![image14](media/image14.png)

1. Ściągnij plik

   ![image15](media/image15.png)

1. Sprawdź działanie serwera ftp, wyślij na serwer plik:

   ![image16](media/image16.png)

1. Sprawdź log, tail -f
    /var/log/vsftpd.log:

   ![image17](media/image17.png)

1. Ustaw banner ftp dla serwera na min. 30 znaków:

    ![image18](media/image18.png)

1. Sprawdź logi:

   ![image19](media/image19.png)

1. Przestaw logi na swoją lokalizację
    \~/vsftpd/log, utwórz dual log w oparciu o notatki z wykładu:

   ![image20](media/image20.png)

1. Sprawdź aktywne połączenia ze swoim serwerem komendą:

   ```bash
   netstat 
   lub 
   ss -anp | grep 21
   ```

   ![image21](media/image21.png)

1. Zezwól na logowanie się użytkowników systemowych, następnie wykonaj
    powyższe zadania dla swojego konta.

1. Stwórz konfigurację serwera dla obsługi SSL ( następna strona ).

1. Utwórz katalog ~/vsftpd_ssl/download

1. Skopiuj do niego plik vsftpd-3.0.5.tar.gz

   ![image22](media/image22.png)

1. Rozpakuj plik jak wcześniej:

1. Edycja pliku:

   ![image23](media/image23.png)

   ![image24](media/image24.png)

1. Zmodyfikuj plik Makefile tak, aby
    (dopisz Wno):

   ![image25](media/image25.png)

1. Wydaj komendę make.

1. Jeśli wystąpią błędy to zainstaluj
    pakiet libssl-dev.

   ![image26](media/image26.png)

1. Wydaj komendę make.

1. Wygeneruj certyfikat tak jak dla apache ( sudo openssl ....).

1. Reszta jak na wykładzie.

   ![image27](media/image27.png)

1. Przetestuj działanie serwera po ssl.

   ![image28](media/image28.png)

1. KONIEC. 🔚
