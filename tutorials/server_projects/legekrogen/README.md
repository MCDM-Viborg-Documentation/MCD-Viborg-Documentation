```
Project         : Server Project Legekrogen
Formål          : Sådan arbejder du med server projekter.
Live Server     : https://legekrogen-v2.webmcdm.dk
```

# Functional Prototyping Legekrogen

Link til videos : https://legekrogen-v2.webmcdm.dk/www/

Dette er en tutorial i at arbejde med et at vores server projekter. Du kan med fordel starte med at hoppe over og se [Video Tutorials](https://legekrogen-v2.webmcdm.dk/www/) og det vil ikke være dumt at se de første par stykker og først derefter selv begynde at kode og se dem igen.

Derudover anbefaler jeg at du læser dette dokument igennem også. - det er hurtigt overstået :)

**Normalt**:
1. Du henter en server og installere og fylder databasen med data.
2. Du får en kravsspecifikation, figma og adgang til api´et.
3. Du gør dit aller-bedste for at lave en lækker fronteend og alle er glade :)

**I denne tutorial**
1. Du starter med at se en video.

## Forudsætninger.

1. Du skal have MongoDB/Compass installeret.
2. Du skal have POSTman installeret.
3. Visual-Code og alt der der.

## Komponenter.

Der vil blive brugt komponeter som vi ikke bruger så meget tid på at forklare og vi indsætter dem løbende.

F.eks.
[PrintJSON](./components/common/PrintJSON/printJson.md)
[Navigation](./components/common/Navigation/Navigation.md)
[Footer](./components/common/Footer/Footer.md)

men også sider og deres styles
[Products](./pages/products/ProductsPage.md)
[Reviews](./pages/reviews/ReviewsPage.md)
[Subscribers](./pages/subscribers/SubscribersPage.md)

Der er flere og alle er ikke listet her - Tag dem efterhånden som du følger med i videoerne.

## Forskellige Tutorials

Du kan starte med Basket videoerne da det hele gerne skulle være uafhængig af hinanden 
men **du bør se video 1 hvis du ikke** har serveren installeret.

### Server installation
Video 1

### CRUD Create, Read, Update og Delete tutorial
Video 2 til 11.

### Basket / Tilføj og fjern fra kurven og præsentér produkter
Video 12 til 15.

## Kildefiler.

I mappen "sources", i dette repsositorie, ligger der kildefiler.

Start med at hente `mcd_web_legekrogen_server.zip` og `mcd_legekrogen_tutorial_crud_client_starter.zip`.

## Server (bemærk serveren kan blive opdateret så hent gerne den nyeste her.)

Alle zip filerne ligger i dette repo under "sources" mappen.

**Server**
`mcd_web_legekrogen_server.zip`

## CRUD 
**Products Starter klient template**
`mcd_legekrogen_tutorial_crud_client_starter.zip`

**Products implementeret, klient template**
`mcd_legekrogen_tutorial_crud_client_products.zip`

## Basket
**Basket Starter klient template**
`mcd_legekrogen_tutorial_basket_client_starter.zip`

**Basket implementeret, klient template (uden egen hook)**
`mcd_legekrogen_tutorial_basket_client_solution.zip`

