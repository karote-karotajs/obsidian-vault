## Basic syntax
 <img src="https://cdn.statically.io/gh/TheOdinProject/curriculum/05ce472eabf8e04eeb2cc9139e66db884074fd7d/foundations/html_css/css-foundations/imgs/00.jpg">
- Trīs parametri - selector izvēlas, ko ietekmēt, property - kas ietekmējams, value - cik ļoti(?)
- `<div>` - pamata HTML elements, tukšs konteineris
## Selektori

- Selektori izvēlās, uz kuriem HTML elementiem kurš CSS noteikums attiecas.
### Universālais selektors

  ```
* {
  color: purple
}
  ```

- Izvēlas elementus no jebkura tipa
### Tipa selektors

- Izvēlas tipu, kuram attiecināt deklarācijas, piem.
- Tipa selektoram nevajag punktu!
```
div {
	color: white;
}
```

- Visi elementi, kuriem ir div html tags, tiks attiecināta šī deklarācija.
### Klases selektors

- No sākuma jāpievieno klase HTML tagam
```
<div class="alert-text">Please agree to our terms of service.</div>
```
- Pēc tam var izvēlēties HTML elementus ar CSS
```
.alert-text {
	color: red;
}
```
- **! Sintakse - .(klase)**
### ID selektors
- Līdzīgi klases selektoriem, bet ID ir unikāls tikai vienam elementam. Tas nevar atkārtoties.
```
<div id="title">Mana mājaslapa</div>
```
- Pēc tam izvēlas ar ID CSS failā
```
#title {
	background-color: red;
}
```
- ID selektors izmanto # simbolu.
### Grupēšanas selektors
- Ja kādai no grupām atkārtojas kāda deklarācija, piem. teksta krāsa, fona krāsa, tad var sagrupēt šos selektorus
- Ir divas grupas - read un unread, var deklarēt kopējos, un pēc tam katrai grupai atsevišķi
```
.read,
.unread {
	color: white;
	background-color: black;
}

.read {
	(unikālas deklarācijas);
}

.unread {
	(unikālas deklarācijas);
}
```
### Selektoru savienošana

- Vienam elementam var būt vairākas klases, piem.
```
<div>
	<div class="subsection header">Latest Posts</div>
	<p class="subsection preview">Preview for post</div>
</div>
```

- Subsection klasei jau ir kāds stils, bet ja grib izvēlēties tikai subsection klasi, kurai ir arī header klase, var izmantot savienošanu:
```
.subsection.header {
	color: red;
}
```
- Šāds selektors izvēlās jebkādu elementu, kuram ir gan subsection, gan header klase, un to stilizē.
- Var arī savienot klasi un ID, piem.
```
<div>
	<div class="subsection">Latest Posts</div>
	<div class="subsection" id="unique">Text</div>
</div>
```

```
.subsection {
	color: blue;
}

.subsection#unique {
	background-color: red;
}
```

- Visiem subsection elementiem teksta krāsa būs zila, bet tam, kuram ir ID "unique", būs sarkana fona krāsa.
### ! Tipa selektorus nevar savienot, jo tekstam nevar būt divi tipi vienlaicīgi.

### Descendant kombinators

- Izvēlas elementus, balstoties uz to attiecībām(?)
- Ja ir elements ar klasi `child` zem klases `ancestor`, piem.
```
<div class="ancestor">
	<div class="child">
		<div class="contents"></div>
	</div>
</div>

<div class="child"></div>
```

un tad mēs izmantojam selektoru
```
.ancestor .child {
	deklarācija
}
```

tiks izvēlēti tikai tie `child` klases objekti, kuri ir *nested* iekš `ancestor` klases.

## Properties

### Color, background-color

- Var izmantot vairāku veidu vērtības
	- Vārdos - `red`, `transparent`
	- HEX, RGB, HSL
### Tipogrāfija, text align

- `font-family` - tā var būt viena vērtība vai arī komatu atdalīts saraksts.
	- `font-family "Times New Roman", serif`
	- Parasti definē gan konkrētu fontu, gan arī generic fallback, ja nav iespējams ielādēt specifisku fontu
- `font-size` - definē fonta izmēru
- `font-weight` - definē boldu
	- Var būt vārdos - `font-weight: bold;` vai arī skaitļos - `font-weight: 700;`
- `text-align` - nolīdzina tekstu, piem. `text-align: center;`
- Bilžu izmēri - parasti atstāj vienu vērtību auto, lai nepazaudētu proporcijas
```
img {
	height: auto;
	width: 500px;
}
```
	
## Pievienot CSS HTML failam

Ir vairākas metodes: external CSS, internal CSS, inline CSS. Parasti lieto external CSS, kur ir atsevišķs styles.css fails.

### External CSS

Pievieno void `<link>` elementu `<head>` tagā, ar `rel="stylesheet"` un `href="(CSS FAILA NOSAUKUMS).css`. Rel ir attiecība starp failiem, "stylesheet" - kuru CSS failu izmantot, href norāda, kur tas ir.

### Internal CSS

`<head>` tagā pievieno `<style>` tagu, kurā ieraksta visas nepieciešamās deklarācijas.

### Inline CSS

Pašā satura tagā pievieno `style="(deklarācijas)`

## Cascade

- Kas ir kaskāde?
	- Konfliktējošo deklarāciju gadījumā, tiek piemērots specifiskākais selektors.
	- Tie tiek sakārtoti šādi:
		1. ID selektori (visspecifiskākais)
		2. Klases selektori
		3. Tipu selektori
	- Ja ir vienādi selektori, bet vienai deklarācijai to ir vairāk, tad tā ir specifiskāka
	- Deklarāciju mantošana - ir dažādas īpašības, kuras tiek mantotas visiem apakšējiem elementiem
	- Deklarāciju kārtība - ja ar iepriekšējiem likumiem nevar noteikt, kurš ir specifiskāks, tad tiek izmantota kārtība - kura ir pēdējā deklarācija, tā tiek izmantota

## The Box Model

- Viss novietojums mājaslapā ir "kastēs" - tās ir kastes, kas var būt kastēs, kastes blakus kastēm, utt.
- Manipulēt ar šīm kastēm var ar padding, border, un margin deklarācijām
	<img src="https://cdn.statically.io/gh/TheOdinProject/curriculum/c547923a86efaccb0fc71adf70fda2ea340b4cb1/foundations/html_css/css_foundations/the_box_model/imgs/box-model.png">
	

- Box sizing property
	- border-box - ja deklarē augstumu un platumu, tad izmantos arī border un padding izmēru, lai noteiktu kastes izmēru!
	- content-box - neņem vērā border un padding izmēru
	- Kam ir jābūt 500x200 pikseļu? Content box vai arī border, padding un content kopā?
- Ir dažādi kastu veidi
	- Kastēm var mainīt veidu ar `display` deklarāciju.
	- `block` - kaste pāriet uz nākošo līniju, `width, height` tiek izmantots, padding, margin un border kustina citus elementus, ja `width` netiek specificēts, tad tas aizpildīs visu vietu.
	- `inline` - kaste nepāriet uz nākošo līniju, `width, height` margin neietekmē, top un bottom padding un borders maina kastes izmēru, neietekmējot pārējos elementus, left un right padding, margins un borders ietekmē pārējos elementus, kas ir līnijā.
- `block, inline` ir ārējie display type - tie nosaka, kā kastes novietotas attiecībā pret citām kastēm, inner display type - kā elementi tiek novietoti kastē.
- ```The key thing to remember for now is: Changing the value of the `display` property can change whether the outer display type of a box is block or inline. This changes the way it displays alongside other elements in the layout.
  - `display: inline-block;` bet parasti izmanto flexbox
  - `div, span` - var saturēt jebko
	  - `div` - block style elements
	  - `span` - inline elements
## CSS Layout

- Normal flow - ja netiek izmantots CSS
- Float - ļauj elementiem piekļauties

## Flexbox

- Veids, kā pozicionēt elementus mājaslapā
- Flex konteineri un priekšmeti
- Jebkurš elements, kuram ir `display: flex-container`, ir Flex konteineris, jebkas, kas ir Flex konteinerī, ir Flex priekšmets
- `flex` shorthand - sastāv no trīs īpašībām, `flex-grow, flex-shrink, flex-basis`
```
div {
	flex: 1;
}
  ```
  ir patiesībā `flex-grow: 1, flex-shrink: 1, flex-basis: 0`
  - Flex asis - row un column, `flex-direction` maina to, vai elementi sakārtoti vertikāli vai horizontāli. Noklusējumā - tiek sakārtoti row jeb horizontāli.
- Viss Flexbox ir balstīts uz primāro asi
- `justify-content` sakārto elementus uz primārās ass, piem. `center` tos novieto pa vidu primārajai asij
- `flex-grow` - kontrolē to, kā vieta tiek aizpildīta ar Flexbox elementiem
- `flex-shrink` - kontrolē to, kā vieta tiek atņemta katram elementam
- Piem. - ja ir 500px "hypothetical" vieta diviem elementiem, un ja flex-grow abiem elementiem ir 1, tad abi elementi aizpildīs pa 250px, ja būtu `.x {flex-grow: 2;}, .y {flex-grow 1;}`, tad tie sadalītu attiecībā 2:1.
- Savukārt `flex-shrink` maina to, kādā attiecībā elementiem tiek atņemta vieta līdzīgā veidā.
- `min-width`, `min-height` - palīdz ar elementiem, kam noklusējuma platums, augstums ir pārāk liels, un elementi var overflowot.
- `gap` - ļauj izveidot starpas starp Flex elementiem
- Auto margins - ja izmanto `margin: auto`, tad tas aizpilda papildus vietu ar margin, un pievieno to kādam Flexbox elementam, piem. ja ir vajadzīgs, ka viens elements ir kreisajā pusē, un pārējie ir labajā, tad pirmajam Flexbox elementam, pierakstot `margin-right: auto`, tas aizpildīs pārējo vieto Flexbox konteinerī ar margin.

## CSS boilerplate

- Lai nav jāčakarējas ar padding un margin, lietderīgi ir izmantot
```
 * {
	padding: 0;
	margin: 0
	box-sizing: border-box
	}
  ```
  Tad definē padding un margin katram elementam, piem. body uzlikt margin, lai būtu atstarpe no pārlūka malām, kā arī izmantot border box sizing, lai visi elementi būtu definētajos izmēros.