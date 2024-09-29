```
Project         : Tutorial Server Project Legekrogen
Formål          : Footer
Live Server     : https://legekrogen-v2.webmcdm.dk
```

`/common/backoffice/Products/outlet/BoProductsForm.jsx`
```javascript

import { useEffect, useRef, useState } from "react";
import { useOutletContext, useParams } from "react-router-dom";

const BoProductsForm = () => {

    const formRef = useRef();
    const [products, addProduct, updateProduct] = useOutletContext();
    const [editMode, setEditMode] = useState(false);
    const [product, setProduct] = useState(null)
    const [image, setImage] = useState('http://localhost:3042/products/no-product.jpg')
    const {id} = useParams();

    useEffect( () => {

        if(id) {

            let product = products.filter( (p) => p._id === id)[0];

            if( product ) {

                let form = formRef.current;
                form.title.value = product.title;
                form.description.value = product.description;
                form.price.value = product.price;
                form.discountInPercent.value = product.discountInPercent;
                form.recommended.checked = product.recommended;

                setImage(product.image)
                setProduct(product)
                setEditMode(true)

            }
  
        } else {

            setEditMode(false)
        }

    }, [id])

    
    const onImageChange = (e) => {
        
 
        let objectUrl = window.URL.createObjectURL(e.target.files[0])
        setImage(objectUrl)
       
    }   


    const onHandleSubmit = (e) => {

        e.preventDefault();

        const {title, price} = e.target.elements

        let formData = new FormData(e.target);
        let recommendedChecked = formData.get('recommended') === "on" ? true : false;

        formData.set('recommended', recommendedChecked);


        if(editMode) {

            formData.append('id', product._id)

        }


        editMode ? updateProduct(formData) : addProduct(formData)
    }


    return (
        <div>
            <h2>{editMode ? "Redigér Produkt" : "Opret Product" }</h2>
            <form onSubmit={onHandleSubmit} ref={formRef}>
                <label>
                    <img src={image} width={150}></img>
                    <input type="file" name={'file'} onChange={onImageChange}></input>
                </label>

                <label> Title 
                    <input type="text" name={'title'} defaultValue={`Default Produkt`}></input>
                </label>

                <label> Description
                    <input type="text" name={'description'} defaultValue={'Default Produkt Beskrivelse'}></input>
                </label>

                <label> Price
                    <input type="number" name={'price'} defaultValue={200}></input>
                </label>

                <label> Discount in Percent
                    <input type="range" min={0} max={100} name={'discountInPercent'} defaultValue={50}></input>
                </label>

                <label> Recommended
                    <input type="checkbox" name={'recommended'} defaultChecked={true}></input>
                </label>

                <button>{editMode ? "Redigér Produkt" : "Opret Product" }</button> <button type="reset">RESET</button>

            </form>
        </div>
    );

};
export default BoProductsForm;
```