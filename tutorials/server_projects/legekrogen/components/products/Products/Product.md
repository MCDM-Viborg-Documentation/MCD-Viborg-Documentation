```
Project         : Tutorial Server Project Legekrogen
Formål          : Product Page
Live Server     : https://legekrogen-v2.webmcdm.dk
```

`/components/products/Product/Products.jsx`
```javascript
import { useEffect, useState } from 'react';
import styles from './products.module.css'
import PrintJson from '../../common/PrintJSON/PrintJson';
import useTinyFetch from '../../../hooks/tinyFetch.hook';

const Product = ({product}) => {

    return <div className={styles.product}>
    
        <PrintJson jsonobj={product} headline={product.title}></PrintJson>
        
    </div>

}

const ProductList = ({products}) => {

    return (
        <div className={styles.list}>

            {products.map( (product) => {

                return <Product key={product._id} product={product}></Product>

            } )}

        </div>
    )

}

const Products = () => {

    const [products, setProducts] = useState([]);
    const {data, fetchData} = useTinyFetch()

    useEffect( () => {

        fetchData('/products');

    }, [])

    useEffect( () => {

        setProducts(data)

    }, [data])

    return (

        <div className={styles.products}>


           <ProductList products={products}></ProductList>


        </div>

    );
};

export default Products;
```
`/components/products/Product/products.module.css`
```css
.products {

    padding : 20px;

    .product {
        padding : 20px;
        border : 2px dashed var(--mc-color-green); 
        width:100%;
    }

    .list {

        display: flex;
        flex-wrap: wrap;
        gap : 20px;

    }

}
```