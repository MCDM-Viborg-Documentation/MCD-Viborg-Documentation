```
Project         : Tutorial Server Project Legekrogen
Formål          : Reviews Page
Live Server     : https://legekrogen-v2.webmcdm.dk
```

`/components/products/Reviews/Review.jsx`
```javascript
import { useEffect, useState } from 'react';
import styles from './reviews.module.css'
import PrintJson from '../../common/PrintJSON/PrintJson';
import useTinyFetch from '../../../hooks/tinyFetch.hook';


const Review = ({review}) => {

    return <div className={styles.review}>
        
        <PrintJson jsonobj={review} headline={review.name}></PrintJson>
        
    </div>

}

const ReviewsList = ({reviews}) => {

    return (
        <div className={styles.list}>

            {reviews.map( (review) => {

                return <Review key={review._id} review={review}></Review>

            } )}

        </div>
    )

}

const Reviews = () => {

    const [reviews, setReviews] = useState([]);
    const {data, fetchData} = useTinyFetch()

    
    useEffect( () => {

        fetchData('/reviews');

    }, [])

    useEffect( () => {

        setReviews(data)
        
    }, [data])

    return (
        <div className={styles.reviews}>
            <ReviewsList reviews={reviews}></ReviewsList>
        </div>
    );
};
export default Reviews;
```

`/components/products/Reviews/reviews.module.css`
```css
.reviews {

    padding : 20px;

    .review {
        padding : 20px;
        border : 2px dashed var(--mc-color-orange); 
        width:100%;
    }

    .list {

        display: flex;
        flex-wrap: wrap;
        gap : 20px;

    }

}
```