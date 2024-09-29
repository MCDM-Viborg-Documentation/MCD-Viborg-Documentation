```
Project         : Tutorial Server Project Legekrogen
Formål          : Backoffice Page
Live Server     : https://legekrogen-v2.webmcdm.dk
```

`/pages/backoffice/BackofficePage.jsx`
```javascript
import styles from './footer.module.css'
const Footer = () => {
    return (
        <div className={styles.footer}>
            2024 WEB
        </div>
    );
};

export default Footer;
```

`/pages/backoffice/backofficePage.module.css`
```css
.page {
    .outlet {
        background-color: var(--mc-color-orange);
        padding : 40px 20px;
        color : #fff;
    }
}
```