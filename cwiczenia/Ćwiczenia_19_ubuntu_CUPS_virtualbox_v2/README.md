# Ćwiczenia 19 -- CUPS

1. Zaloguj się na swoje konto.
1. Na pierwszym terminalu:

   ![image1](media/image1.png)

1. Zainstaluj usługę cups:

   ```bash
   sudo apt install cups -y
   ```

1. Sprawdzić stan usługi: sudo systemctl status cups
1. W virtualbox dodaj kartę mostkową:

   ![image2](media/image2.png)

1. Na 5 terminalu : man cupsd.conf
1. Połącz się ze stacji windows do usługi cups.
1. Serwer wpięty do sieci, natomiast stacja tylko do serwera.

   ![image3](media/image3.png)

1. Ustaw na serwerze dostęp zdalny:

   ![image4](media/image4.png)

1. Dodaj drukarkę kyocerę FS-1320D na
    serwerze, znajdź sterownik PPD tak jak na wykładzie
   ![image5](media/image5.png)
1. Skopiuj sterownik ze stacji na serwer
    z użyciem winscp:

   ![image6](media/image6.png)

   ![image7](media/image7.png)

1. Wypakuj sterownik

   ![image8](media/image8.png)

1. Zainstaluj drukarkę
1. Krok 1: W lokalizacji podaj swoje imię

   ![image9](media/image9.png)
   
1. Krok 2

   ![image10](media/image10.png)

1. Krok 3

   ![image11](media/image11.png)

1. Zainstaluj na stacji windows z udostępnienia
    drukarki.

   ![image12](media/image12.png)

1. Zainstaluj na stacji ubuntu z udostępnienia drukarki.
1. Ze stacji wydrukuj stronę testową podając nazwę komputera stacjaX,
    za X podaj numer stanowiska.
1. Sprawdź na swoim serwerze stan drukarek

   ![image13](media/image13.png)

1. KONIEC.
