## 1 JavaScript — obecně

JavaScript (JS) je skriptovací programovací jazyk.

Používá se například pro:

- interaktivní webové stránky,
- reakci na kliknutí a jiné události,
- změnu obsahu stránky bez jejího znovunačtení,
- kontrolu formulářů,
- práci s DOM,
- komunikaci se serverem,
- backend pomocí Node.js.

### Základní vlastnosti

- dynamické typování,
- automatická správa paměti pomocí garbage collectoru,
- objektový, procedurální i funkcionální přístup,
- běží například v prohlížeči nebo přes Node.js.


Proměnná může během programu obsahovat jiný datový typ.

---

## 2 Způsoby připojení JS kódu:
1. V souboru `.html`
```html
<script> JS-kód </script>
```
2) Externí soubor `name.js` s připojenou cestou v `head`
```html
<script src="name.js"></script>
```
---

## 3 Proměnné
> [!IMPORTANT]
> V JavaScriptu je typ proměnné určen dynamicky, takže se určí podle hodnoty, kterou do proměnné ukládáme. <br>
> Stejnou proměnnou lze použít pro uložení jak řetězce, tak i celého čísla.


```javascript
let name = value;
```

Používá se pro proměnnou, jejíž hodnota se může měnit.

- dostupná pouze v rozsahu bloku `{}` v němž byla deklarována
<br><br>
---

```javascript
var name = value;
```

- Starší způsob deklarace proměnné.
- "Globální proměná"
- má rozsah funkce, ne bloku,
- pokud není při deklaraci zadána hodnota, je hodnota `undefined`

 > [!IMPORTANT]
 > `var` není „globální proměnná“ samo o sobě. Může být globální, pokud je deklarována mimo funkci.

---

### Konstanta

```javascript
const name = value;
```

- <font color="red">musí být inicializována hned při deklaraci!</font>
- je konstantní, takže se po inicializaci nedá změnit.
- má blokový rozsah.

---

### 3,1 Převedení textu na číslo
1) Příkaz `parseTypProměnné`
- zaokrouhlení na celé číslo (int): <font color="red">ignoruje hodnoty za desetinnou čárkou</font> 
```javascript
parseInt("cislo_textem"); // místo int se dají použít i jiné typy proměnných
```

2) Vynásobení jedničkou
- převede řetězec na desetinné číslo
```javascript
1 * "3.14159"
```
---

### 3,2 Zaokrouhlování
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
- zaokrouhlení čísla na `x` desetinných míst pomoci `toFixed`
    - <ins>vrácí textovou hodnotu </ins>`string`! 
```javascript
(3.2791).toFixed(2); // výsledek: "3.28"
```
```javascript
parseFloat((3.2791).toFixed(2)); // s převodem na Float 
```
---

### 3,3 Náhodná čísla
- generuje v intervalu [0 ; max]
```javascript
let nahodneCislo = Math.floor(Math.random() * (max + 1));
```

- generuje v intervalu [min ; max]
```javascript
let nahodneCislo = Math.floor(Math.random() * (max + 1 - min)) + min;
```

> [!NOTE]
> Samotný `Math.random()` vrací náhodné desetiné číslo v intervalu `[0 ; 1)`.


---
## 4 Vyhledávání prvků v dokumentu HTML

Obvykle si prvek uložíme do proměnné:

```javascript
let promena = document.getElementById("ID");
```
 > [!IMPORTANT]
 > Vždy pokud prvek neexistuje vráci `null`

### 4.1 Podle `id`

```javascript
document.getElementById("ID");
```

vybere jeden konkrétní prvek,

---
### 4.2 `getElementsByClassName()`

Vybere prvky podle názvu třídy.

```javascript
document.getElementsByClassName("green");
```

Výsledkem může být více prvků.

---

### 4.3 `getElementsByTagName()`

Vybere všechny prvky daného typu značky.

```javascript
document.getElementsByTagName("p");
```

Vybere všechny `<p>`.

---

### 4.4 `querySelector()`

Vybere **první** prvek odpovídající CSS selektoru.

```javascript
document.querySelector("#id");
document.querySelector(".class");
document.querySelector("tag");
```

Používá CSS zápis:

- `#id`
- `.class`
- `tag`

---

### 4.5 `querySelectorAll()`

Vybere **všechny** odpovídající prvky.

```javascript
document.querySelectorAll(".class");
```

Například všechny odstavce s třídou `green`:

```javascript
document.querySelectorAll("p.green");
```

---

## 5 Čtení a změná s `textContent` 
      
Slouží ke čtení nebo změně textu prvku.

```javascript
let odpoved = document.getElementById("odpovedOut");
odpoved.textContent = "Ahoj!";
```

HTML:

```html
<p id="odpovedOut"></p>
```

Po provedení JS bude uvnitř:

```html
<p id="odpovedOut">Ahoj!</p>
```

---

### Čtení pomocí `textContent`

```javascript
let text = odpoved.textContent;
```

---


