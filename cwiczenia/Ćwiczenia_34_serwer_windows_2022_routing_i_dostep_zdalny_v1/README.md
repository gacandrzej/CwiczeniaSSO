![](media/image1.jpeg)
Ćwiczenia 34 -- Routing i dostęp zdalny
1.  Zaloguj się na swoje konto administrator.
2.  Skonfiguruj serwer do roli routera.
    a)  Pierwszy interfejs o nazwie NIC1: ( dla sieci publicznej)
    - ip: 172.18.0.2
    - maska: 255.255.255.0
    - bramka: 172.18.0.1
    - DNS1: 8.8.8.8, DNS2: 8.8.4.4
    b)  Pierwszy interfejs o nazwie NIC2: ( dla sieci lokalnej )
\- ip: 10.0.1.2
\- maska: 255.255.255.0
\- bramka: brak
\- DNS1: brak
3.  Zainstaluj rolę DHCP:
\- dla podsieci 10.0.1.0/24 z zakresu 10.0.1.11- 10.0.1.29
\- adres domeny nadrzędnej zsmeie.local
\- przydziel bramkę
\- przydziel DNS
4.  Zainstaluj rolę Usługi zasad i dostępu sieciowego, zaznaczyć: Usługi
    routing i dostępu zdalnego
\- uruchom kreator: Konfiguruj i włącz routing i dostęp zdalny,
\- translator adresów sieciowych
\- wybierz interfejs publiczny
5.  Stację po lewej stronie serwera podłącz do interfejsu serwera
    odpowiadającego za sieć lokalną.
6.  Na stacji ( lewej ) sprawdź czy nowe ustawienia sieci zostały
    pobrane, jeśli nie to wyłącz i włącz kartę.
7.  Wykonaj ping do bramki. Wykonaj screena.
8.  Wykonaj ping do drugiej karty serwera. Wykonaj screena.
9.  Na drugiej stacji ( po prawej stronie serwera ) wpisz adres z maską
    i bramką.
10. Następnie wykonaj ping do bramki, drugiej karty serwera oraz drugiej
    stacji.
11. Dodaj zakres 2 na serwerze DHCP dla stacji po prawej stronie
    serwera.
12. Sprawdź pingi z obu stacji.
