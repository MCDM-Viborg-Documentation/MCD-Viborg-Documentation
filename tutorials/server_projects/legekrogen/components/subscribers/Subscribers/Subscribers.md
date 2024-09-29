```
Project         : Tutorial Server Project Legekrogen
Formål          : Reviews Page
Live Server     : https://legekrogen-v2.webmcdm.dk
```

`/components/products/Subscribers/Subscribers.jsx`
```javascript
import { useEffect, useState } from 'react';
import PrintJson from '../../common/PrintJSON/PrintJson';
import styles from './subscribers.module.css'
import useTinyFetch from '../../../hooks/tinyFetch.hook';

const Subscriber = ({subscriber}) => {

    return <div className={styles.subscriber}>
        
        <PrintJson jsonobj={subscriber} headline={subscriber.name}></PrintJson>
        
    </div>

}

const SubscribersList = ({subscribers}) => {

    return (
        <div className={styles.list}>

            {subscribers.map( (subscriber) => {

                return <Subscriber key={subscriber._id} subscriber={subscriber}></Subscriber>

            } )}

        </div>
    )

}

const Subscribers = () => {

    const [subscribers, setSubscribers] = useState([]);
    const {data, fetchData} = useTinyFetch();

    useEffect( () => {

        fetchData('/subscribers');

    }, [])

    useEffect( () => {

        setSubscribers(data)
        
    }, [data])

    return (
        <div className={styles.subscribers}>
            <SubscribersList subscribers={subscribers}></SubscribersList>
        </div>
    );

};
export default Subscribers;
```

`/components/products/Subscribers/subscribers.module.css`
```css
.subscribers {

    padding : 20px;

    .subscriber {
        padding : 20px;
        border : 2px dashed var(--mc-color-yellow); 
        width:100%;
    }

    .list {

        display: flex;
        flex-wrap: wrap;
        gap : 20px;

    }

}
```