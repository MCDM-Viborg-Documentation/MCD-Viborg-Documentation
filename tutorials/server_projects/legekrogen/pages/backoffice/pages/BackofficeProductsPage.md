```
Project         : Tutorial Server Project Legekrogen
Formål          : Backoffice Products Page
Live Server     : https://legekrogen-v2.webmcdm.dk
```

`/pages/backoffice/pages/BackofficeProductsPage.jsx`
```javascript
import { useEffect, useState } from "react";
import BoProductList from "../../../components/backoffice/Products/lists/BoProductList";
import useTinyFetch from "../../../hooks/tinyFetch.hook";
import { Outlet } from "react-router-dom";

const BackofficeProductsPage = () => {

    const [products, setProducts] = useState([]);
    const {data, fetchData} = useTinyFetch();

    useEffect( () => {

        fetchData('/products')

    },[])

    useEffect( () => {

        setProducts(data);

    },[data])

    const addProduct = (formData) => {

        const addNewProduct = async (formData) => {

            let response = await fetch('http://localhost:3042/product', {
                "method" : "POST",
                "body" : formData
            })
            const result = await response.json();
            let newProduct = result.data;

            if(result.status === "ok") {

                setProducts([
                    ...products,
                    newProduct

                ])

            } else {

                setProducts([
                    ...products,
                ])

            }
         

        }


        addNewProduct(formData)

    }

    const deleteProduct = (id) => {

        const delProduct = async () => {

            await fetch(`http://localhost:3042/product/${id}`, {
                "method" : "DELETE"
            })

            let updatedList = products.filter( (p) => p._id !== id)

            setProducts([
                ...updatedList,
            ])
        }

        delProduct(id)

    }

    const updateProduct = (formData) => {

        const editProduct = async (formData) => {

            let response = await fetch('http://localhost:3042/product', {
                "method" : "PUT",
                "body" : formData
            })

            const result = await response.json();
            let productId = formData.get('id');
            let index = products.findIndex( (p) => p._id === productId)
            console.log(index, formData.get('id'), result.data)


            products[index] = result.data;

            setProducts([
                ...products,
            ])


        }

        editProduct(formData)


    }


    return (
        
        <div>
        
            <BoProductList products={products} deleteProduct={deleteProduct}></BoProductList>
            <br/><br/>
            <Outlet context={[products, addProduct, updateProduct]}></Outlet>
        </div>

    );
};
export default BackofficeProductsPage;
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