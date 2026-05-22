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

1. Założyć grupę www1 o numerze 765.

   ![image1](media/image1.png)

1. Utworzyć jednym poleceniem konto o nazwie webadmin1 o następujących
    cechach:

   - powłoka sh
   - katalog domowy /home/web/webadmin1
   - komentarz: webmaster 1
   - numer użytkownika (uid) równy 601
   - grupa początkowa: users
   - grupy dodatkowe: www1, sudo

1. Sprawdź czy konto powstało: id webadmin1, cat /etc/passwd.

   ![image2](media/image2.png)

1. Ustaw hasło dla webadmin1:

   ![image3](media/image3.png)

1. Zaloguj się na konto webadmin1, wydaj komendy: pwd i ls -al. Wyloguj
    się.

   ![image4](media/image4.png)

1. Zmień powłokę użytkownika webadmin1 na bash, a następnie sprawdź
    modyfikację:

   ![image5](media/image5.png)

1. Zaloguj się na konto webadmin1, wydaj komendy: id oraz pwd. Wyloguj
    się.

   ![image6](media/image6.png)

1. Sprawdzić, które powłoki są w systemie:

   ![image7](media/image7.png)

1. Sprawdź gdzie znajduje się powłoka nologin:

   ![image8](media/image8.png)

1. Zmień powłokę użytkownika webadmin1 na nologin. Spróbuj zalogować
    się na konto webadmin1.

   ![image9](media/image9.png)

1. Zmień powłokę użytkownika webadmin1 na bash.

   ![image10](media/image10.png)

1. Usuń konto webadmin1 z systemu z jednoczesnym skasowaniem jego
    plików

   ![image11](media/image11.png)

1. Poprawne polecenie zakladające konto z wszystkimi
    parametrami zapisz do pliku zaloz_konto.sh

   ![image12](media/image12.png)

1. Sprawdź zawartość pliku
    zaloz_konto.sh, dokonaj ewentualnie poprawki.

   ![image13](media/image13.png)

1. Sprawdź poprawność usunięcia konta.

   ![image14](media/image14.png)

1. Nadaj prawo wykonania dla właściciela pliku zaloz_konto.sh.

   ![image15](media/image15.png)

1. Uruchom skrypt zaloz_konto.sh poleceniem:

   ![image16](media/image16.png)

1. Sprawdź czy konto powstało: id webadmin1, cat /etc/passwd.

   ![image17](media/image17.png)

1. Na koniec zajęć:

   ```bash
   sudo poweroff
   ```
