```
Project         : Tutorial Server Project Legekrogen
Formål          : Single Product Page
Live Server     : https://legekrogen-v2.webmcdm.dk
```

`/pages/product/ProductPage.jsx`
```javascript
import { useParams } from "react-router-dom"

const ProductPage = () => {

    const params = useParams();

    return (
        <div>
             <h1>Product Page {params.id}</h1>
        </div>
    )

}

export default ProductPage
```