# Konfiguracja podstawowa

## Nazwa serwera

`serverX` za X wstaw numer stanowiska

## Licencja

Gdy mamy dostęp na serwerze do internetu:

```bash
slmgr -rearm
```

Restart serwera.

## Karty sieciowe

### Górna

| pole  | zawartość     |
| ----: | :------------ |
| Nazwa |  wan          |
| Ip    | 172.18.19.2   |
| Maska | 255.255.255.0 |
| Bramka| 172.18.19.1   |
| DNS 1 | 8.8.8.8       |
| DNS 2 | 8.8.4.4       |

### Dolna (TP-Link)

| pole     | zawartość       |
|---------:|:----------------|
| Nazwa    |  lan            |
| Ip       | 10.9.8.1        |
| Maska    | 255.255.255.192 |
| Bramka   | brak            |
| DNS 1    | 10.9.8.1        |

## Instalacja AD

dla domeny: `zsmeie.abcd`
