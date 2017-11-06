# AngularJS 

#### Angular JE:

* open-source JavaScriptový framework vytvorený spoločnosťou Google 
* silný nástroj pre tvorbu webových a mobilných aplikácií
* verzie: Angular 1.x (r. 2010), 2.x (r. 2015), 4.x (r. 2017), Angular 5 (**23.10.2017**)
* **Igor Minár**, šéf vývojového tímu - [**článok**](https://plus7dni.pluska.sk/Rozhovory/Slovak-v-Google-Ked-som-tam-prisiel-pripadal-som-si-ako-na-vesmirnej-lodi)

#### Angular 1 vs. Angular 2/Angular 4

* Angular 2 **nie je upgrade** Angularu 1 
* Angular 2 je **rýchlejší a jednoduchší** než Angular 1
* Angular 2 **používa komponenty** 
* Angular 2 **používa [TypeScript](https://www.typescriptlang.org/)**, ktorý je kompilovaný do JavaScriptu
* Angular 2 má lepšiu **podporu pre mobilné zariadenia**

#### Angular NIE JE:

* JavaScriptová knižnica
* platforma alebo jazyk 
* plugin alebo rozšírenie 
* určený pre prácu na strane servera (backend)

Zameriava sa na **tvorbu** **[single-page](https://en.wikipedia.org/wiki/Single-page_application)** **aplikácií** - dynamické načítavanie stránok; pri prvom spustení sa načíta celá stránka, potom sa obnovuje už iba jej obsah. Výhodou je rýchlejšie načítavanie "bez prebliknutí", ale aj minimalizácia prenášaných dát medzi serverom a klientom. Takýmito aplikáciami sú napr. **Gmail, Google Maps, Facebook, GitHub, SoundCloud...**

## Data-Binding

Angular aplikácie sú **tvorené HTML kódom** do ktorého sa vkladajú **špeciálne tagy**, ktoré **určujú**, aké **operácie** sa majú vykonať, alebo aké **dáta** sa majú na konkrétne miesto **vložiť** (tzv. **Data-Binding**, čiže zväzovanie dát s premennými). 

Pomocou špeciálneho zápisu je možné **vkladať dynamický obsah do statického HTML kódu**. Miesto, kam sa má dynamický obsah umiestniť sa označuje **dvoma zloženými zátvorkami**. 

**Príklady:**

```html
{{ expression }}
```

```html
{{ 1 + 1 }} // sčítanie
```

```html
{{ a + b }} // práca s premennými
```

```html
{{ user.name }} // práca s objektmi
```

```html
{{ collection[index] }} // práca s kolekciami
```

```html
<input type="text" value="{{ user.name }}"> // Data-Binding ako súčasť HTML kódu
```

## Architektúra 

Angular je navrhnutý tak, aby **oddeľoval zobrazovaciu logiku od aplikačnej logiky**. 

#### Angular 1.x
Architektúra je postavená návrhovom vzore **[Model-View-Controller (MVC)](https://en.wikipedia.org/wiki/Model%E2%80%93view%E2%80%93controller)**.

Tvorba aplikácií s využitím architektúry MVC vyžaduje vytvorenie troch komponentov:

* Model (model) - reprezentuje informácie s ktorými aplikácia pracuje
* View (pohľad) - prevádza dáta reprezentované modelom do užívateľsky prívetivej podoby
* Controller (ovládač) - reaguje na udalosti (zväčša prichádzajúce od užívateľov) a zabezpečuje zmeny v modely a v pohľade.

![](https://i.imgur.com/tCYH8A9.png "Princíp MVC")

#### Angular 2.x

**Základným stavebným blokom** každej aplikácie vybudovanej pomocou Angular 2 je **komponent**, ktorý predstavuje určitú funkcionalitu pre danú aplikáciu. Celá aplikácia tvorí **strom komponentov**.

**Časti komponentu:**

* **Trieda** - vlastnosti a metódy (.ts)
* [**Metadata**](https://angular.io/api/core/Component#metadata-overview) - definuje napr. názov html tagu komponentu (`selector`), štýly, animácie, šablóny a iné
* **Template** - definovanie HTML pohľadu, ktorý bude zobrazovaný v aplikácii (.html)

*Príklad triedy komponentu:*

```typescript
import { Component } from '@angular/core';

@Component ({ 
   selector: 'my-app',  					// html tag komponentu
   templateUrl: './app.component.html'     // cesta k šablóne, ktorá prislúcha tomuto komponentu
   styleUrls: [ './app.component.css' ]    // definovanie štýlu
}) 

export class AppComponent { 
	name:string = 'My First Angular Page';
} 
```

Každá Angular 2 aplikácia taktiež pozostáva z [**modulov**](https://docs.angularjs.org/guide/module), ktorej súčasťou musí byť koreňový **Angular Root Module** (zostavovací modul aplikácie ~ `main` metóda v Jave). Tento koreňový modul môže mať viacero komponentov s rôznymi oddelenými funkciami. Funkcia modulov je rozdeliť aplikáciu do určitých logických častí (kontajnerov), ktoré zastávajú nejakú úlohu.


*Príklad koreňového modulu:*

```typescript
import { NgModule } from '@angular/core';
import { BrowserModule } from '@angular/platform-browser';
import { FormsModule } from '@angular/forms';

import { AppComponent } from './app.component';

@NgModule({
  imports:      [ BrowserModule, FormsModule ],
  declarations: [ AppComponent ],
  bootstrap:    [ AppComponent ]
})
export class AppModule { }
```

------

## Čo potrebujeme?

1. IDE

	* [Jetbrains WebStorm](https://www.jetbrains.com/webstorm/) - študentská licencia na požiadanie

	* [Visual Studio Code](https://code.visualstudio.com/)

	* online editory
 		* [Plunker](https://plnkr.co/)
 		* [Stackblitz](https://stackblitz.com)

2. [Node.js a NPM](https://nodejs.org/en/download/)

3. [TypeScript](https://www.typescriptlang.org/)

```
npm install –g typescript
```

4. [Angular Quickstart](https://github.com/angular/quickstart) alebo [Angular CLI](https://cli.angular.io/) - Command Line Interface (zostavovač Angular projektu)

```
npm install -g angular-cli
```

5. Template - kostra projektu

```
ng new PROJECT_NAME
```

6. Bootstrap (nie je nutnosť)

```
npm install bootstrap@next
```

------

## Typescript

* nadstavba JavaScriptu 
* OOP programovanie (existencia tried)
* črty Javy a C/C++
* od Microsoftu

[Základné dátové typy v Typescripte](https://www.typescriptlang.org/docs/handbook/basic-types.html)

```typescript
export class ClassName {
   propertyName: propertyType = Value;
}
```

```typescript
import { Component } from '@angular/core';

// Metadata
@Component ({ 
   selector: 'my-app',  					
   templateUrl: 'app/app.component.html'    
}) 

export class AppComponent {					// zadefinovali sme triedu s názvom AppComponent
											// "export" umožňuje použitie komponentu aj v iných moduloch našej aplikácie
   appTitle: string = 'Welcome';			
}
```

*Príklad OOP v Typescripte:*

```typescript
class Student {
 meno:string;
 vek: number;

 constructor(meno:string, vek:number = 19) {
	this.meno = meno;
	this.vek = vek;
 }

 povedzMenoAVek(musis:boolean): string {
	if (musis) return meno+” “ + vek;
	else return “nepoviem”;
 }}

 let jano= new Student(“Jano”);
 let janoPovedal = jano.povedzMenoAVek(true); // “Jano 19”
```

*Ukážka č. 1: [**link**](https://stackblitz.com/edit/angular-sps-1)*

*Ukážka č. 2: tvorba nového komponentu*

## Direktívy

Direktívy sú prvky jazyka HTML, ktoré sú súčasťou BrowserModule modulu a obohacujú prácu s HTML.

* ***ngIf**

```html
*ngIf = 'expression'
```

```html
<p *ngIf="courses.length > 3">There are many courses!</p>
```

* ***ngFor**

```html
*ngFor = 'let variable of variablelist'
```

```html
<p>Courses:</p>
  <ul>
    <li *ngFor="let course of courses">{{ course }}</li>
  </ul>
```

* **[(ngModel)]** - prepájanie prvkov vo formulároch (input, select, textarea) s dátami aplikácie (napr. premennými)

```html
<form >
  <label>Name:</label>
  <input type="text"  name="name" [(ngModel)]="name"><br/>
</form>
```

*Ukážka č. 3: využitie direktív*

-----

## Úlohy

**Použite túto predpripravenú verziu nového projektu: [link](https://stackblitz.com/edit/angular-sps-ulohy-template)**

### 1. úloha

V adresári *app/components/* vytvorte nový komponent s názvom **review-form**, triedou ReviewForm a jemu prislúchajúcou HTML šablónou. Nezabudnite na **importy v koreňovom module**!

Časť HTML kódu v **app.component.html**, ktorá reprezentuje formulár vystrihnite a vložte do novej HTML šablóny **review-form.component.html**. Vystrihnuté miesto v šablóne **app.component.html** nahradťe tagmi tak, aby sa formulár načítal už z nového komponentu **review-form**.

### 2. úloha

V triede ReviewForm **vytvorte novú triedu "Recenzia"** s premennými "nazov" a "text" recenzie. **Deklarujte pole**, ktoré bude reprezentovať pole pridaných recenzií. [**Inicializujte**](https://stackoverflow.com/a/45285236/6394810) toto pole **ako prázdne**!

### 3. úloha

Vytvorte metódu **getRecenzia(nazov:string, text:string)**, ktorá z vyplneného formulára načíta názov a text recenzie a vloží novú recenziu do poľa komentárov.

### 4. úloha

Do komponentu **review-form** pridajte výpis všetkých pridaných recenzií. Využite neusporiadaný zoznam (*ul*), prípadne tieto recenzie namapujte do tabuľky. Pre túto funkcionalitu môžete vytvoriť samostatný komponent, ktorý bude tieto recenzie vypisovať.

