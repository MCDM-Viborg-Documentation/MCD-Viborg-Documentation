```
Project         : Tutorial Server Project Legekrogen
Formål          : "Fetcher" GET data fra serveren.
Live Server     : https://legekrogen-v2.webmcdm.dk
```

```javascript
const useTinyFetch = () => {

    
    const [data, setData] = useState([]);


    const fetchData = async (url) => {

        const response = await fetch(url);
        const result = await response.json();
        setData(result.data);


        return result
    }

    return {
        data,
        fetchData
        
    }
};
export default useTinyFetch;
```