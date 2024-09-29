```
Project         : Tutorial Server Project Legekrogen
Formål          : Product List
Live Server     : https://legekrogen-v2.webmcdm.dk
```

`/common/backoffice/Products/lists/BoProductList.jsx`
```javascript
import { useNavigate } from "react-router-dom";
import styles from './boProductList.module.css'
const BoProductList = ({products, deleteProduct}) => {


    const navigate = useNavigate();

    const editProduct = (id) => {

        navigate(`/backoffice/products/edit/${id}`)
    }

    const createProduct = () => {

        navigate(`/backoffice/products/add`)
        
    }

    return (
        <div className={styles.list}>
            
            <table>
                <thead>
                    <tr>
                        <th>image</th>
                        <th>title</th>
                        <th>description</th>
                        <th>price</th>
                        <th>discountInPercent</th>
                        <th>recommended</th>
                        <th>Actions</th>
                    </tr>
                </thead>
                <tbody>

                    {products.map( (product) => {

                        let { _id, image, title, description, price, discountInPercent, recommended } = product;

                        return (<tr key={_id}>
                                <td><img src={image}></img></td>
                                <td>{title}</td>
                                <td>{description}</td>
                                <td>{price}</td>
                                <td>{discountInPercent}</td>
                                <td>{recommended ? 'Anbefalet' : 'Kataloget'}</td>
                                <td className={'table-actions'}>
                                    <button onClick={() => editProduct(_id)}>REDIGÈR</button>
                                    <button onClick={() => deleteProduct(_id)}>SLET</button>
                                </td>
                            </tr>
                        )

                    })}

                </tbody>
            </table>
            <button onClick={createProduct}>OPRET</button>
        </div>
    );
};
export default BoProductList;
```

`/common/backoffice/Products/lists/boProductList.module.css`
```css
.list {
    overflow-x:auto;
}
```