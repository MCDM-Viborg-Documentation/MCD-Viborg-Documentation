```
Project         : Tutorial Server Project Legekrogen
Formål          : Navigation
Live Server     : https://legekrogen-v2.webmcdm.dk
```

`/common/(Navvigation/Navigation.jsx`
```javascript
import { Link, NavLink } from 'react-router-dom';
import styles from './navigation.module.css'
import { icons } from '../../../services/icons';
const Navigation = () => {

    return (
        <div className={styles.navigation}>
            <div className={styles.brand}>
                <Link to={"/"} className={styles.banner}>
         
                   Functional Prototype
                
                </Link>
            </div>
            <div>
                <div className={styles.routes}>

                    <NavLink to="/" className={({ isActive }) => (isActive ? styles.active : null)}>

                        {icons['FaHouse']}  <span className={styles.title}>HOME</span>

                    </NavLink>

                    <NavLink to="/products" className={({ isActive }) => (isActive ? styles.active : null)}>

                        {icons['FaProductHunt']} <span className={styles.title}>PRODUCTS</span>

                    </NavLink>

                    <NavLink to="/reviews" className={({ isActive }) => (isActive ? styles.active : null)}>

                        {icons['FaCircleUser']} <span className={styles.title}>REVIEWS</span>

                    </NavLink>

                    <NavLink to="/subscribers" className={({ isActive }) => (isActive ? styles.active : null)}>

                        {icons['FaBullseye']} <span className={styles.title}>SUBSCRIBERS</span>

                    </NavLink>

                </div>

            </div>
        </div>
    );

};
export default Navigation;
```

`/common/(Navvigation/navigation.module.css`
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

    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
    height : 80px;
    .brand {
       
        
        img {
            user-select: none;
            width: 180px;
        }

        .banner {
            text-decoration: none;
            color : var(--mc-color-green);
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
            
            color : rgba(255, 102, 52, .6);
            border-top: 3px solid rgba(255, 102, 52, .6);
            border-bottom: 3px solid rgba(255, 102, 52, .6); 

            display: flex;
            justify-content: center;
            align-items: center;
            gap : 6px;
            padding: 6px 6px;
            
            .title {
                display: none;
               
            }

            &.active {
                
               
                border-top: 3px solid var(--mc-color-green);
                border-bottom: 3px solid var(--mc-color-green);
                color : var(--mc-color-green);
                svg {
                    color : var(--mc-color-green);
                }
            }

            &:hover {

                border-bottom: 3px solid var(--mc-color-green);
                color : var(--mc-color-green);

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