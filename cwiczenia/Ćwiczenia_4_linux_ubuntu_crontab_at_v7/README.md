# Ćwiczenia 4 -- Ubuntu serwer -- crontab, at

Zaloguj się na swoje konto `imienXYZ`, gdzie `XYZ` oznacza kod klasy i
grupy, np. jank3t1
Jeśli nie masz konta,

```bash
sudo adduser imienXYZ
```

1. Dodaj swoje konto do grupy sudo:

    ```bash
    sudo usermod twoje_konto -G sudo
    ```

    lub

    ```bash
    sudo adduser imienXYZ sudo
    ```

1. Sprawdzenie czy jesteśmy w grupie sudo:

   ```bash
   id konto
   ```

1. Wydaj komendę na piątym terminal:

   ```bash
   man at
   ```

1. Wydaj komendę na szóstym terminalu:

    ```bash
    info crontab
    ````

1. Otwórz pomocniczo na czwartym terminal:

    ```bash
    cat /etc/crontab
    ```

   ![img.png](media/image5_1.png)

1. Otwórz stronę pomocy, np.: <https://crontab.guru/>

1. Zainstaluj obsługę poczty, podaj tylko lokanie:

    ```bash
    sudo apt install mailutils 
    ```

1. Sprawdzić pocztę komendą:

    ```bash
    mail
    ```

1. Z pomocą polecenia crontab zaplanuj:

    a)  Archiwizuj swój katalog domowy co 1
        minutę do katalogu ***/var/backups*** oraz ***/tmp*** z użyciem narzędzia `tar` i `gzip`.  
      Wybór edytora po `crontab -e` można powtórzyć poleceniem `select-editor`

    ![image1](media/image1.png)

    b)  Utwórz co 1 minutę podając dzień i miesiąc plik o nazwie
        plikcrontabtest w \~

    ![image2](media/image2.png)

    c)  Uruchom skrypt co 1 minutę w każdy dzień roboczy pobierający wycenę
        bitcoina ze strony:

    <https://docs.cdp.coinbase.com/coinbase-app/track-apis/prices>

    ```bash
    curl https://api.coinbase.com/v2/prices/spot?currency=USD
    ```

    ![image3](media/image3.png)

    ```bash
    jason=$(curl https://api.coinbase.com/v2/prices/spot\?currency\=USD)
    ```

    ```bash
    jq -r '.data.amount' <<< $jason
    ```

    ![image4](media/image4.png)

    ![image5](media/image5.png)

    Efekt działania:

    ![image6](media/image6.png)
    d)  uruchomienie skryptu skrypt3.sh
        zbierającego statystyki pracy karty sieciowej z ostatnich 5 minut o
        zadanej godzinie, ale tylko w środy i piątki oraz w dniu ćwiczeń.  
        Najpierw zainstaluj potrzebne pakiety:

    ```bash
    sudo apt install vnstat vnstati -y
    ```

    ![image7](media/image7.png)

    ![image8](media/image8.png)

    Zadanie crona:

    ![image9](media/image9.png)

    Sprawdzenie:

    ![image10](media/image10.png)

    e)  uruchomienie skryptu skrypt4.sh zbierającego statystyki pracy karty
        sieciowej do pliku graficznego z ostatnich 5 minut o zadanej
        godzinie, ale tylko w środy i piątki oraz w dniu ćwiczeń
    ![image11](media/image11.png)

    ![image12](media/image12.png)

    Sprawdzenie, ściągamy plik ze stacji windows programem winscp:

    ![image13](media/image13.png)

    Otworzyć plik w eksploratorze windows:

    ![image14](media/image14.png)

    f)  uruchomienie skryptu arch_mysql.sh o
        zadanej godzinie, każdego 28 i 14 dnia miesiąca oraz w każdą środę,
        który wykona kopię zapasowa bazy mysql w katalogu ***/tmp***.

    ```bash
    sudo apt install mysql-server -y
    ```

    ![image15](media/image15.png)

    ![image16](media/image16.png)

    ![image17](media/image17.png)

    ![image18](media/image18.png)

    ![image19](media/image19.png)

    ![image20](media/image20.png)

    g)  uruchomienie skryptu restart.sh przy każdym restarcie serwera, który
        wyśle maila z powiadomieniem  

    h)  wyślij mail do siebie każdego dnia 5 minut po północy.  

1. Sprawdź zadania crontab wszystkich użytkowników

![image21](media/image21.png)

1. Z pomocą polecenia at zaplanuj zadania wykonane wcześniej dla crona.

2. Utwórz plik testat za 1 minutę:

    ![image22](media/image22.png)

3. Utwórz skrypt o nazwie arch.sh, który kopiuje zawartość katalogu
    ***\~/at_crontab/dane*** do katalogu ***\~/at_crontab/kopie***.

4. Sprawdź zawartość katalogu ***/var/spool/cron/atjobs/***

    ![image23](media/image23.png)

5. Utwórz skrypt o nazwie zmiana.sh, który zmieni nazwę pliku test2.txt
    na nowy.txt, przetestuj jego działanie, a następnie zaplanuj
    uruchomienie 22 i 23 grudnia, 5 minut po godzinie 12

6. Zaplanuj uruchomienie skryptu kom1.sh tylko w lutym, marcu,kwietniu
    i wrześniu o godzinie 11:30, ale tylko we wtorki i czwartki.

7. Z pomocą polecenia at zaplanuj:

a)  utwórz skrypt o nazwie
    zajetosc_dysku.sh, który tworzy plik na dysku z raportem o zajętości
    miejsca na dysku. Przetestuj jego działanie, a następnie zaplanuj
    jego uruchomienie podając godzinę, minuty i dzień tygodnia.
    Wykorzystaj narzędzie duf.
![image24](media/image24.png)
![image25](media/image25.png)
![image26](media/image26.png)

 ![image27](media/image27.png)

 Skrypt:

 ![image28](media/image28.png)

 ![image29](media/image29.png)

1. Sprawdź jakie prawa posiadają pliki at, crontab.

2. Zezwól na używanie polecenia at sobie, a zabroń używania go
    użytkownikowi Blazej.

![image30](media/image30.png)

1. Zezwól na używanie polecenia crontab sobie, a
    zabroń używania go użytkownikowi blazej.
    ![image31](media/image31.png)
 ![image32](media/image32.png)

2. Dodatkowe zadania:  

a)  Wykonaj kopię zapasową bazy postgresql z pomocą crontab  
    Instalacja:

```bash
 sudo apt install postgresql -y
```

 ![image33](media/image33.png)

 ![image34](media/image34.png)

 Utworzenie pliku .pgpass:

 ![image35](media/image35.png)

 Crontab:

 ![image36](media/image36.png)

 ![image37](media/image37.png)

b)  Wykonaj kopię zapasową bazy MongoDB z pomocą at

c)  przetestuj polecenie at w Windows Server.

d)  inne podane przez nauczyciela

1. Na koniec zajęć 😃

```bash
 sudo poweroff
```
