# Planning Document

## Table of contents

**[User Stories](#user-stories)**<br>
**[Products](#products)**<br>
**[Classes](#classes)**<br>
**[Models/Methods](#models/methods)**<br>
**[Controllers](#controllers)**

# Valley Bread
Create an MVC web application order/customer/product tracking app.

## User Stories

**CUSTOMER**
* ADD CUSTOMER
* VIEW CUSTOMER DETAIL
* VIEW ALL CUSTOMER ORDERS
* VIEW ALL CUSTOMER ORDER DETAILS
* VIEW AVAILABLE PRODUCTS
* CREATE ORDER
* ADD PRODUCTS TO ORDER

#### ASSUME ADMIN CAN DO EVERYTHING A CUSTOMER CAN DO, PLUS . . .
**ADMIN**
* VIEW ALL CUSTOMERS
* VIEW ALL ORDERS
* VIEW ALL PRODUCTS
* ADD PRODUCTS
* SHOW/HIDE AVAILABLE PRODUCTS
* TRACK SALES OF INDIVIDUAL PRODUCTS
* VIEW SALES TRENDS OVER THE COURSE OF A MONTH/YEAR
* COSTING FOR INGREDIENTS
* COSTING FOR SUPPLIES, GAS, ETC.
* GROSS PROFITS

## Products
Demi Baguettes  
Spelt Sourdough  
Chile Cheddar Sourdough  
Challah  
Cinnamon Raisin Swirl  
Apple Walnut Sourdough  
Light Brioche  
Flax Oatmeal  
Seedy Sourdough  
Roasted Garlic Sourdough  
Turmeric Onion Sourdough  
Blue Corn Anadama  
Country Sour  
Honey Whole Wheat  
Chocolate & Red Chile Flake Sourdough  
Semolina Rolls  
Pumpernickel  
Hot Cross Buns  

## Classes
* ORDERS  
* CUSTOMERS  
* PRODUCTS  

### Customer database columns/class properties
- id: PRIMARY KEY, AUTO_INCREMENT
- firstName
- lastName
- phoneNumber
- email
- address
- city
- state
- zipcode

### Orders database columns/class properties
- id: PRIMARY KEY, AUTO_INCREMENT  
- orderNumber  
- receivedDate  
- requestedPickupDate  
- deliveredDate  
- pickupLocation    
- customer_id: FOREIGN KEY  

### Products database columns/class properties
- id: PRIMARY KEY, AUTO_INCREMENT
- Name
- description
- availability
- price
- producttype

## Models/Methods
### Customer
- public string GetFirstName()
- public string SetFirstName(string newName)
- public string GetLastName()
- public string SetLastName(string newName)
- public string GetPhoneNumber()
- public string SetPhoneNumber(string number)
- public string GetEmail()
- public void SetEmail(string newEmail)
- public string GetAddress()
- public void SetAddress(string newAddress)
- public string GetCity()
- public void SetCity(string newCity)
- public string GetState()
- public void SetState(string newState)
- public int GetZip()
- public void SetZip(int newZip)
- public int GetId()
- public string FirstLast()
- public List<Customer> GetAll()
- public void Save()
- public static Customer Find(int id)
- public void Edit(string firstName, string lastName, string phoneNumber, string email, string address, string city, string state, int zip)

**FOR TESTING HOUSEKEEPING:**
- public override bool Equals(System.Object otherCustomer)
- public void ClearAll()

### Order
- public int GetId()
- public List<Order> GetAll()
- public void Save()
- public Order Find(int searchId)
- public List<Customer> GetCustomer()
- public void Edit(int newOrderNumber, DateTime newReceivedDate, DateTime newRequestedPickupDate, DateTime newDeliveredDate, string newPickupLocation)
**FOR TESTING HOUSEKEEPING:**
- public override bool Equals(System.Object otherOrder)
- public void ClearAll()

### Products
- public string GetProductName()
- public void SetProductName(string name)
- public string GetProductType()
- public void SetProductType(string type)
- public string GetDescription()
- public void SetDescription(string description)
- public string GetUrl()
- public void SetUrl(string url)
- public float GetPrice()
- public void SetPrice(float price)
- public int GetId()
- public List<Order> GetAll()
- public void Save()
- public Order Find(int searchId)
- public void Edit(string name, string type, string description, string url)

**FOR TESTING HOUSEKEEPING:**
- public override bool Equals(System.Object otherProduct)
- public void ClearAll()

##Controllers
### HomeController
[HttpGet("/")] Index() - @Model: none  

### CustomerController
[HttpGet("/customer")] Index() - @Model: ???  
[HttpGet("/customer/new")] New(int orderId) - @Model: ???  
[HttpPost("/customer")] Create() - @Model: Dictionary<string, object>  
[HttpGet("/customer/show")] Show(int id) - @Model: Dictionary<string, object> {"customer", "order"}

### OrderController
[HttpGet("/order")] Index() - pass in @Model:  List<Order> {allOrders}
[HttpGet("/order/new")] New() - pass in @Model: Customer
[HttpPost("/order")] Create() - pass in @Model: Dictionary<string, object>  
[HttpGet("/order/{orderId}")] Show(int id) - pass in @Model: Dictionary<string, object> {"order", "products"}  
[HttpGet("/order/{orderId}/edit")] Edit() - pass in @Model: Dictionary<string, object>  
[HttpPost("/order/{orderId}")] Update() - pass in @Model: Dictionary<string, object>  
[HttpPost("/order/{orderId}")] Destroy() - pass in @Model: Dictionary<string, object>  

### ProductController
[HttpGet("/product")] Index() - pass in @Model:  List<Product> {allProducts}
[HttpGet("/product/new")] New() - pass in @Model: Customer
[HttpPost("/product")] Create() - pass in @Model: Dictionary<string, object>  
[HttpGet("/product/{productId}")] Show(int id) - pass in @Model: Dictionary<string, object> {"product", "products"}  
[HttpGet("/product/{productId}/edit")] Edit() - pass in @Model: Dictionary<string, object>  
[HttpPost("/product/{productId}")] Update() - pass in @Model: Dictionary<string, object>  
[HttpPost("/product/{productId}")] Destroy() - pass in @Model: Dictionary<string, object>  
