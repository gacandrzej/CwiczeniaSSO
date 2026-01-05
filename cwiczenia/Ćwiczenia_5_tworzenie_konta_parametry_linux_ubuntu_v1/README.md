Ćwiczenia 5 -- Ubuntu serwer -- tworzenie i modyfikacja konta
Zaloguj się na swoje konto imienXYZ, gdzie XYZ oznacza kod klasy i
grupy, np. jank3t1
Jeśli nie masz konta, sudo adduser imienXYZ
1.  Dodaj swoje konto do grupy sudo: *sudo usermod twoje_konto -G sudo*
2.  Sprawdzenie czy jesteśmy w grupie sudo: *id konto*
3.  Utwórz katalog \~/konta i przejdź do niego
4.  Założyć grupę www1 o numerze 765.
![](media/image1.png)
5.  Utworzyć jednym poleceniem konto o nazwie webadmin1 o następujących
    cechach:
<!-- -->
a)  powłoka sh
b)  katalog domowy /home/web/webadmin1
c)  komentarz: webmaster 1
d)  numer użytkownika (uid) równy 601
e)  grupa początkowa: users
f)  grupy dodatkowe: www1, sudo
<!-- -->
6.  Sprawdź czy konto powstało: id webadmin1, cat /etc/passwd.
![](media/image2.png)
7.  Ustaw hasło dla webadmin1:
![](media/image3.png)
8.  Zaloguj się na konto webadmin1, wydaj komendy: pwd i ls -al. Wyloguj
    się.
![](media/image4.png)
9.  Zmień powłokę użytkownika webadmin1 na bash, a następnie sprawdź
    modyfikację:
![](media/image5.png)
10. Zaloguj się na konto webadmin1, wydaj komendy: id oraz pwd. Wyloguj
    się.
![](media/image6.png)
11. Sprawdzić, które powłoki są w systemie:
![](media/image7.png)
12. Sprawdź gdzie znajduje się powłoka nologin:
![](media/image8.png)
13. Zmień powłokę użytkownika webadmin1 na nologin. Spróbuj zalogować
    się na konto webadmin1.
![](media/image9.png)
14. Zmień powłokę użytkownika webadmin1 na bash.
![](media/image10.png)
15. Usuń konto webadmin1 z systemu z jednoczesnym skasowaniem jego
    plików
![](media/image11.png)
16. ![](media/image12.png)
    Poprawne polecenie zakladające konto z wszystkimi
    parametrami zapisz do pliku zaloz_konto.sh
17. ![](media/image13.png)
    Sprawdź zawartość pliku
    zaloz_konto.sh, dokonaj ewentualnie poprawki.
18. Sprawdź poprawność usunięcia konta.
![](media/image14.png)
19. Nadaj prawo wykonania dla właściciela pliku zaloz_konto.sh.
![](media/image15.png)
20. Uruchom skrypt zaloz_konto.sh poleceniem:
![](media/image16.png)
21. Sprawdź czy konto powstało: id webadmin1, cat /etc/passwd.
![](media/image17.png)
22. *sudo poweroff* ( na koniec zajęć)
