# AK8PO

## Popis práce
Firma Zaslat s.r.o. potřebuje na svých stránkách vytvořit modul pro zobrazení ceny přepravy do všech států.
Ceny musí být reálně brané z API dopravců a musí být uvedeny pro různé váhy balíků.
Ceny nebudou kvůli rychlosti načítané při každém načtení stránky ceníku, ale budou ukládany do cache databáze.
Pro nejnavštěvovanější ceníky pak bude platnost cache 1 den. Pro méně navštěvované týden a pro zbytek zemí světa měsíc.
Samotné načtení do cache je pak řešeno pomocí databázové queue, aby byla zajištěna plynulost načítání.
Pro každou váhu pak bude zobrazena nejlevnější cena dopravy a také dopravce, který tuto cenu poskytuje.

## Požadavky
- Ceník pro import i export každé země je načítán asynchronně do cache a zobrazuje se nacachovaná cena přepravy.  
- Ceníky obsahují předem dodané texty o konkrétní zemi.  
- Načítání ceníků probíhá asynchronně pomocí queue a po vypršení platnosti cache se do queue zařadí další požadavek na opětovné načtení ceníku.  
- Ceníky jsou načítány z api dopravců, nebo přímo z uložených cen v db.

## Použité technologie
- php 8.0 (framework yii2)
- Vue.js
- MySQL
- Redis
- Rest API
- CSS
- HTML
- Docker
- Cypress

## Časový plán
- Výzkum dostupných technologií 3h
- Výzkum API dopravců pro získání cen 5h
- Implementace cache 4h
- Implementace queue pro zpracování cache ceníků 3h
- Implementace napojení na API dopravců 10h
- Grafická reprezentace ceníků 5h
- Grafické úpravy stránek ceníku 7h
- Implementace invalidace cache podle určených pravidel 3h
- Testování správnosti cen 4h
- Implementace základních E2E testů pro nejpoužívanější ceníky 3h