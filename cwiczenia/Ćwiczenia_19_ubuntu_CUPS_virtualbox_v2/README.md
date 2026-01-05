Ćwiczenia 19 -- CUPS
1.  Zaloguj się na swoje konto.
2.  Na pierwszym terminalu:
> ![](media/image1.png)
3.  Zainstaluj usługę cups: sudo apt install cups -y
4.  Sprawdzić stan usługi: sudo systemctl status cups
5.  W virtualbox dodaj kartę mostkową:
> ![](media/image2.png)
6.  Na 5 terminalu : man cupsd.conf
7.  Połącz się ze stacji windows do usługi cups.
8.  Serwer wpięty do sieci, natomiast stacja tylko do serwera.
> ![](media/image3.png)
9.  Ustaw na serwerze dostęp zdalny:
> ![](media/image4.png)
10. ![](media/image5.png)
    Dodaj drukarkę kyocerę FS-1320D na
    serwerze, znajdź sterownik PPD tak jak na wykładzie
11. ![](media/image6.png)
    Skopiuj sterownik ze stacji na serwer
    z użyciem winscp:
> ![](media/image7.png)
12. Wypakuj sterownik
> ![](media/image8.png)
13. Zainstaluj drukarkę
14. ![](media/image9.png)
    Krok1 W lokalizacji podaj swoje imię
15. Krok 2
> ![](media/image10.png)
16. ![](media/image11.png)
    Krok 3
17. ![](media/image12.png)
    Zainstaluj na stacji windows z udostępnienia
    drukarki.
18. Zainstaluj na stacji ubuntu z udostępnienia drukarki.
19. Ze stacji wydrukuj stronę testową podając nazwę komputera stacjaX,
    za X podaj numer stanowiska.
20. Sprawdź na swoim serwerze stan drukarek
> ![](media/image13.png)
21. KONIEC.
