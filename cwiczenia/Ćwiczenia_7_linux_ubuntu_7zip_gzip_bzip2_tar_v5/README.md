Ćwiczenia 7 -- Ubuntu serwer -- archiwizacja, kompresja
Zaloguj się na swoje konto imienXYZ, gdzie XYZ oznacza kod klasy i
grupy, np. jank3t1
Jeśli nie masz konta, sudo adduser imienXYZ
1.  Dodaj swoje konto do grupy sudo: *sudo usermod twoje_konto -G sudo*
2.  Sprawdzenie czy jesteśmy w grupie sudo: *id konto*
3.  Zainstaluj 7-zip:
![](media/image1.png)
4.  ![](media/image2.png)
    Przygotować strukturę katalogów:
5.  Utwórz 4 pliki z pomocą komend:
> ![](media/image3.png)
6.  Utwórz archiwum w katalogu man powyższych plików:
![](media/image4.png)
7.  Utworzyć archiwum katalogu /usr/share/doc
![](media/image5.png)
8.  Sprawdź poprawność spakowania w programie mc. ( wejście w plik
    archiwum )
9.  Wypakuj archiwum doc.tar do katalogu \~/kopie/tar/
![](media/image6.png)
10. Spakuj katalog /usr/share/doc z użyciem tar, gzip, bzip2, xz i 7z
![](media/image7.png)
11. Porównaj wielkości poszczególnych plików archiwum (wartość w
    bajtach). Który jest najmniejszy?
![](media/image8.png)
12. Wypakuj powyższe pliki do odpowiednich katalogów, np.:
![](media/image9.png)
13. Pozostałe:
![](media/image10.png)
14. Wypakowanie archiwum 7z:
![](media/image11.png)
15. Spakuj plik doc.tar narzędziem gzip używając 5 stopnia kompresji.
Spakuj plik doc.tar narzędziem gzip używając 1 i 9 stopnia kompresji.
![](media/image12.png)
16. Wykonaj archiwum z pominięciem pliku:
![](media/image13.png)
17. Wykonaj archiwum tar.bz2 zachowując uprawnienia
![](media/image14.png)
18. Utwórz archiwum z pomocą gzipa plików man\*
![](media/image15.png)
19. Utwórz archiwum z pomocą gzipa plików man\* zastosuj najlepszy
    stopień kompresji
![](media/image16.png)
20. Utwórz archiwum z pomocą gzipa plików man\* zastosuj najgorszy
    stopień kompresji
![](media/image17.png)
21. Porównaj rozmiary powstałych plików
![](media/image18.png)
22. Rozpakuj wybrane dwa pliki \*.gz w katalogu gzip i gzip2
![](media/image19.png)
![](media/image20.png)
23. Utwórz archiwum z pomocą bzipa plików man\*
![](media/image21.png)
24. Sprawdź zawartość utworzonego archiwum
![](media/image22.png)
25. Utwórz archiwum z pomocą bzipa plików man\* zastosuj najlepszy
    stopień kompresji
![](media/image23.png)
26. Utwórz archiwum z pomocą bzipa plików man\* zastosuj najgorszy
    stopień kompresji
![](media/image24.png)
27. Porównaj rozmiary powstałych plików
![](media/image25.png)
28. Rozpakuj wybrane dwa pliki \*.bz2 w katalogu bzip i bzip2
![](media/image26.png)
29. Sprawdź poprawność rozpakowania.
30. Dodatkowe zadania:
<!-- -->
a)  ![](media/image27.png)
    Wyodrębnij tylko pliki z rozszerzeniem
    conf
b)  ![](media/image28.png)
    Sprawdź spójność archiwum bzip2, gzip,
    tar, 7z
c)  ![](media/image29.png)
    Wypisz informacje na temat
    skompresowanego pliku archiwum bzip2, gzip, tar, 7z
d)  Porównaj czas wykonania archiwum tar, gzip i bzip2
![](media/image30.png)
31. *sudo 31. shutdown now* ( na koniec zajęć)
