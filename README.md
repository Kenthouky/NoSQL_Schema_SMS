# NoSQL  Schema Design for a Shopping App

## User Story

As a shopper, I want to be able to browse a catalog of products and add items to my shopping cart. I also want to be able to view the contents of my cart and adjust the quantity of items in my cart. Finally, I want to be able to place an order and recieve confirmation of my order.

## Requirements Analysis

### Entities:

- Products: The products is basically a catalogue for the shopper to browse through. Every product has a name, description, price, and category.
- Shopper: Every shopper has unique identifiers, which for this case are name, email and password.
- Orders: Each order has unique identifiers - the shopper who placed it, list of products, and the total amount.

### Relationships:

- A shopper can view the products, and place an order.
- An order can contain many products.

## NoSQL Schema Design

Based on the requirements analysis, the following schema was designed:

### Shoppers Collection:
```
{
	_id: ObjectId,
	name: string,
	email: string,
	password: string
}
```

### Products Collection
```
{
	_id: ObjectId,
	name: string,
	description: string,
	price: number,
	categories: [string]
}
```

### Orders Collection
```
{
	_id: ObjectId,
	shopperId: ObjectId,
	products: [
		{
		productID : ObjectId,
		quantity: number
		}
	],
	totalAmount: number,
	status: string,
	orderDate: date,
	deliveryAddress: string
}
```

## API Endpoints

```
-	GET /products - Get a list of all products.
-	GET /products/:{productId} - Get details of a particular product.
-	POST /products/:{productId}/order -- Place an order for the product(s) selected by the shopper.
-	GET /shopper/:{shopperId}/orders - Get the list of orders placed by the shopper
-	GET /orders/{orderId} - Get the details of a specific order.
```
