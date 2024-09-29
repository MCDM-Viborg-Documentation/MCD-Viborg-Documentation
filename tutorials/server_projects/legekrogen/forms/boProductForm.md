
```javascript
<form>
    <label>
        <img src={""} width={150}></img>
        <input type="file" name={'file'}></input>
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

    <button>FORM KNAP</button>

</form>
```