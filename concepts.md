## Způsoby připojení JS kódu:
1. V souboru `.html`
```html
<script> JS-kód </script>
```
2) Externí soubor `name.js` s připojenou cestou v `head`
```html
<script src="name.js"></script>
```
---

## Proměnné
> [!IMPORTANT]
> V JavaScriptu je typ proměnné určen dynamicky, takže se určí podle hodnoty, kterou do proměnné ukládáme. <br>
> Stejnou proměnnou lze použít pro uložení jak řetězce, tak i celého čísla.

1) Lokální proměnná
- dostupná pouze v rozsahu bloku `{}` v němž byla deklarována
```javascript
let name = value;
```

2) Globální
- dostupná v jakékoli části programu, v níž byla deklarována
```javascript
var name = value;
```

3) Konstantní
- musí být inicializována hned při deklaraci!
- je konstantní, takže se po inicializaci nedá změnit.
```javascript
const name = value;
```
---

### Převedení textu na číslo
1) Příkaz `parseTypProměnné`
- zaokrouhlení na celé číslo (int): ignoruje hodnoty za desetinnou čárkou
```javascript
parseInt("cislo_textem"); // místo int se dají použít i jiné typy proměnných
```

2) Vynásobení jedničkou
- převede řetězec na desetinné číslo
```javascript
1 * "3.14159"
```
---

### Zaokrouhlování
- zaokrouhlí dolů na celé číslo
```javascript
Math.floor(desetinne_cislo);
```
- zaokrouhlí nahoru na celé číslo
```javascript
Math.ceil(desetinne_cislo);
```
- zaokrouhlení čísla na `x` desetinných míst
```javascript
Math.round(desetinne_cislo * (x ** 10)) / (x ** 10)
```
---

### Náhodná čísla
- generuje v intervalu [0 ; max]
```javascript
let nahodneCislo = Math.floor(Math.random() * (max + 1));
```

- generuje v intervalu [min ; max]
```javascript
let nahodneCislo = Math.floor(Math.random() * (max + 1 - min)) + min;
```


> [!NOTE]
> Samotný `Math.random()` vrací náhodné číslo od 0 do 1.
<<<<<<< HEAD

<!-- collaborator change  --> 
=======
hello Vasiya!
>>>>>>> ba29cec (add text)
