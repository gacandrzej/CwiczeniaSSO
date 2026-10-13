# Ćwiczenia 17 -- konfiguracja quoty na ubuntu serwer

Praca na stacji windows z programem virtualbox

1. Zaimportuj w virtualbox na stacji windows plik ubuntu_server1 do
    QUOTY 1600x1200.ova ( ctrl+i )

2. Sklonuj zaimportowaną maszynę.

3. Dla klona zmień nazwę na twoje imię.

4. Uruchom zaimportowaną maszynę wirtualną nazwaną twoim imieniem.
    Możesz poprawić widok → tryb przeskalowany.

5. Sprawdź układ partycji na dysku, w szczególności czy /home jest na
    osobnej partycji, np.

    ```bash
    lsblk 
    blkid
    ```

6. Zainstaluj quotę:

    ```bash
    sudo apt install quota quotatool -y 
    dpkg --configure -a
    ```

7. Ustaw hasło dla konta root i zaloguj się na nie.

8. Usuń konto administratora.

9. Odmontuj katalog home:

    ```bash
    umount /home
    ```

10. vi /etc/fstab

    ![image1](media/image1.png)

11. Zamontuj katalog home:

    ```bash
    sudo mount -o usrquota,grpquota /dev/sda2 /home
    ```

12. Włącz quotę dla katalogu home:

    ```bash
    quotacheck -ugm /home
    ```

13. Zreastartuj serwer.

14. Wyświetl staus poleceniem:

    ```bash
    quotaon -ap
    ```

    ![image2](media/image2.png)

15. Skonfiguruj quotę dla dwóch użytkowników
    - Zosi na 25MB
    - Marka na 20MB

16. Na kontach Zosia i Marek poleceniem quota możesz sprawdzić aktualne
    przydziały.

17. Wyświetl raport:

    ![image3](media/image3.png)

18. Sprawdź przekroczenie quoty:

    ![image4](media/image4.png)

19. Zainstaluj pakiet mailutils, odpowiedź tylko lokanie.

20. Wydaj komendę warnquota.

21. Sprawdź mail z ostrzeżeniem o przekroczeniu quoty:

    ![image5](media/image5.png)

22. Zawartość maila

    ![image6](media/image6.png)

23. Spróbuj ustawić quotę dla użytkownika wojtek za pomocą polecenia:

    ```bash
    setquota -ua soft hard 0 0.
    ```

24. Zmień domyślny czas dla quoty na 10 dni, np.:

    ```bash
    setquota -t 864000.
    ```

25. Stwórz quotę dla grupy **users**, która istnieje w systemie.

26. Stwórz konto o nazwie blazej dodając je na etapie tworzenia do grupy
    users.

27. Sprawdzić działanie quoty tworząc duży plik.

28. Sprawdź logi i maila.

29. KONIEC. 😀
