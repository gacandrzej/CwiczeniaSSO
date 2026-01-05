Ćwiczenia 4 -- Ubuntu serwer -- crontab, at
Zaloguj się na swoje konto imienXYZ, gdzie XYZ oznacza kod klasy i
grupy, np. jank3t1
Jeśli nie masz konta, sudo adduser imienXYZ
1.  Dodaj swoje konto do grupy sudo: *sudo usermod twoje_konto -G sudo*
2.  Sprawdzenie czy jesteśmy w grupie sudo: *id konto*
3.  Wydaj komendę na piątym terminal: man at
4.  Wydaj komendę na szóstym terminalu: info crontab
5.  Otwórz pomocniczo na czwartym terminal: cat /etc/crontab
6.  Otwórz stronę pomocy, np.: <https://crontab.guru/>
7.  Zainstaluj obsługę poczty: sudo apt install mailutils podaj tylko
    lokanie
8.  Sprawdzić pocztę komendą mail
9.  Z pomocą polecenia crontab zaplanuj:
<!-- -->
a)  ![](media/image1.png)
    Archiwizuj swój katalog domowy co 1
    minutę do katalogu /var/backups oraz /tmp z użyciem tara i gzipa
b)  Utwórz co 1 minutę podając dzień i miesiąc plik o nazwie
    plikcrontabtest w \~
![](media/image2.png)
c)  Uruchom skrypt co 1 minutę w każdy dzień roboczy pobierający wycenę
    bitcoina ze strony: <https://api.coinbase.com>
> ![](media/image3.png)
>
> ![](media/image4.png)
>
> ![](media/image5.png)
>
> Efekt działania:
>
> ![](media/image6.png)
d)  ![](media/image7.png)
    uruchomienie skryptu skrypt3.sh
    zbierającego statystyki pracy karty sieciowej z ostatnich 5 minut o
    zadanej godzinie, ale tylko w środy i piątki oraz w dniu ćwiczeń
> ![](media/image8.png)
>
> Zadanie crona:
>
> ![](media/image9.png)
>
> Sprawdzenie:
>
> ![](media/image10.png)
e)  uruchomienie skryptu skrypt4.sh zbierającego statystyki pracy karty
    sieciowej do pliku graficznego z ostatnich 5 minut o zadanej
    godzinie, ale tylko w środy i piątki oraz w dniu ćwiczeń
> ![](media/image11.png)
>
> ![](media/image12.png)
>
> Sprawdzenie, ściągamy plik ze stacji windows programem winscp:
>
> ![](media/image13.png)
>
> Otworzyć plik w eksploratorze windows:
>
> ![](media/image14.png)
f)  ![](media/image15.png)
    uruchomienie skryptu arch_mysql.sh o
    zadanej godzinie, każdego 28 i 14 dnia miesiąca oraz w każdą środę,
    który wykona kopię zapasowa bazy mysql w katalogu /tmp.
> ![](media/image16.png)
>
> ![](media/image17.png)
>
> ![](media/image18.png)
>
> ![](media/image19.png)
>
> ![](media/image20.png)
g)  uruchomienie skryptu restart.sh przy każdym restarcie serwera, który
    wyśle maila z powiadomieniem
h)  wyślij mail do siebie każdego dnia 5 minut po północy.
<!-- -->
10. Sprawdź zadania crontab wszystkich użytkowników
![](media/image21.png)
11. Z pomocą polecenia at zaplanuj zadania wykonane wcześniej dla crona.
12. ![](media/image22.png)
    Utwórz plik testat za 1 minutę:
13. Utwórz skrypt o nazwie arch.sh, który kopiuje zawartość katalogu
    \~/at_crontab/dane do katalogu \~/at_crontab/kopie.
14. ![](media/image23.png)
    Sprawdź zawartość katalogu
    /var/spool/cron/atjobs/
15. Utwórz skrypt o nazwie zmiana.sh, który zmieni nazwę pliku test2.txt
    na nowy.txt, przetestuj jego działanie, a następnie zaplanuj
    uruchomienie 22 i 23 grudnia, 5 minut po godzinie 12
16. Zaplanuj uruchomienie skryptu kom1.sh tylko w lutym, marcu,kwietniu
    i wrześniu o godzinie 11:30,
ale tylko we wtorki i czwartki.
17. Z pomocą polecenia at zaplanuj:
<!-- -->
a)  ![](media/image24.png)
    ![](media/image25.png)
    ![](media/image26.png)
    utwórz skrypt o nazwie
    zajetosc_dysku.sh, który tworzy plik na dysku z raportem o zajętości
    miejsca na dysku. Przetestuj jego działanie, a następnie zaplanuj
    jego uruchomienie podając godzinę, minuty i dzień tygodnia.
    Wykorzystaj narzędzie duf.
> ![](media/image27.png)
>
> Skrypt:
>
> ![](media/image28.png)
>
> ![](media/image29.png)
18. Sprawdź jakie prawa posiadają pliki at, crontab.
19. Zezwól na używanie polecenia at sobie, a zabroń używania go
    użytkownikowi Blazej.
![](media/image30.png)
20. ![](media/image31.png)
    Zezwól na używanie polecenia crontab sobie, a
    zabroń używania go użytkownikowi blazej.
> ![](media/image32.png)
21. Dodatkowe zadania:
<!-- -->
a)  Wykonaj kopię zapasową bazy postgresql z pomocą crontab
> Instalacja: apt install postgresql -y
>
> ![](media/image33.png)
>
> ![](media/image34.png)
>
> Utworzenie pliku .pgpass:
>
> ![](media/image35.png)
>
> Crontab:
>
> ![](media/image36.png)
>
> ![](media/image37.png)
b)  Wykonaj kopię zapasową bazy MongoDB z pomocą at
c)  przetestuj polecenie at w Windows Server.
d)  inne podane przez nauczyciela
<!-- -->
22. *sudo poweroff* ( na koniec zajęć)
