# Ćwiczenia 9 -- Ubuntu serwer -- prawa do plików

Zaloguj się na swoje konto imienXYZ, gdzie XYZ oznacza kod klasy i
grupy, np. jank3t1

1. Dodaj swoje konto do grupy sudo:

   ```bash
   sudo usermod twoje_konto -G sudo
   ```

1. Sprawdzenie czy jesteśmy w grupie sudo:

   ```bash
   id konto
   ```

1. Status i restart usługi atd:

   ```bash
   sudo systemctl status atd
   sudo systemctl restart atd
   ```

1. Wyświetl listę wszystkich usług:

   ```bash
   sudo systemctl --no-pager | less
   ```

1. Stwórz katalog: `mkdir prawaXYZ`, za XYZ podaj kod klasy I grupy

1. Przejdź do założonego katalogu: `cd prawaXYZ`

1. Sprawdź ustawienia dla nowo tworzonych plików i katalogów:

   ```bash
   umask
   ```

1. mkdir katalog1, katalog2, touch plik1, plik2

1. ls -al lub ll

1. chmod 211 plik1

   ![image1](media/image1.png)

1. Nadaj uprawnienia:

   rw-r-xr\-- dla plik1,

   rwx-w\-\--x dla plik2,

   r-x\--x\--x dla katalog1,

   rw\--wxr\-- dla katalog2.

   ![image2](media/image2.png)

1. Polecenia:

   ```bash
   cd katalog2
   chmod 734 katalog2
   ```

   ![image3](media/image3.png)

1. mkdir dane, touch plik3, plik4

1. Polecenie:

   ```bash
   chmod 744 plik3
   ```

1. Sprawdzenie bitu t w systemie:

   ![image4](media/image4.png)

1. Sprawdzenie bitu s w systemie:

   ![image5](media/image5.png)

1. Ustawienie bitu s dla właściciela: chmod 4744 plik3 (małe s, tło
    pliku czerwone)

   ![image6](media/image6.png)

1. Ustawienie bitu s dla właściciela: chmod 4644 plik4 (dużo s, tło
    pliku czerwone)

   ![image7](media/image7.png)

1. Polecenie:

   ```bash
   chmod 654 plik4
   ```

   ![image8](media/image8.png)

1. Polecenie:

   ```bash
   chmod 2654 plik4 (małe s, tło pliku żółte)
   ```

   ![image9](media/image9.png)

1. chmod 2744 plik3 (duże s, tło pliku żółte)

   ![image10](media/image10.png)

1. chmod 6744 plik3 (małe s(właściciel),duże S(grupa), tło pliku
    czerwone)

   ![image11](media/image11.png)

1. cp plik3 plik4 dane

1. cd dane

   ![image12](media/image12.png)

1. chmod 745 plik3

1. chmod 1745 plik3 (małe t),

   ![image13](media/image13.png)

1. chmod 1654 plik4 (duże T)

   ![image14](media/image14.png)

1. chmod 7654 plik4 (duże s(właściciel),małe s(grupa),duże T,tło
    czerwone)

   ![image15](media/image15.png)

1. ls -alR ~/prawaXYZ ( \~ oznacza katalog domowy)

1. Polecenie:

   ```bash
   tree -pC ~/prawaXYZ\~
   ```

   ![image16](media/image16.png)

1. cd katalog1

1. mkdir doc1,doc2, touch plik5, plik6

   ![image17](media/image17.png)

1. Dodać uprawnienie w dla właściciela dla katalog1)

   ![image18](media/image18.png)

1. Polecenie:

   ```bash
   chmod u-x,g+w,o-r doc1
   ```

   ![image19](media/image19.png)

1. Polecenie:

   ```bash
   chmod -R 422 ~/prawaXYZ/katalog2
   ```

   ![image20](media/image20.png)

1. Z sudo

   ![image21](media/image21.png)

1. Wyszukanie wszystkich plików w katalogu /usr/bin z bitem s dla
    właściciela:

   ![image22](media/image22.png)

1. Na koniec zajęć polecenie:

   ```bash
   sudo shutdown now
   lub 
   poweroff
   ```
