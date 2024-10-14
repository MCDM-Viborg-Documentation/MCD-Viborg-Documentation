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
import { Link } from 'react-router-dom';
import { icons } from '../../../services/icons';

const Product = ({product}) => {

    return <div className={styles.product}>
        
        <img src={product.image} />
        <div className={styles.content}>
            
            <h3>{product.title}</h3>
            <p>{product.description}</p>
            <p>{product.price} kr.</p>
        </div>
        
    </div>

}

const DebugProduct = ({product}) => {

    return <div className={styles.debugProduct}>
    
        <PrintJson jsonobj={product} headline={product.title}></PrintJson>
        
        <Link to={`/products/${product._id}`}>Product Page</Link>
    </div>

}

const ProductList = ({products, debugMode}) => {

    return (
        <div className={styles.list}>
            
            {products.map( (product) => {

                return debugMode ? <DebugProduct key={product._id} product={product}></DebugProduct> : <Product key={product._id} product={product}></Product>

            } )}

        </div>
    )

}

const Products = () => {

    const [products, setProducts] = useState([]);
    const [debugMode, setDebugMode] = useState(true);
    const {data, fetchData} = useTinyFetch()

    useEffect( () => {

        fetchData('/products');

    }, [])

    useEffect( () => {

        setProducts(data)

    }, [data])

    return (

        <div className={styles.products}>
            <div className={styles.debugBtn} onClick={ () => setDebugMode(!debugMode)}>{icons["FaWrench"]} TOGGLE {debugMode ? 'PRODUCT' : 'DEBUG'} MODE</div>

           <ProductList products={products} debugMode={debugMode}></ProductList>

        </div>

    );
};

export default Products;
```
`/components/products/Product/products.module.css`
```css
.products {

    padding: 20px;

    .debugProduct {
        padding : 20px;
        border : 2px dashed var(--mc-color-green); 
        width:100%;
    }

    .product {
        background-color: rgb(148, 120, 168);
        width:100%;
        border-radius: 16px;

        .content {
            padding: 20px;

            color : #fff;
            border-radius: 0 0 16px 16px;
        }
        img {
            width : 100%;
            border-radius: 16px 16px 0 0;
            aspect-ratio: 1/1;
            object-fit: cover;
        }
    }

    .list {

        display: flex;
        flex-wrap: wrap;
        gap : 20px;

        > div {
            width: 100%;
        }
       
    }

    .debugBtn {
        background-color: black;
        width : 100%;
        color:#fff;
        display: flex;
        justify-content: center;
        align-items: center;
        gap: 10px;
        border-radius: 8px;
        padding: 10px;
        margin: 10px 0;
        cursor: pointer;
    }
    
    @media(min-width:768px) {
       .list {

            > div {
                width: calc(50% - 10px);
            }

       }

    }

    @media(min-width:1024px) {
        .list {
 
             > div {
                 width: calc(25% - 15px);
             }
 
        }
 
     }

     @media(min-width:1224px) {
        .list {
 
             > div {
                 width: calc(20% - 16px);
             }
 
        }
 
     }
}

.debugBtn {
    background-color: black;
    width : 300px;
    color:#fff;
    display: flex;
    justify-content: center;
    align-items: center;
    gap: 10px;
    border-radius: 8px;
    padding: 10px;
    margin: 10px 0;
    cursor: pointer;
}
```