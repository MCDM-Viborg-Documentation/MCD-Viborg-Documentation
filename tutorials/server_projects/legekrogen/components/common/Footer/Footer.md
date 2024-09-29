```
Project         : Tutorial Server Project Legekrogen
Formål          : Footer
Live Server     : https://legekrogen-v2.webmcdm.dk
```

`/common/Footer/Footer.jsx`
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

`/common/Footer/footer.module.css`
```css
.footer {
    text-align: center;
    padding: 20px 0;
    background-color: var(--mc-color-green);
    width: 100%;;
    color : #fff;
    height : 60px;
}
```