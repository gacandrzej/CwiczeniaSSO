# Ćwiczenia 5 -- Ubuntu serwer -- tworzenie i modyfikacja konta

💡Zaloguj się na swoje konto imienXYZ, gdzie XYZ oznacza kod klasy i
grupy, np. jank3t1
Jeśli nie masz konta, sudo adduser imienXYZ

1. Dodaj swoje konto do grupy sudo: *

   ```bash
   sudo usermod twoje_konto -G sudo
   ```
1. Sprawdzenie czy jesteśmy w grupie sudo:

   ```bash
   id konto
   ```

1. Utwórz katalog \~/konta i przejdź do niego
2. Założyć grupę www1 o numerze 765.
![image1](media/image1.png)
3. Utworzyć jednym poleceniem konto o nazwie webadmin1 o następujących
    cechach:
<!-- -->
a)  powłoka sh
b)  katalog domowy /home/web/webadmin1
c)  komentarz: webmaster 1
d)  numer użytkownika (uid) równy 601
e)  grupa początkowa: users
f)  grupy dodatkowe: www1, sudo
<!-- -->
1. Sprawdź czy konto powstało: id webadmin1, cat /etc/passwd.
![image2](media/image2.png)
2. Ustaw hasło dla webadmin1:
![image3](media/image3.png)
3. Zaloguj się na konto webadmin1, wydaj komendy: pwd i ls -al. Wyloguj
    się.
![image4](media/image4.png)
4. Zmień powłokę użytkownika webadmin1 na bash, a następnie sprawdź
    modyfikację:
![image5](media/image5.png)
5. Zaloguj się na konto webadmin1, wydaj komendy: id oraz pwd. Wyloguj
    się.
![image6](media/image6.png)
6. Sprawdzić, które powłoki są w systemie:
![image7](media/image7.png)
7. Sprawdź gdzie znajduje się powłoka nologin:
![image8](media/image8.png)
8. Zmień powłokę użytkownika webadmin1 na nologin. Spróbuj zalogować
    się na konto webadmin1.
![image9](media/image9.png)
9. Zmień powłokę użytkownika webadmin1 na bash.
![image10](media/image10.png)
10. Usuń konto webadmin1 z systemu z jednoczesnym skasowaniem jego
    plików
![image11](media/image11.png)
11. ![image12](media/image12.png)
    Poprawne polecenie zakladające konto z wszystkimi
    parametrami zapisz do pliku zaloz_konto.sh
12. ![image13](media/image13.png)
    Sprawdź zawartość pliku
    zaloz_konto.sh, dokonaj ewentualnie poprawki.
13. Sprawdź poprawność usunięcia konta.
![image14](media/image14.png)
14. Nadaj prawo wykonania dla właściciela pliku zaloz_konto.sh.
![image15](media/image15.png)
15. Uruchom skrypt zaloz_konto.sh poleceniem:
![image16](media/image16.png)
16. Sprawdź czy konto powstało: id webadmin1, cat /etc/passwd.
![image17](media/image17.png)
17. *sudo poweroff* ( na koniec zajęć)
