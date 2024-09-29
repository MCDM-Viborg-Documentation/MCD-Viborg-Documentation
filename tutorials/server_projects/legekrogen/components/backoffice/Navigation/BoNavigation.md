```
Project         : Tutorial Server Project Legekrogen
Formål          : Backoffice Navigation
Live Server     : https://legekrogen-v2.webmcdm.dk
```

`/common/backoffice/Navigation/BoNavigation.jsx`
```javascript
import { Link, NavLink } from 'react-router-dom';
import styles from './bonavigation.module.css'
import { icons } from '../../../services/icons';

const BoNavigation = () => {

    return (
        <div className={styles.navigation}>
            <div className={styles.brand}>
                <Link to={"/"} className={styles.banner}>
         
                   Backoffice Navigation
                
                </Link>
            </div>
            <div>
                <div className={styles.routes}>

                    <NavLink to="/backoffice/products" className={({ isActive }) => (isActive ? styles.active : null)}>

                        {icons['FaProductHunt']}  <span className={styles.title}>Backoffice Products</span>

                    </NavLink>

                    <NavLink to="/backoffice/subscribers" className={({ isActive }) => (isActive ? styles.active : null)}>

                        {icons['FaProductHunt']}  <span className={styles.title}>Backoffice Subscribers</span>

                    </NavLink>
                    
                </div>

            </div>
        </div>
    );

};
export default BoNavigation;
```

`/common/backoffice/Navigation/bonavigation.module.css`
```css
.navigation {

    padding: 40px 20px;
    display: flex;
    align-items: center;
    justify-content: space-between;
    position: relative;
    overflow: hidden;
    gap : 20px;
    /* background-color: var(--mc-color-green); */
    border-bottom: solid 1px rgba(255, 102, 52, .3);
    background-color: black;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
    height : 80px;

    .brand {
       
        
        img {
            user-select: none;
            width: 180px;
        }

        .banner {
            text-decoration: none;
            color : #fff;
            width: 270px;
            text-align: center;
            user-select: none;
            font-size: 2.2rem;;
        }
    }


    .routes {
        display: flex;
        align-items: center;
        justify-content: left;
        gap:20px;

        a {
            transition: all 500ms;
            text-decoration: none;
            
            color : #fff;
            border-top: 3px solid transparent;
            border-bottom: 3px solid transparent;

            display: flex;
            justify-content: center;
            align-items: center;
            gap : 6px;
            padding: 6px 6px;
            
            .title {
                display: none;
               
            }

            &.active {
                
               
                border-top: 3px solid #fff;
                border-bottom: 3px solid #fff;
                color : #fff;
                svg {
                    color : #fff;
                }
            }

            &:hover {

                border-bottom: 3px solid #fff;
                color : #fff;

            }
    

        }

    }

}

@media (min-width: 700px) {

    .navigation {
        .routes { 
            a {
                .title {
                    display: inline;
                }
            }
        }
    }

}
```