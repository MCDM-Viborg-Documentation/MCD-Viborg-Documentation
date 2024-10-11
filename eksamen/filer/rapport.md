# Rapport Spørgsmål.

## Vurdering af din egen indsats og gennemførelse af prøven

En vurdering af din egen fremgang og indsats

## Argumentation for de valg du har truffet under løsningen af opgaven.

Hvorfor benytter du React eller lign


## Redegørelse for oprindelsen af de forskellige kodeelementer i

Har du benyttet noget smart der ligger uden for det vi har brugt og hvor benytter du det fra.

F.eks. React Swiper, React Hooks som er eksterne


## Eksemple på PrintJson Komponent. Beskrivelse

Dett komponent udskrive JSON data som Debug og benyttes i frontenden til at få "hul igennem" til data´en.

Dette komponent tage imod 2 properties

1. jsonobj
2. headline.

```javascript
import styles from './printJson.module.css';
const PrintJson = ({jsonobj, headline = ''}) => {

    // Hvis der er en overskrift så udskriver vi den!
    const printHeadline = headline !== '' ? <p>{headline}</p> : null

    return (
        <div>

            {printHeadline}

            <pre className={styles.printJson}>
                {JSON.stringify(jsonobj, null, 2)}
            </pre>
        </div>
    )
};
export default PrintJson;
```

## Dette er noget css der er specielt - kunne være brug af variabler osv - hvis du vil fremhæve det.

```css
.class {
    color : "red"
}
```