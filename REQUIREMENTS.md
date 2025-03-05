# API Requirements

The company stakeholders want to create an online storefront to showcase their great product ideas. Users need to be able to browse an index of all products, see the specifics of a single product, and add products to an order that they can view in a cart page. You have been tasked with building the API that will support this application, and your coworker is building the frontend.

These are the notes from a meeting with the frontend developer that describe what endpoints the API needs to supply, as well as data shapes the frontend and backend have agreed meet the requirements of the application.

## API Endpoints

### Products

- Index: `/products`[GET]
- Show: `/products:id`[GET]
- Create `/products`[POST] [token required]
- Top 5 most popular products: `/products/popular`[GET]
- Products by category (args: product category): `/products/category/:category`[GET]

### Users

- Index: `/users` [GET] [token required]
- Show: `/users/:id` [GET] [token required]
- Create: `/users` [POST]

### Orders (Routes)

- Current Order by user (args: user id) `/orders/current/:user_id`[GET] [token required]
- Completed Orders by user (args: user id) `/orders/completed/:user_id`[GET] [token required]

## Data Shapes

### Product

- id: SERIAL PRIMARY KEY
- name: VARCHAR(100) NOT NULL
- price: DECIMAL(10,2) NOT NULL
- category: VARCHAR(50)

### User

- id: SERIAL PRIMARY KEY
- firstName: VARCHAR(50) NOT NULL
- lastName: VARCHAR(50) NOT NULL
- password: VARCHAR(255) NOT NULL

### Orders (Models)

- id: SERIAL PRIMARY KEY
- product_id: INTEGER [foreign key to products table]
- quantity: INTEGER NOT NULL
- user_id: INTEGER [foreign key to users table]
- status: VARCHAR(15) NOT NULL CHECK (status IN ('active', 'complete'))
