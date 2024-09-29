```
Project         : Tutorial Server Project Legekrogen
Formål          : App - Routes
Live Server     : https://legekrogen-v2.webmcdm.dk
```

```javascript
import { useRoutes } from "react-router-dom";

// Common Pages.
import HomePage from "./pages/home/HomePage";
import Navigation from "./components/common/Navigation/Navigation";
import Footer from "./components/common/Footer/Footer";
import ProductsPage from "./pages/products/ProductsPage";
import ReviewsPage from "./pages/reviews/ReviewsPage";
import SubscribersPage from "./pages/subscribers/SubscribersPage";
import ProductPage from "./pages/product/ProductPage";
import BackofficePage from "./pages/backoffice/BackofficePage";
import BackofficeProductsPage from "./pages/backoffice/pages/BackofficeProductsPage";
import BoProductsForm from "./components/backoffice/Products/outlet/BoProductsForm";

// Application
const App = () => {

  // Setting Up Routes
  const routes = useRoutes([
    {
      path: "/",
      element : <HomePage></HomePage>
    },
    {
      path: "/products",
      element : <ProductsPage></ProductsPage>
    },
    {
      path: "/products/:id",
      element : <ProductPage></ProductPage>
    },
    {
      path: "/backoffice",
      element : <BackofficePage></BackofficePage>,
      children : [
        {
          path: "/backoffice/products",
          element : <BackofficeProductsPage></BackofficeProductsPage>,
          children : [
            {
              path: "/backoffice/products/add",
              element : <BoProductsForm></BoProductsForm>
            },
            {
              path: "/backoffice/products/edit/:id",
              element : <BoProductsForm></BoProductsForm>
            }
          ]
        },
        {
          path: "/backoffice/subscribers",
          element : <div>SUBSCRIBERS</div>
        },
        {
          path: "/backoffice/reviews",
          element : <div>REVIEWS</div>
        }
      ]
    },
    {
      path: "/reviews",
      element : <ReviewsPage></ReviewsPage>
    },
    {
      path: "/subscribers",
      element : <SubscribersPage></SubscribersPage>
    },
    {
      path: "*",
      element : <div>NOT 404 FOUND</div>
    },
  ]);

  return <>
    <div>
        <Navigation></Navigation>
        <div className="globale-page-wrapper">
            {routes}
        </div>
        <Footer></Footer>
    </div>
  </>;

}

export default App;

```