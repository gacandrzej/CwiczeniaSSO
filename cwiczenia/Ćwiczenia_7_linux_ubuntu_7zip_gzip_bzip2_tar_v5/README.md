# Ćwiczenia 7 -- Ubuntu serwer -- archiwizacja, kompresja

💡 Zaloguj się na swoje konto imienXYZ, gdzie XYZ oznacza kod klasy i
grupy, np. jank3t1
Jeśli nie masz konta,

```bash
sudo adduser imienXYZ
```

1. Dodaj swoje konto do grupy sudo:

   ```bash
   sudo usermod twoje_konto -G sudo
   ```

1. Sprawdzenie czy jesteśmy w grupie sudo:

   ```bash
   id konto
   ```

1. Zainstaluj 7-zip:

   ```bash
    sudo apt install p7zip-full
   ```

   ![image1](media/image1.png)

1. Przygotować strukturę katalogów:

   ![image2](media/image2.png)

1. Utwórz 4 pliki z pomocą komend:

    ```bash
    man ls > man_ls.txt
    man tar > man_tar.txt
    man gzip > man_gzip.txt
    man bzip2 > man_bzip2.txt
    
    ```

   ![image3](media/image3.png)

1. Utwórz archiwum w katalogu man powyższych plików:

   ![image4](media/image4.png)

1. Utworzyć archiwum katalogu _/usr/share/doc_

   ![image5](media/image5.png)

1. Sprawdź poprawność spakowania w programie mc. ( wejście w plik
    archiwum )

1. Wypakuj archiwum doc.tar do katalogu _~/kopie/tar/_

   ![image6](media/image6.png)

1. Spakuj katalog _/usr/share/doc_ z użyciem `tar`, `gzip`, `bzip2`, `xz` i `7z`

   ```bash
   tar cfz doc.tar.gz -P /usr/share/doc/
   ```

   ![image7](media/image7.png)

1. Porównaj wielkości poszczególnych plików archiwum (wartość w
    bajtach). Który jest najmniejszy?

   ![image8](media/image8.png)

1. Wypakuj powyższe pliki do odpowiednich katalogów, np.:

   ![image9](media/image9.png)

1. Pozostałe:

   ![image10](media/image10.png)

1. Wypakowanie archiwum 7z:

   ![image11](media/image11.png)

1. Spakuj plik doc.tar narzędziem gzip używając 5 stopnia kompresji.
   Spakuj plik doc.tar narzędziem gzip używając 1 i 9 stopnia kompresji.

   ![image12](media/image12.png)

1. Wykonaj archiwum z pominięciem pliku:

   ![image13](media/image13.png)

1. Wykonaj archiwum tar.bz2 zachowując uprawnienia

   ![image14](media/image14.png)

1. Utwórz archiwum z pomocą gzipa plików man

   ![image15](media/image15.png)

1. Utwórz archiwum z pomocą gzipa plików man\* zastosuj najlepszy
    stopień kompresji

   ![image16](media/image16.png)

1. Utwórz archiwum z pomocą gzipa plików man\* zastosuj najgorszy
    stopień kompresji

   ![image17](media/image17.png)

1. Porównaj rozmiary powstałych plików

   ![image18](media/image18.png)

1. Rozpakuj wybrane dwa pliki \*.gz w katalogu gzip i gzip2

   ![image19](media/image19.png)

   ![image20](media/image20.png)

1. Utwórz archiwum z pomocą bzipa plików man\*

   ![image21](media/image21.png)

1. Sprawdź zawartość utworzonego archiwum

   ![image22](media/image22.png)

1. Utwórz archiwum z pomocą bzipa plików man\* zastosuj najlepszy
    stopień kompresji

   ![image23](media/image23.png)

1. Utwórz archiwum z pomocą bzipa plików man\* zastosuj najgorszy
    stopień kompresji

   ![image24](media/image24.png)

1. Porównaj rozmiary powstałych plików

   ![image25](media/image25.png)

1. Rozpakuj wybrane dwa pliki \*.bz2 w katalogu bzip i bzip2

   ![image26](media/image26.png)

1. Sprawdź poprawność rozpakowania.

1. Dodatkowe zadania:

   - wyodrębnij tylko pliki z rozszerzeniem conf

     ![image27](media/image27.png)

   - sprawdź spójność archiwum bzip2, gzip, tar, 7z

     ![image28](media/image28.png)

   - wypisz informacje na temat skompresowanego pliku archiwum bzip2, gzip, tar, 7z

     ![image29](media/image29.png)

   - porównaj czas wykonania archiwum tar, gzip i bzip2

     ![image30](media/image30.png)

1. Na koniec zajęć:

```bash
 sudo shutdown now 
```
