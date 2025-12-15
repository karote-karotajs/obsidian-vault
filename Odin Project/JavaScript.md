:nvimL- HTML failā iekļaut JavaScript kodu var ar HTML tagu `<script>`.
- Var arī iekļaut ar atsevišķiem .js failiem, lai saglabātu tīru HTML failu
- `<script src="javascript.js"></script>`
## Mainīgie (variables)
- Jebkuras programmas pamatbloks, datu konteineri
- Mainīgos var deklarēt ar `let`
	- Sintakse - `let variable = value`
	- Mainīgais var būt gan teksts, izmantojot `"variable"` - pēdiņas, vai arī skaitliska vērtība
- Tos var mainīt, neizmantojot `let`, piem.
	- Deklarē mainīgo `let variable = 1`
	- Pēc tam, lai mainītu vērtību, izmanto tikai `variable = 2`
	- Mainīgo var arī deklarēt, nepiešķirot tam nekādu vērtību, un piešķirt tam vērtību citā koda daļā
- Deklarējot `let` divreiz, tiek izmesta kļūda, jo mainīgais ir jādeklarē vienreiz, vērtību tam maina ar `mainīgais = vērtība`.
- Parasti mainīgā nosaukumu raksta ar `camelCase`, pirmais burts mazs, pārējie vārdi ar pirmo lielo burtu
## Nemainīgie (constant)
- Izmanto nemainīgu vērtību deklarēšanai, piem. `const pi = 3.14`
- `pi = 4` nemainīs nemainīgā vērtību, tas izmetīs kļūdu konsolē
	 ![[Pasted image 20251129202146.png]]

Pastāv arī `var`, bet tas netiek bieži lietots, tam ir dažādas īpatnības, kas atrisinātas, kad ieviests `let` un `const`.
- Ja izmet kļūdu, programma neiet tālāk (visticamāk no tā var izvairīties, izmantojot exception vai kaut ko tamlīdzīgu)

## Skaitļi
- Matemātiskas darbības notiek pēc standarta principa - iekavas, reizināšana/dalīšana, saskaitīšana/atņemšana
- Matemātiskās darbības var veikt ar skaitļiem un ar mainīgajiem
- Ir pieejamas visas matemātiskās darbības -
	1) Saskaitīšana `+`
	2) Atņemšana `-`
	3) Reizināšana `*`
	4) Kāpināšana `**`
	5) Dalīsana `/`
	6) Modulis `%`
		! Šis operators dala divus veselus skaitļus, un izdod to atlikumu, piem. `let variable = 5 % 2`, `variable` būs 1
	7) Increment `++`
		- Pievieno vērtībai 1 un atgriež vērtību pirms vai pēc pievienošanas, atkarībā no tā, kur ir operators
		- **Nevar izmantot skaitļiem, tikai mainīgajiem!**
	8) Decrement `--`
		- Līdzīgi, tikai otrādi
- Skaitļiem JavaScript ir tikai viens  datu tips - `Number` (it kā, ir vēl `BigInt`, kas ir izmantots ļoti lieliem veseliem skaitļiem)
- Ir arī *assignment operators*, kas ir saīsinājums matemātiskajām darbībām, piem.
``` 
let x = 4
	  x += 4
  ```
x būs 8, jo += operators pievieno mainīgajam labajā pusē esošo mainīgo vai skaitli. Šādi operatori ir `+, -, *, /` darbībām.
- Ir arī salīdzinājuma operatori, kas izdod boolean vērtību.
## Noderīgas `Number` metodes

-  `toFixed()` - decimālskaitļiem liek noapaļot līdz noteiktam skaitam decimāldaļu, kas definēts metodes iekavās, piem.
		```
		const lotsOfDecimal = 1.23456
		const twoDecimalPlaces = lotsOfDecimal.toFixed(2)
		```
- `Number()` - mēģina pārvērst string tipa vērtību par skaitli. Noder it īpaši, ja ir form ievade, kur datu tips parasti ir string.

## Datu tipi

- Javascript ir 8 pamata datu tipi
- Mainīgajā var ielikt jebkādu datu tipu, un tos var mainīt neatkarīgi no tā, vai pirms tam tas ir bijis skaitlis vai string. JavaScript ir *dynamically typed*.
### Kādi ir datu tipi?

1) Skaitļi (*number*)
	- Tie ir gan veseli, gan *floating point* (skaitļi ar decimāldaļām)
	- Skaitļiem ir dažādas operācijas (skat. [[JavaScript#Skaitļi]])
	- Īpašas Number vērtības
		- `Infinity` 
		- `-Infinity`
		- `NaN` - Not a Number, jebkura cita matēmātiska operācija ar NaN tajā atgriezīs NaN.
	- Matemātika ir "droša" JavaScript, programma neapstāsies, ja veiks nedefinētas matemātiskas darbības.
2) BigInt (lieli veseli skaitļi)
	- Izmanto lieliem, veseliem skaitļiem, kas pārsniedz JavaScript atļauto
3) String
	- Teksts - to ieskauj "", '' vai backticks.
	- Ar backticks, string kļūst par "extended functionality" string, kuram var ielikt mainīgos un izteiksmes ar `${}`, piem.
		Ir mainīgais `let name = "John"`
		To var ievietot string type variable, ja tas ir ieskauts backticks, piem.
		`let fullName = ${name}` (ar backtickiem, bet Obsidian backticki ir code formatēšana :(
	- 
4) Boolean (loģiskā vērtība)
	- Ir tikai divas vērtibas - `true` un `false`.
	- Boolean tips arī tiek atgriezts, ja ir izmantots operators, kas salīdzina, piem `>`, `===`, `!==` utt.
5) Null value
6) Undefined value
! Starp šiem diviem atšķirība ir tāda, ka null value parasti definē pats, bet undefined tiek atgriezts, ja tiek deklarēts mainīgais, bet tam nav dota vērtība.
 7) Objekti
	 - Pārējie datu tipi ir "primitīvi", jo tie satur tikai vienu vērtību
	 - Objekti var saturēt vairāk datu
8) Simboli
	- Tiks vairāk iztirzāti, kad mācīsies par objektiem
- `typeof` - atgriež datu tipu. Var izmantot debugging.

## ! [String metodes](https://www.w3schools.com/js/js_string_methods.asp)

## Salīdzinājumi (comparisons)
- Visi salīdzinājuma operatori atgriež boolean vērtību
- Salīdzinot string tipa mainīgos, tiek izmantots leksikogrāfiskais salīdzinājums - pēc Unicode indeksa
- Ja salīdzina divus dažādus tipus, tad JavaScript string pārvērš par skaitļiem. Boolean vērtības kļūst par 1 vai 0.
- Ja grib atšķirt `false` no 0, var izmantot `===` - strict equality operator. Tad, ja ir divi dažādi datu tipi, tas atgriezīs `false`.

## Loģiskie operatori

- JavaScript ir 4 loģiskie operatori
	1) || - or,
	2) && - and,
	3) ! - not,
	4) ?? - nullish coalescing
## 1) || - OR
- Ja jebkurš no argumentiem ir `true`, tad tas atgriež `true`, ja neviens nav `true`, tas atgriež `false` - klasiskā programmēšanas loģika
- JavaScript OR operators ir sarežģītāks
	- Ja operandi nav boolean, tie tiek pārvērsti boolean.
	- Skaitļi 1 - patiess, 0 - nepatiess
	- Lielākoties tiek izmantots `if` statementos, lai pārbaudītu, vai jebkurš no dotajiem ir patiess.
	- JavaScript specifika - OR atrod pirmo patieso vērtību no vairākiem
		- Piem. var izvēlēties pirmo patieso vērtību no saraksta. OR operators iet cauri dotajām vērtībām. Ja kādam no mainīgajiem nav definēta vērtība vai arī tā ir nulle, tad tas ies cauri tam, līdz atradīs kādu patiesu vērtību, t.i. definētu, vai arī, ja visas dotās vērtības ir nepatiesas (falsy), tad tas atgriež pēdējo vērtību.
		- OR var izmantot arī, ja, piemēram, kreisajā pusē esošais operands ir nepatiess, lai izpildītu komandu labajā pusē.
## 2) && - AND

- Klasiskajā programmēšanas loģikā - atgriež `true`, ja abi operandi ir truthy, ja nav - `false`
- JavaScript - atrod pirmo falsy vērtību
	- Iet cauri visiem operandiem no kreisās uz labo
	- Katru pārvērš par boolean, ja kāds no tiem ir `false`, atgriež tā vērtību
	- Ja visi operandi izvērtēti un patiesi, atgriež pēdējo
	- Citos vārdos - atgriež vai nu pirmo falsy vērtību, vai arī pēdējo, ja visi operandi ir truthy
	- Princips kā OR, tikai otrādi!
	- && ir lielāka precedence kā ||!

### ! Abus iepriekšminētos operatorus nevajag izmantot `if` vietā! `if` ir salasāmāks kā loģiskie operatori.

## 3) ! - NOT

- Izmanto tikai vienu argumentu
- Pārvērš operandu par boolean tipu un atgriež pretējo
- Visaugstākā precedence no visiem loģiskajiem operatoriem

## Conditionals - `if` un `?`

`if(...)` izvērtē to, vai tas, kas ir iekavās, ir patiess, un tad izpilda attiecīgu bloku ar kodu
Piem. 
	
	`if (year = 2025) console.log("Ir pareizais gads!")`
Ja ir vajadzīgas vairākas rindas ar kodu, tad izmanto `{}`
	```
	if (year = 2025) {
		console.log ("Ir pareizais gads!)
		console.log ("Malacis!")
	}
	```
Ieteicams vienmēr izmantot `{}`, tas uzlabo salasāmību.

`else` - neobligāts papildinājums, kas izpildās, ja `if` iekavas ir nepatiesas, piem.
```
if (year = 2025) {
	console.log ("Pareizi!")
} else {
	console.log ("Nepareizi!")
}
```

Ir arī `else if`, kas ir vēl viens `if`, ja pirmais `if` neizpildās.

```
if (year > 2025) {
	console.log ("Pārāk agri...")
} else if (year < 2025) {
	console.log ("Pārāk vēlu...")
} else {
	console.log ("Tieši tā!")
}
```

`?` sintakse

`let result = condition ? value1 : value2;`

`condition` tiek izvērtēts. Ja tas ir patiess, `result` tiek atgriezta pirmā vērtība, ja nepatiess - otrā.

## `switch` un `case`

`switch` var aizvietot vairākus `if`, salīdzinot vērtību ar vairākiem variantiem, vai arī izpildot kodu, kas ir zem `default`.

```
switch(x) {
	case `value1`:
		...
		[break]
	case `value2`:
		...
		[break]
	default:
		...
		[break]
}
```

Process - iet cauri dotajiem `case`, skatoties, vai kādai no vērtībām ir *strict equality* ar x. Ja ir, tad izpilda doto koda bloku zem `case`. Ja nav, tad izpilda `default`.

Var arī savienot vairākus `case`, kas izpildīs vienu un to pašu kodu.

```
switch(x) {
	case `value1`:
	case `value2`:
		kods1
		[break]
	case `value3`:
		kods2
		[break]
	default:
		kods3
}
```

Šajā gadījumā, ja x === `value1` VAI `value2`, tiks izpildīts `kods1`.

## Funkciju pamati

Funkcija ir skripts, kas sapakots vienā ietvarā, ko var izmantot vairākkārt, lai nebūtu jāpārraksta kods.

Piemērs

```
function favoriteAnimal(animal) {
	return animal + " is my favorite animal!
}

const message = favoriteAnimal("Cat")
console.log(message)
```

Šeit tiek izveidota funckija, kurā ir **parametrs** iekavās - `animal`. Ar šo mēs nosakam, ka šai funkcijai mēs gribam sūtīt vērtību. Pēc tam, deklarējam `const message`, kur piesaucam funkciju, un sūtam parametru funkcijas iekavās.

Protams, var arī vienkārši funckiju piesaukt `console.log()`, bet, gadījumos, kad funkcijas rezultāts būtu jāpiesauc vairākkārt, labāk to nosūtīt uz mainīgo, lai nebūtu vairākkārt jāiet cauri funkcijai, kas var būt lēnāk, jo tad ir jāiet cauri visai funkcijai, nevis tikai jāpiesauc mainīgais, kurā ir funkcijas rezultāts.

Ja funkcijai ir vairāki parametri, tad tie jāatdala iekavās ar komatu - `const newFunction(param1, param2)`

Funckijai var arī būt noklusējuma parametrs, ko definē, definējot funkciju.

```
function hello(name = "Tomijs") {
	console.log("Hello ${name}!")
}
```

Ir arī anonīmās funkcijas.

```
(function () {
	alert("hello")
});
```

Funkcijas mainīgos nevar manipulēt ārpus funkcijas. Šis ir izveidots ar nolūku, lai nebūtu konflikti starp mainīgajiem. Tas ir **funkcijas scope**. Funkcijas, savukārt, var izmantot **global** mainīgos, taču citas funkcijas nevar izmantot mainīgos, kas ir deklarēti funkcijas ietvarā.

Ja grib deklarēt **lokālo** mainīgo, tas ir, mainīgo, kas ir tikai funkcijas ietvarā, tad jāizmanto `let`. Ja neizmanto `let`, tad funkcija izmaina **globālo** mainīgo.

Piem.

![[Pasted image 20251202101812.png]]

Šeit tiek deklarēts mainīgais `userName`, ar vērtību `"Tomijs"`. Pēc tam, **funkcijas ietvarā** tiek deklarēts mainīgais `userName`, un funkcija tiek piesaukta. Pēc tam, tiek izmantots `console.log`, lai piesauktu **globālo** mainīgo.

![[Pasted image 20251202102042.png]]

Kā var redzēt, kaut gan funkcijā tiek izmantots tāds pats mainīgā nosaukums, funkcija **neizmaina** globālo mainīgo, jo tika izmantots `let`.

![[Pasted image 20251202102156.png]]
Savukārt, izņemot ārā `let`...

![[Pasted image 20251202102239.png]]

Funkcija izmaina globālo mainīgo, jo netiek deklarēts mainīgais funkcijā. Kas notiek, ja funkcijā tiek deklarēts ar `let` mainīgais, un mēs mēģinam to izmantot ārpus funkcijas?

![[Pasted image 20251202102418.png]]

Funkcijas ietvarā ir mainīgais `userName`. Funkcija var to izmantot, savukārt, pēc funkcijas, izmantojot mainīgo `userName`...

![[Pasted image 20251202102513.png]]

`return` var izmantot, lai atgrieztu kādu vērtību, piesaucot funkciju.
![[Pasted image 20251202103012.png]]
Šeit tiek definēta funkcija `sum`, kurai ir divi parametri, `a` un `b`.

Funkcijai parasti paredzēta tikai viena darbība. Parasti to nosauc ar `get`, `calc`, `create`, utt. Funkcijai, kurai ir prefikss `get`, nevajadzētu arī parādīt to, utt.

## Function expressions

Funkcija JavaScript nav "maģiska struktūra", bet vērtība. Mainīgajiem var piešķirt funkcijas vērtību, nenosaucot funkciju.

```
let sayHi = function () {
	alert( "Hello" );
};
```

## Kļūdas

`ReferenceError` - notiek, ja nav deklarēts mainīgais vai neatrodas dotā bloka apjomā
`SyntaxError` - sintakses kļūdas
`TypeError` - operators mēģina apstrādāt nepareiza tipa datus

## Loops and Arrays

Lai izpildītu instrukcijas vairākkārt, izmanto loop. Izmantojot loop, bieži būs jāizmanto kolekcija ar mainīgajiem, viens tiem - `Array`.  Parasti izmanto `for... of` loop. Tas iet cauri kādai kārtībai ar vērtībām.

![[Pasted image 20251214164613.png]]

Šeit tiek izveidots `Array` ar nosaukumu `cats`, kurā ir trīs string tipa vērtības. For loop šeit iet cauri array, un iedod mainīgajam cat vērtību, atkarībā no tā, kurā reizē tiek izmantots for loop. Pēc tam, for loop izpilda kodu, kas ir iekavās. Mainīgajam nav obligāti jābūt kodā pēc tam!

Ar `map()` var izmainīt katru no array vērtībām, piem. izveidot funkciju, kas string mainīgo izmaina uz upper case.

![[Pasted image 20251214171148.png]]

Šeit tiek izveidota funkcija, kas pārvērš string tipa mainīgos lielajos burtos. Ar `mainīgais.map(funkcija)` katra array vērtība tiek izlaista cauri funkcijai, un funkcijas return tiek atgriezts un ievietots atpakaļ array.

`filter()`, savukārt, ir nepieciešams, lai funkcija atgriež boolean tipa vērtību. Ja funkcija atgriež `True`, tad array vērtība tiek iekļauta jaunajā array.

For loop standarta sintakse ir sekojoša:

```
for (initializer; condition; final-expression) {
  code
}
```

Initializer - parasti mainīgais, kas ir skaitlis, kas tiek inkrementēts, lai noteiktu, cik reizes tiek izpildīts loop, to var arī saukt par skaitītāja mainīgo.
Condition - nosaka, kad for loop ir jābeidzas, vērtībai ir jābūt `True`, lai loop turpinātos. Parasti tas ir salīdzinājums, kam jāatgriež `False`, lai izietu ārā no loop.
Final-expression - tiek izpildīts katru reizi, kad tiek izpildīts for loop.

![[Pasted image 20251214174044.png]]

Initializer vietā var arī likt jebkuru citu mainīgo. Pēc tam, kamēr i ir mazāks par 10, for loop tiek pildīts. Katru reizi, kad tiek izpildīts loop cikls, i tiek inkrementēts.

![[Pasted image 20251214174218.png]]

Šis tiek atgriezts konsolē.

Ar `break` var iziet ārā no loop, ja izpildās kāds apstāklis. Savukārt, ar `continue` var turpināt ar nākošo loop, piem.

`while` loop, savukārt, ir tikai viens mainīgais - apstāklis, kurš, kamēr atgriež vērtību `True`, izpilda kodu, kas ir figūriekavās.

```
while (condition) {
	code
}
```

`do while` loop kods tiek izpildīts vismaz vienu reizi, jo apstāklis tiek definēts pēc tam.

```
initializer
do {
code
} while (condition)
```

Labels for break/continue - ja ir cilpas cilpās, tad ar label var izmantot break vai continue ārpus iekšējās cilpas.


