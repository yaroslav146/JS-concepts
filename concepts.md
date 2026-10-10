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

## 3 Výstup v JavaScriptu

### 3.1 `console.log()`

Vypíše text do vývojářské konzole.

```javascript
console.log("text");
```

Používá se hlavně pro kontrolu programu a hledání chyb.

### 3.2 `console.error()`

Vypíše chybu do konzole.

```javascript
console.error("Allert");
```

### 3.3 `alert()`

Zobrazí jednoduché upozornění.

![alert](/images/alert.png)
```javascript
alert("Ahoj!");
```

---

### 3.4 `prompt()`

Zeptá se uživatele na hodnotu.

![prompt](/images/prompt.png)
```javascript
let jmeno = prompt("Jak se jmenuješ?");
```

> [!WARNING]
> Hodnota získaná přes `prompt()` je text (`string`), takže pro výpočty ji obvykle musíme převést na číslo.

Například:

```javascript
let cislo = parseFloat(prompt("Zadej číslo:"));
```

---



## 4 Proměnné
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

### 4.1 Konstanta

```javascript
const name = value;
```

- <font color="red">musí být inicializována hned při deklaraci!</font>
- je konstantní, takže se po inicializaci nedá změnit.
- má blokový rozsah.

---

### 4.2 Převedení textu na číslo
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

### 4.3 Zaokrouhlování
1) zaokrouhlení dolů na celé číslo `.floor`
```javascript
Math.floor(desetinne_cislo);
```
2) zaokrouhlení nahoru na celé číslo `.ceil`
```javascript
Math.ceil(desetinne_cislo);
```
3) zaokrouhlení čísla na `x` desetinných míst
```javascript
Math.round(desetinne_cislo * (x ** 10)) / (x ** 10)
```
4) zaokrouhlení čísla na `x` desetinných míst pomoci `toFixed`
    - <ins>vrácí textovou hodnotu </ins>`string`! 
```javascript
(3.2791).toFixed(2); // výsledek: "3.28"
```
```javascript
parseFloat((3.2791).toFixed(2)); // s převodem na Float 
```
---

### 4.4 Náhodná čísla
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
## 5 Vyhledávání prvků v dokumentu HTML

Obvykle si prvek uložíme do proměnné:

```javascript
let promena = document.getElementById("ID");
```
 > [!IMPORTANT]
 > Vždy pokud prvek neexistuje vráci `null`

### 5.1 `id`

```javascript
document.getElementById("ID");
```

vybere jeden konkrétní prvek,

---
### 5.2 `getElementsByClassName()`

Vybere prvky podle názvu třídy.

```javascript
document.getElementsByClassName("green");
```

Výsledkem může být více prvků.

---

### 5.3 `getElementsByTagName()`

Vybere všechny prvky daného typu značky.

```javascript
document.getElementsByTagName("p");
```

Vybere všechny `<p>`.

---

### 5.4 `querySelector()`

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

### 5.5 `querySelectorAll()`

Vybere **všechny** odpovídající prvky.

```javascript
document.querySelectorAll(".class");
```

Například všechny odstavce s třídou `green`:

```javascript
document.querySelectorAll("p.green");
```

---

## 6 Čtení a změná s `textContent` 
      
Slouží ke čtení nebo změně textu prvku.

### 6.1 vypís pomocí `textContent`
```javascript
let odpoved = document.getElementById("odpovedOut");
odpoved.textContent = "Ahoj!";
```

```html
<p id="odpovedOut"></p>    >>>   <p id="odpovedOut">Ahoj!</p>
```

---

### 6.2 Čtení pomocí `textContent`

```javascript
let text = odpoved.textInput;
```

---

## 7 Čtení a změná s `innerHTML`

<ins>Čte prvek jako **html** kod.</ins>

```javascript
prvek.innerHTML = "<b>Ahoj!</b>";
```

Text `Ahoj!` se zobrazí tučně.

Můžeme vložit i více HTML prvků:

```javascript
prvek.innerHTML = "<ul><li>Jedna</li><li>Dva</li></ul>";
```
--- 
Hlávní rozdíl mezi `textContent` je právě čteni html kodu

takže 
```javascript
prvek.textContent = "<b>Ahoj</b>";
```

Se zobrazí doslova jako `<b>Ahoj</b>`

---

## 8 Vlastnost `.value`

Používá se u formulářových prvků, např.:

- `<input>`
- `<select>`
- `<textarea>`

Vlastnost .value – <ins>slouží k získání nebo změně hodnoty formulářového prvku</ins> bez ní získáme samotný HTML prvek místo hodnoty zadané uživatelem


```html
<input type="number" id="cisloIn"> <!-- html --> 
```
⬇⬇⬇
```javascript
let cislo = document.getElementById("cisloIn").value;
```

> Hodnota `.value` je běžně **text (`string`)**, i když má `<input>` `type="number"`.

Proto se často používá:

```javascript
let cislo = parseInt(document.getElementById("cisloIn").value); 
```

---

## 9 Změna CSS přes JS 
Vzorec: 
```javascript
prvek.style.CSScommand = "CSSvalue";
```

Příklad z ověrování hesla[^1]:

[^1]: https://github.com/yaroslav146/formular-JS/blob/main/index.html

```javascript
formular.style.display = "none"; // skryje formular
```






