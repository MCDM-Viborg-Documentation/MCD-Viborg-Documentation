```
Project         : Tutorial Server Project Legekrogen
Formål          : "Printer" et JSON Object i dom´en.
Live Server     : https://legekrogen-v2.webmcdm.dk
```

`PrintJson.jsx`
```javascript
import styles from './printJson.module.css';

const PrintJson = ({jsonobj, headline = ''}) => {

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

`printJson.module.css`
```css
.printJson {
    padding: 20px;
    border : dotted 1px var(--mc-color-green)
}
```