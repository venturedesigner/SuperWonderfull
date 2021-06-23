![](https://user-images.githubusercontent.com/970858/63474771-d6734700-c469-11e9-83bb-9429da563909.png)

# Express | VUE SHOPPING CART

## Introduction

> ***Note:*** _This can be a pair programming activity or done independently._

## Learning Goals

After this learning unit, you will be able to:

- Structure a vue app using components
- Communicate between components using events and props
- Use the Event Bus to communicate components directly

## Requirements

- [Fork this repo](https://guides.github.com/activities/forking/)
- Clone this repo into your `~/code/labs`

## Deliverables

Please, push every file needed to make your app properly on GitHub before creating the pull request.

## Introduction

This project will consist on creating a **Mr Superwornderful**, a supermarket based on Rr Wonderful branding.

Here is the [Vue Guide](https://vuejs.org/v2/guide/) in case you need it

## Structuring your vue app

The vue app will consist on the following components:

- App.vue will be the Parent Component of the App
- ProductCard will display the information of ONE given product
- ProductList will display a card for all given products
- Cart will store how much items are added to cart and whats the total value of those items
- SearchBar [BONUS] will have an input and a button, when something is introduced or the button is clicked, it will filter the products that show

```
/src
    App.vue
    /components
        Cart.vue
        ProductList.vue
        ProductCard.vue
        SearchBar.vue
```


## Iteration 1 - Load All Products

Create a new Vue app. Move the `products.json` into the **assets** folder and load it on the App.vue component. Create the ProductList and ProductCard Components in order to display all the products. The products should be loaded on the App.vue, then passed as an array through props to the ProductList.

The productList should then create a productCard for each item in the list an pass each product through props to its card.

## Iteration 2 - Create a cart

Create the cart component. It should display:

- a counter indicating how many elements there are in the cart
- the total value of the cart

Both values should be passes as props from the app.vue component

## Iteration 3 - Add a product

Add a button on the product card component that adds that product to the cart. To do so, it should notify the app.vue through event emitters. **Dont use the Event Bus**

## Iteration 4 - Wipe the cart

Add a button on the product card component that deletes all the products on the cart. This should reset both the counter and the total price. To do so, it should notify the app.vue through event emitters. **Dont use the Event Bus**

## Iteration 5 - Filter

Filter the products using a searchbar. It should only show the products that **include** the letters introduced. Notify the Product list using the `Event Bus`

## BONUS - Style Mr SuperWonderful

## Submission

Upon completion, run the following commands:

```
$ git add .
$ git commit -m "done"
$ git push origin master
```

Then create a Pull Request!!


![happy_coding](https://user-images.githubusercontent.com/970858/63899010-c23fc480-c9ea-11e9-84a2-542907e42362.png)
