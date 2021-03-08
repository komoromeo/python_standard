# Alapok

<!--Ami nincs benne az Google, ami abba sincs benne, az PEP8, linkek?-->

## Moduláris kód

Az egyes függvények olyanok, mint az építőkockák, amiket be lehet hívni és össze lehet fűzni különböző módokon. Az "építőkocka" függvények belsejét nem írjuk át, azokat paraméterezzük.

Hüvelykujj szabály: Ha egy kódrészlet több mint egyszer jelenik meg a kódban (még ha más paraméterekkel is), írj rá egy függvényt. Ez főleg hosszabb kódrészletekre vonatkozik.

## Felhasználó bázis

Alapvetően kétféle felhasználó használja ezeket a kódokat.

 - Kódoló: alacsony szinten nyúl bele a kódba, ismeri az alapvető függvényeket, és kezeli ezeknek minden paraméterér, ezeket szerkeszti, ezekhez wrappereket ír, és folyamatokká fűzi őket össze. Számukra a kód és a dokumentáció angolul van.
 - Futtató: az alacsony szintű függvényeket nem ismeri, a kódot csak magas szinten kezeli wrapperek és parancsok révén, limitált számú paraméterhez fér hozzá. Számukra a dokumentáció magyarul van.

<!--filozófiák-->

# Szkript felépítése

Egy szkript általános felépítése.

1. Modul Docstring
2. importok `import module`
3. Változók és konstansok `my_var` és `MY_CONST`
4. Osztályok `class MyClass:`
5. Függvények `def my_func(arg1, arg2, arg3):`

## Kód formázása

- sorhossz: 120 karakter (a sorvégi komment ebből kilóghat)
- behúzás: 4 szóköz
- kommentek: leírás 3#, kikommentelt sorok 1# <!--!?* etc-->
- Kód blokkok közötti térköz: 1 sor
- idézőjelek: <!--ki kell találni-->

Hosszú listák, dictinary-k és függvény argumentumok.

```python
my_dict = {
    'a': 1, # Az egyes értékek kommentelhetőek is
    'b': 2,
    'c': 3, # Ha sokat változtatjuk a listát, a végén is érdemes vesszőt hagyni
}
```

<!--külön változó nevekről-->

<!--docstring formátum gyorsban-->

A függvényeknek két típusa van, ezek egymásra épülnek.

- Alap függvény: Sokféleképpen paraméterezhető, egy dolgot csinál egy dologra fut le.
- Wrapper: Egy alap függvényt bizonyos módon futtat. Összefűz több függvényt, kiír valamit, loopol egy függvényt, elabsztraktálja a nem fontos paramétereket. Akár több rétegben is.

<!--üzik, errorok-->

<!--return none kitevése függvények végére?-->

# Kódbázis felépítése

A szkripteknek három típusa van, ezek nagyjából megfeleltethetőek a függvénytípusoknak.

| Szkript típusa | Utótag | Tartalma                                                     |
| -------------- | ------ | ------------------------------------------------------------ |
| definition     | def    | Alap függvények és az ezekkel gyakran használt wrapperek.    |
| wrapper        | wrp    | A specifikusan az adott folyamatban használt wrapperek.      |
| runner         | run    | Az adott folyamat futását bonyolító paraméterek és pár sor kód. |

# Fájlok

<!--névkonvenciók, fájltípusok-->

Kis folyamat memóriába dolgozik (gyorsabb), nagy folyamat fájlokat ír ki (biztonságos)

<!--paraméterfájlok `par` utótaggal-->

Paraméterek

- **Függvény ARG:** Ha csak egy egyszerű érték. Ilyenkor nem érdemes paraméter fájllal vesződni. Ha be tudjuk adni a programunknak, strukturáltabb paramétereknél is érdemes megfontolni.
- **TXT fájl:** Ha egyszerű lista vagy dict és ember is belenyúl.
- **JSON fájl:** Ha strukturáltabb, több, egymásba ágyazott listát és dictet tartalmaz, illetve csak szkriptek nyúlnak bele.

## Kép fájlok

<!--névkonvenció-->

<!--külső dokumentáció?-->

# Egy példa szkript

``` python
"""Short description for the moule. This should be one line.

Longer description...
...this can go on and on.

Examples:
    Short description for an example.

        $ python example.py -h

    Short description for another example.

        $ python example.py a b c

Todo:
    * A task
    * Another task
    * Yet another task

"""

import os
import sys
from pathlib import Path

import numpy as np

MY_GLOBAL_CONST = None ### Constants are set before runtime and do not change
my_global_var = None ### Variables can be assigned and reassigned during runtime

class MyClass:
    """Short description for the class. This should be one line.

    Longer description...
    ...this can go on and on.

    Args:
        a (int): First arg for the __init__ function.
        b (str): Second arg for the __init__ function.

    Attributes:
        alpha (int): Attribute of the class instance.
        beta (str): Another attribute of a class instance.
    """

    pass

def my_func_with_params(a, b, c, d):
    """Short description for the function. This should be one line.

    Longer description...
    ...this can go on and on.

    Args:
        a (int): First arg of the function.
        b (int): Second arg of the function.
        c (int): Third arg of the function.
        d (int): Fourth arg of the function.

    Returns:
        None
    """

    pass

def my_func_with_returns():
    """Short description for the function. This should be one line.

    Longer description...
    ...this can go on and on.

    Returns:
        x (int): First return of the Function.
        y (int): Second return of the function.
    """
    
    pass
```
