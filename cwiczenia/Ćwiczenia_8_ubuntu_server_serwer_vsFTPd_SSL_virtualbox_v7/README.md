Ćwiczenia 8 -- instalacja i konfiguracja serwera FTP ze źródeł
1.  Zaloguj się na swoje konto.
2.  Sprawdź czy zainstalowany jest pakiet vsftpd
3.  Utwórz katalog /home/twoje_konto**/**vsftpd**/**, a w nim podkatalog
    download
4.  Źródła pobrać narzędziem wget ze strony
    <https://security.appspot.com/downloads/vsftpd-3.0.5.tar.gz>
5.  Sumę kontrolną pobrać narzędziem curl -O ze strony
    <https://security.appspot.com/downloads/vsftpd-3.0.5.tar.gz.asc>
6.  ![](media/image1.png)
    Pobierz klucz GPG key (67A2 AB4F 41F9
    972C 21F6 BF66 7B89 011B CAE1 CFEA):
7.  ![](media/image2.png)
    Zaimportuj klucz:
8.  Sprawdzić poprawność importu klucza komendą:
![](media/image3.png)
9.  Sprawdź klucz komendą gpg --verify:
![](media/image4.png)
10. Sprawdzamy na stronie
    <https://security.appspot.com/vsftpd.html#download>
> odcisk palca.
![](media/image5.png)
11. Rozpakować plik **vsftpd-3.0.5.tar.gz** komendą tar.
> ![](media/image6.png)
12. Następnie przejść do katalogu vsftpd-3.0.5
13. Przeczytaj zawartość pliku INSTALL.
14. Wydać komendę: **make**
15. Jeśli make zakończy się bez błędów, wydać komendę:
![](media/image7.png)
16. Przejdź do katalogu /home/twoje_konto/vsftpd i załóż katalogi sbin,
    etc i log.
17. Ustaw uprawnienia:
> ![](media/image8.png)
18. ![](media/image9.png)
    Sprawdź czy istnieje konto ftp ( można
    sudo apt install vsftpd)
19. ![](media/image10.png)
    Ustaw prawa:
20. ![](media/image11.png)
    Uruchom serwer komendą:
21. Zaloguj się na serwerze i załóż katalog /usr/share/empty
![](media/image12.png)
22. Sprawdź czy istnieje proces dla serwera komendą: ps aux \| grep
    vsftpd
![](media/image13.png)
23. Utwórz plik:
![](media/image14.png)
24. Ściągnij plik
![](media/image15.png)
25. Sprawdź działanie serwera ftp, wyślij na serwer plik:
![](media/image16.png)
26. ![](media/image17.png)
    Sprawdź log, tail -f
    /var/log/vsftpd.log:
27. ![](media/image18.png)
    Ustaw banner ftp dla serwera na min.
    30 znaków:
28. ![](media/image19.png)
    Sprawdź logi:
29. ![](media/image20.png)
    Przestaw logi na swoją lokalizację
    \~/vsftpd/log, utwórz dual log w oparciu o notatki z wykładu:
30. ![](media/image21.png)
    Sprawdź aktywne połączenia ze swoim
    serwerem komendą: netstat lub ss -anp \| grep 21
31. Zezwól na logowanie się użytkowników systemowych, następnie wykonaj
    powyższe zadania dla swojego konta.
32. Stwórz konfigurację serwera dla obsługi SSL ( następna strona ).
33. Utwórz katalog \~/vsftpd_ssl/download
34. Skopiuj do niego plik vsftpd-3.0.5.tar.gz
35. ![](media/image22.png)
    Rozpakuj plik jak wcześniej:
36. Edycja pliku:
> ![](media/image23.png)
37. ![](media/image24.png)
    Zmodyfikuj plik Makefile tak, aby
    (dopisz Wno):
> ![](media/image25.png)
38. Wydaj komendę make.
39. ![](media/image26.png)
    Jeśli wystąpią błędy to zainstaluj
    pakiet libssl-dev.
40. Wydaj komendę make.
41. Wygeneruj certyfikat tak jak dla apache ( sudo openssl ....).
42. Reszta jak na wykładzie.
![](media/image27.png)
43. Przetestuj działanie serwera po ssl.
> ![](media/image28.png)
44. KONIEC
