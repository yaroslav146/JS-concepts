## Navigace

- [1 JavaScript — obecně](#1-javascript--obecně)
- [2 Způsoby připojení JS kódu](#2-způsoby-připojení-js-kódu)
- [3 Výstup v JavaScriptu](#3-výstup-v-javascriptu)
  - [3.1 `console.log()`](#31-consolelog)
  - [3.2 `console.error()`](#32-consoleerror)
  - [3.3 `alert()`](#33-alert)
  - [3.4 `prompt()`](#34-prompt)
- [4 Proměnné](#4-proměnné)
  - [4.1 Konstanta](#41-konstanta)
  - [4.2 Převedení textu na číslo](#42-převedení-textu-na-číslo)
  - [4.3 Zaokrouhlování](#43-zaokrouhlování)
  - [4.4 Náhodná čísla](#44-náhodná-čísla)
- [5 Vyhledávání prvků v dokumentu HTML](#5-vyhledávání-prvků-v-dokumentu-html)
  - [5.1 `id`](#51-id)
  - [5.2 `getElementsByClassName()`](#52-getelementsbyclassname)
  - [5.3 `getElementsByTagName()`](#53-getelementsbytagname)
  - [5.4 `querySelector()`](#54-queryselector)
  - [5.5 `querySelectorAll()`](#55-queryselectorall)
- [6 Čtení a změna pomocí `textContent`](#6-čtení-a-změna-pomocí-textcontent)
  - [6.1 Výpis pomocí `textContent`](#61-výpis-pomocí-textcontent)
  - [6.2 Čtení pomocí `textContent`](#62-čtení-pomocí-textcontent)
- [7 Čtení a změna pomocí `innerHTML`](#7-čtení-a-změna-pomocí-innerhtml)
- [8 Vlastnost `.value`](#8-vlastnost-value)
- [9 Změna CSS přes JS](#9-změna-css-přes-js)
- [10 Podmínky v JS](#10-podmínky-v-js)
  - [10.1 `if + else if + else`](#101-vzorec-if--else-if--else)
  - [10.2 `switch ... case`](#102-vzorec-switch--case)
  - [10.3 Porovnávací operátory](#103-porovnávací-operátory)
  - [10.4 Logické operátory](#104-logické-operátory)
- [11 Cykly](#11-cykly)
  - [11.1 `for`](#111-for)
  - [11.2 `while`](#112-while)
  - [11.3 `do ... while`](#113-do--while)
  - [11.4 `break` a `continue`](#114-break-a-continue)
- [12 Funkce](#12-funkce)
  - [12.1 Volání funkce](#121-volání-funkce)
  - [12.2 Parametr funkce](#122-parametr-funkce)
  - [12.3 Návratová hodnota `return`](#123-návratová-hodnota-return)
- [13 HTML – formulářové prvky](#13-html--formulářové-prvky)
  - [13.1 `input`](#131-input)
  - [13.2 Základní atributy](#132-základní-atributy)
  - [13.3 Typy `input`](#133-typy-input)

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
console.error("chyba");
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

- dostupná pouze v rozsahu bloku `{}`, v němž byla deklarována
<br><br>
---

```javascript
var name = value;
```

- Starší způsob deklarace proměnné.
- "Globální proměnná"
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
4) zaokrouhlení čísla na `x` desetinných míst pomocí `toFixed`
    - <ins>vrací textovou hodnotu </ins>`string`!
```javascript
(3.2791).toFixed(2); // výsledek: "3.28"
```
```javascript
parseFloat((3.2791).toFixed(2)); // s převodem na Float 
```
---

### 4.4 Náhodná čísla
- Generuje náhodné celé číslo v intervalu [0 ; max].
```javascript
let nahodneCislo = Math.floor(Math.random() * (max + 1));
```

- Generuje náhodné celé číslo v intervalu [min ; max].
```javascript
let nahodneCislo = Math.floor(Math.random() * (max + 1 - min)) + min;
```

> [!NOTE]
> Samotný `Math.random()` vrací náhodné desetinné číslo v intervalu `[0 ; 1)`.


---
## 5 Vyhledávání prvků v dokumentu HTML

Obvykle si prvek uložíme do proměnné:

```javascript
let promena = document.getElementById("ID");
```
 > [!IMPORTANT]
 > Pokud prvek neexistuje, vrátí `null`.

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

Používá zápis CSS:

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

## 6 Čtení a změna pomocí `textContent`
      
Slouží ke čtení nebo změně textu prvku.

### 6.1 Výpis pomocí `textContent`
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
let text = odpoved.textContent;
```

---

## 7 Čtení a změna pomocí `innerHTML`

<ins>Čte prvek jako **HTML** kód.</ins>

```javascript
prvek.innerHTML = "<b>Ahoj!</b>";
```

Text `Ahoj!` se zobrazí tučně.

Můžeme vložit i více HTML prvků:

```javascript
prvek.innerHTML = "<ul><li>Jedna</li><li>Dva</li></ul>";
```
--- 
Hlavní rozdíl spočívá v tom, že `innerHTML` čte HTML kód.

Takže
```javascript
prvek.textContent = "<b>Ahoj</b>";
```

Zobrazí se doslova jako `<b>Ahoj</b>`.

---

## 8 Vlastnost `.value`

Používá se u formulářových prvků, např.:

- `<input>`
- `<select>`
- `<textarea>`

Vlastnost `.value` <ins>slouží k získání nebo změně hodnoty formulářového prvku</ins>. Bez ní získáme samotný HTML prvek místo hodnoty zadané uživatelem.


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

Příklad z ověřování hesla[^1]:

[^1]: https://github.com/yaroslav146/formular-JS/blob/main/index.html

```javascript
formular.style.display = "none"; // skryje formulář
```

---

## 10 Podmínky v JS

**Podmínka** – logický výraz, který může nabývat dvou stavů (`true` nebo `false`).

### 10.1 Vzorec `if + else if + else`
```javascript
if (podminka1){
    // Provede se, pokud podmínka1 vrátí true.
}
else if (podminka2){
    // Provede se, pokud podmínka1 vrátí false a podmínka2 vrátí true.
}
else {
    // Provede se, pokud ani jedna z předchozích podmínek nevrátí true.
}
```
---
### 10.2 Vzorec `switch ... case`
```javascript
switch (hodnota) {
    case moznost1:
        // kód
        break;

    case moznost2:
        // kód
        break;

    default:
        // žádná možnost neodpovídá
}
```

---
### 10.3 Porovnávací operátory
| Operátor | Význam |
| --- | --- |
| `==` | rovnost, s převodem typu |
| `===` | striktní rovnost, bez převodu typu |
| `!=` | nerovnost, s převodem typu |
| `!==` | striktní nerovnost, bez převodu typu |
| `>` | větší než |
| `<` | menší než |
| `>=` | větší nebo rovno |
| `<=` | menší nebo rovno |

```javascript
const a = 5;
const b = "5";

console.log(a == b);   // true  | "5" se převede na 5 (int)
console.log(a === b);  // false  | "5" zůstane "5" (string/char)
```
> ChatGPT doporučuje používat `===` a `!==`. <br>
> *Netuším proč.*

---
### 10.4 Logické operátory
Používají se ke spojování podmínek uvnitř podmínkových příkazů.
#### `&&` A zároveň
Obě podmínky musí být pravdivé.
```javascript
if (true && true) {
   // se provede
}

if (true && false){ // << jedna z podmínek je false
    // se NEprovede
}
```
---

#### `||` = Nebo
Alespoň jedna podmínka musí být `true`.
```javascript
if (true || true) {
    // se provede
}

if (false || true) {
    // se provede
}

if (false || false) {
    // se NEprovede
}
```

---
#### `!` = opačná hodnota
`!true` >>> `false` 

`!false` >>> `true`
```javascript
if (!true) {
    console.log("Podmínka if vrací false.");
}
```

> [!TIP]
> Jako `false` se v JavaScriptu vyhodnocují nejen hodnoty `false`, ale také:<br>
> `0` - Číselná nula <br>
> `""` - Prázdný text <br>
> `null` - Chybějící hodnota <br>
> `undefined` - Hodnota nebyla určena <br>
> `NaN` - Neplatný číselný výsledek <br>
---

## 11 Cykly
Cyklus opakuje stejný kód vícekrát.

### 11.1 `for`
Opakuje kód `i`-krát.

Struktura:
```javascript
for (let i = 0; i < pocet_opakovani; i++) {
    // kód
}
```
---
### 11.2 `while`
<ins>Nejprve se kontroluje podmínka.</ins><br>
Pokud má podmínka hodnotu `true`, cyklus pokračuje.

```javascript
while (podminka) {
    // kód
}
```
Často se používá takto:
```javascript
while (true) {
    // kód
    if (podminka)
        break; // Okamžitě ukončí cyklus, je-li podmínka true.
}
```
---
### 11.3 `do ... while`
Je podobný cyklu `while`, ale podmínka se kontroluje na konci. <ins>Cyklus se spustí alespoň jednou.</ins>

Struktura:
```javascript
do {
    // kód
} while (podminka);
```
---

### 11.4 `break` a `continue`

#### `break` - okamžitě ukončuje cyklus.

```javascript
for (let i = 0; i <= 10; i++) {
    if (i == 5) {
        break;
    }

    console.log(i);
}
```

Výsledek:

```text
0
1
2
3
4
```
---

#### `continue` – přeskočí aktuální opakování a pokračuje dalším opakováním.

```javascript
for (let i = 0; i <= 5; i++) {
    if (i == 3) {
        continue;
    }

    console.log(i);
}
```

Výsledek:

```text
0
1
2
4
5
```
---

## 12 Funkce
Funkce je blok kódu, který můžeme opakovaně spouštět jejím zavoláním. Používá se například pro rozdělení programu na menší části.
```javascript
function nazevFunkce(){
    // kód
}
```
### 12.1 Volání funkce
Funkci můžeme zavolat například po kliknutí na tlačítko pomocí onclick:
```html
<button onclick="nazevFunkce()">Pozdrav</button>
```
Nebo po změně hodnoty v zadávacím poli pomocí onchange:
```html
<input type="number" onchange="nazevFunkce()"> 
```
Funkci lze zavolat také přímo v kódu JS:
```javascript
if(true)
{
    nazevFunkce();
}
```
 > [!WARNING]
 > Samotné vytvoření funkce nestačí k jejímu spuštění! <br>
 > Funkci je nutné nějak zavolat.
--- 
### 12.2 Parametr funkce
> Funguje stejně jako v C#.
Vzorec:
```javascript
function nazevFunkce(parametr) {
    // kód, který pracuje s parametrem
}
nazevFunkce(parametr);
```
Příklad:
```javascript
function vypisCisla(cislo) {
    console.log(cislo);
}

vypisCisla(5);  // vypíše 5
vypisCisla(10); // vypíše 10
```

### 12.3 Návratová hodnota `return`

Funkce může pomocí `return` vrátit výsledek, který můžeme uložit do proměnné nebo dále použít.

Vzorec:

```javascript
function nazevFunkce(parametry) {
    return hodnota;
}

let vysledek = nazevFunkce(argumenty);
```

Příklad:

```javascript
function secti(a, b) {
    return a + b;
}

let vysledek = secti(5, 3);

console.log(vysledek); // vypíše 8
```
---
## 13 HTML – formulářové prvky
### 13.1 `input` 
`input` - Slouží k vytvoření vstupního pole, do kterého může uživatel zadávat nebo vybírat hodnoty.
```html 
<input type="text" id="jmenoIn" placeholder="Zadej jméno">
```

### 13.2 Základní atributy
| Atribut | Význam | Příklad |
| --- | --- | --- |
| type | Určuje typ vstupního pole. | type="number" |
| id | Jedinečný identifikátor prvku pro JS a CSS. | id="cisloIn" |
| name | Název hodnoty při odesílání formuláře. | name="jmeno" |
| value | Výchozí hodnota pole. | value="10" |
| placeholder | Pomocný text zobrazovaný v prázdném poli. | placeholder="Zadej číslo" |
| min | Nejnižší povolená hodnota u podporovaných typů. | min="1" |
| max | Nejvyšší povolená hodnota u podporovaných typů. | max="100" |
| step | Povolený krok hodnoty. | step="0.5" |
| required | Vyžaduje vyplnění pole při odeslání formuláře. | required |
| disabled | Zakáže používání pole. | disabled |
| readonly | Zakáže úpravu hodnoty, ale dovolí ji označit a kopírovat. | readonly |
| checked | Nastaví výchozí zaškrtnutí checkboxu nebo radio tlačítka. | checked |
| multiple | Umožní výběr více souborů nebo hodnot u podporovaných typů. | multiple |
| autocomplete | Řídí automatické doplňování hodnot prohlížečem. | autocomplete="off" |

### 13.3 Typy `input`
| Typ | Definice |
| --- | --- |
| text | Textové pole |
| number | Číselné pole |
| password | Heslo, jehož znaky se vizuálně skryjí |
| email | E-mailová adresa |
| checkbox | Zaškrtávací políčko |
| radio | Výběr jedné možnosti ze skupiny |
| date | Výběr data |
| time | Výběr času |
| range | Posuvník pro výběr hodnoty |
| color | Výběr barvy |
| file | Výběr souboru |
| submit | Odeslání formuláře |
| button | Tlačítko bez výchozí akce odeslání |
