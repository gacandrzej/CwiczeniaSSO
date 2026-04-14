# Ćwiczenia 30 -- instalacja i konfiguracja IIS

1. Zaloguj się na konto administrator.

1. Uruchom menedżer serwera i sprawdź w pozycji serwer lokalny czy masz
    skonfigurowane obie karty.

   ![image1](media/image1.png)

1. Dodaj role:

   serwer sieci web (IIS),

   dodaj w kreatorze instalacji konfigurację dla **FTP**.

1. Sprawdź czy usługa routingu i dostępu zdalnego jest
   nieskonfigurowana, powinno być tak:

   ![image2](media/image2.png)

1. Uruchom przystawkę:

   ```text
   Menedżer Serwera->Narzędzia->Menedżer internetowych usług informacyjnych (IIS)
   ```

1. Sprawdź czy działa główna strona: (
   klikamy po prawej Browse \*:80 (http))

   ![image3](media/image3.png)

1. Sprawdź też adres 127.0.0.1

1. Utwórz swoją **witrynę www** o następujących ustawieniach *(nie
    podawać nazwy hosta*:

    - ip: 10.9.8.1, port 80, podkatalog
        c:\\Inetpub\\www1_twojeimię
    - ip: 172.18.19.2, port 8088, podkatalog
        c:\\Inetpub\\www2_twojeimię
    - ip: wszystkie nieprzypisane, port 85, podkatalog
        c:\\ferie\\www3_twojeimię
        **,** testujemy na wszystkich adresach ip*
    - https, ip 10.9.8.1 , port 443 podkatalog
        c:\\XYZ\\Inetpub\\www4_twojeimię

   ![image4](media/image4.png)

   *, gdzie XYZ oznacza kod klasy i grupy,

   wcześniej wygenerować
   samopodpisany certyfikat:

   ```text
   IIS→Serwer→Certyfikaty serwera→Utwórz

   ```

   certyfikat z podpisem własnym*

   ![image5](media/image5.png)

   ![image6](media/image6.png)

1. Uruchom na **serwerze** przeglądarkę i
   sprawdź działanie swoich stron. Pamiętaj o włączaniu, zatrzymywaniu
   i uruchamianiu odpowiedniej witryny, którą chcesz sprawdzić.

   ![image7](media/image7.png)

   ![image8](media/image10.png)

1. Dodaj domyślne nazwy stron zima.html i wiosna.html.

   ![image11](media/image11.png)

1. Zmień nazwy swoich plików index.html na powyższe, następnie
    przetestuj w przeglądarce.

1. Połącz się ze **stacji** i sprawdź działanie swoich witryn.

1. Sprawdź stan zapory na serwerze dla połączeń przychodzących, Narzędzia -\> ...
    Tools -\>

   ![image12](media/image12.png)

1. W katalogu c:\\Inetpub\\ftp_twojeimię
    utworzyć swoją witrynę ftp, o następujących ustawieniach:

    - ip: 10.9.8.1 port 21,

      c:\\Inetpub\\ftp1_twojeimię (brak SSL),

      ![image13](media/image13.png)

      *logowanie anonimowe tylko do odczytu ( wykonać get)*

      ![image14](media/image14.png)

    - ip: 172.18.19.2 port 23,

      c:\\Inetpub\\ftp2_twojeimię (brak SSL),

      logowanie anonimowe do odczytu i zapisu
      wykonać put i get

      ![image15](media/image15.png)

    - ip: 10.9.8.1 port 21,
      [c:\\ftp_XYZ\\](../../../../../../c:/Inetpub/%20ftp_twojeimię)*ftp3_twojeimię*,
      gdzie XYZ oznacza kod klasy i grupy

        *(brak SSL),*

        *logowanie podstawowe na twoje konto z AD,*

        *do odczytu i zapisu ( wykonać put i get)*

    - *ip: 10.9.8.1 port 2125,*
      c:\\ftp_XYZ\\
      *ftp4_twojeimię (zezwalaj na SSL, wcześniej wygenerowany
      samopodpisany certyfikat: IIS→Serwer→Certyfikaty serwera→Utwórz
      certyfikat z podpisem własnym),*

      *logowanie podstawowe na twoje konto z AD,*

       *tryb do odczytu*

       Widok wszystkich witryn ftp:

       ![image16](media/image16.png)

    - umieść w katalogach witryn po dwa pliki
    - do wszystkich witryn dodaj bannery ( przywitalny, transparentny i
      końcowy **minimum 20 znaków**)

      ![image17](media/image17.png)

1. Uruchom wiersz poleceń i zaloguj się na serwer ftp na wszystkie
   adresy z serwera, np. cmd, potem wpisać

   ```bash
   ftp 10.9.8.1
   ```

1. Sprawdź działanie witryn ftp w
    przeglądarkach.

    ![image18](media/image18.png)

1. Połącz się ze **stacji** i sprawdź działanie swoich witryn **ftp** w
   przeglądarkach i wierszu poleceń.

   ![image20](media/image20.png)

   ![image22](media/image22.png)

   ![image23](media/image23.png)

1. Dla wybranych dwóch witryn ftp

   - zmodyfikuj „reguły autoryzacji"
   - zmodyfikuj „uwierzytelnianie ftp"

1. Na stacji uruchom Wiresharka i
   przechwyć komunikację do twojej witryny www i ftp.

    ![image24](media/image24.png)

    ![image25](media/image25.png)

1. Połącz się ze stacji za pomocą VPN, instrukcja na teams. (nie
   podłączamy stacji do domeny!!!)

   ![image26](media/image26.png)

   ![image27](media/image27.png)

1. Ustanowienie połączenia VPN.

   ![image28](media/image28.png)

1. W katalogu c:\\Inetpub\\www_twojeimię\ utworzyć
   swoją *witrynę www* o następujących ustawieniach:

   - ip: 10.11.12.1 port 8089 dla połączenia VPN, podkatalog
     *www5_vpn_twojeimię*
   - ip: 10.11.12.1 port 8099 dla połączenia VPN, podkatalog
        www6_vpn_twojeimię

1. W katalogu c:\\Inetpub\\ftp_twojeimię
   utworzyć swoją *witrynę ftp* o następujących ustawieniach:

   - ip: 10.11.12.1 port 2122 dla połączenia VPN, podkatalog
     ***ftp5_vpn_twojeimię** (brak SSL),*

     *logowanie anonimowe*

     *do odczytu i zapisu*

     ![image29](media/image29.png)

   - *ip: 10.11.12.1 port 2124 dla połączenia VPN,
     podkatalog **ftp6_vpn_twojeimię** (zezwalaj na SSL),*
     *logowanie podstawowe na twoje konto z AD,
     tryb do odczytu i zapisu*

   - *zmodyfikować „reguły autoryzacji" oraz „uwierzytelnianie ftp"*

   - *do obu witryn dodaj wybrany banner ( przywitalny, transparentny lub
    końcowy **minimum 30 znaków**)*

1. Połącz się ze stacji za pomocą VPN i sprawdź działanie swoich witryn
    www oraz ftp na oba adresy, jeżeli nie można się połączyć to włączyć
    regułę na firewallu serwera zezwalającą na połączenia.

   ![image30](media/image30.png)

1. Na stacji uruchom Wiresharka i przechwyć komunikację do twojej
   witryny www i ftp.

1. Utwórz połączenie VPN ze stacji ubuntu desktop.

   ![image31](media/image31.png)

   ![image32](media/image32.png)

   ![image33](media/image33.png)

1. Sprawdź działanie swoich witryn www oraz ftp na oba adresy. (Ctrl+l)

   ![image34](media/image34.png)

   ![image35](media/image35.png)

1. Wykonaj dodatkowe zadanie podane przez nauczyciela:

   - W DNS dodaj strefę przeszukiwania wstecz, następnie dodaj
     odpowiednie rekordy tak, aby można było odczytaj stronę www
     poprzez adres: [www.zsmeie.abcd](http://www.zsmeie.abcd/)

   - przekieruj porty na routerze tak, aby po wpisaniu na stacji
     adresu [http://50.50.50.1:8080](http://50.50.50.1:8080/)

     wyświetliła się strona z serwera 10.9.8.1:80.

     Wskazówki:

     Ustaw na routerze:

     WAN: 50.50.50.1, z maską 24

     ![image38](media/image38.png)

     LAN: 10.9.8.5 z maską zgodną z kartą serwera

     Na stacji: ip stacji, dolna karta: 50.50.50.2/24 z bramką 50.50.50.1

1. Dodatkowe zadanie.

1. Wyłączyć routing i dostęp zdalny

   ![image2](media/image2.png)

1. Zresetuj ustawienia zapory na serwerze do ustawień domyślnych.

   ![image40](media/image40.png)

1. KONIEC.🔚
