# Javaeats-Lite: System Analysis & Design Document (SAD)

![Status](https://img.shields.io/badge/Status-Analysis_Phase-blue)
![Type](https://img.shields.io/badge/Type-SAD-orange)
![Modeling](https://img.shields.io/badge/Modeling-UML_2.5-purple)

## Executive Summary (Vision)

Javaeats Lite is a Talabat-like restaurant browsing and ordering system designed to simplify the process of discovering restaurants,
exploring menus, and placing orders.

The system provides customers with an intuitive platform to browse a wide variety of restaurants,
manage their orders efficiently, and enhance their overall ordering experience. Additionally,
the platform aims to help restaurants expand their customer base by increasing visibility and accessibility to new customers.

## Document Scope

This document focuses on system analysis and high-level design.
Implementation details are intentionally excluded.
Implementation details will be maintained in a separate repository.

## Data Model

> Not Implemented Yet.

- The data layer will be designed with a focus on: **Data Integrity**, **Data Consistency**, **Normalization**, **Denormalization**, **Indexing**, **Performance Tuning**.

## System Requirements

### System Features and & Functions

#### F01-Restaurant Browsing

- System shall allow user to browse **Restaurants**, **Menus**, as a guest without authentication.
- System shall display resturant name, area, address, phone number, availability, ratings.
- System shall allow user to add items to cart.

##### Constraints

- User should be registered in order to pursue his checkout process.

##### Functions

```java
getAllRestaurants();
getResturantMenu(restaurantID);
```

#### F02-User Registration

- System shall allow user to register using his email address or phone number.
- System shall allow user to enter his name.
- System shall allow user to enter his phone number.
- System shall allow user to enter his gender (Optional).
- System shall allow user to enter his birth date (Optional).
- System shall send verification message to the user (email, SMS).

##### Constraints

- User email or phone number must be unique and valid.
- User's name and phone number is mandatory.
- User should provide valid password in order to register.

##### Functions

```java
isValidEmail(email);
isEmailExists(email);
isValidPhoneNum(phoneNumber);
IsPhoneNumberExists(phoneNumber);
isValidPassword(password);
addNewUser(User);
```

#### F03-User Login

- System shall allow user to login using his user name/ email/ phone number and password

##### Constraints

- User should enter valid credentials in order to login.

##### Functions

```java
authenticateUserByEmail(email, password);
authenticateUserByUserName(userName, password);
authenticateUserByPhone(phone, password);
```

#### F04-Menu Viewing

- System shall allow user to access restaurant menus to
  - Explore menu categories
  - View item details
  - View items pictures
  - View retaurant or item reviews.

##### Functions

```java
getResMenue(resId);
getResReviewes(resId);
getItemReviews(itemId);
```

#### F05-Cart Management

- System shall allow user to add items to cart.
- System shall allow user to modify cart items quantity.
- System shall allow user to delete items from cart.
- System shall allow user to clear cart.
- System shall allow user to cancel order.
- System shall allow user to add custom notes for the order .
- System shall allow user to add custom notes for the item .

- System shall display summary of selected items.
- System shall calculate and display the order's total cost.

> **Note**: Order statuses after checkout are: **Pinding**, **In Progress**, **On the way**, **Delivered**.

##### Constraints

- Only the system / restaurant can update status.
- User can't modify or delete items after **Pending**.
- User can't cancel order after **Pending**.

##### Functions

```java
addToCart(item);
changeCartItemQuantity(newQuantity);
deleteCartItem(itemID);
clearCart(orderID);
cancelOrder(OrderID);
calcTotal(orderItems);
addOrderNote(note);
addItemNote(note);
```

#### F06-Place Order

- System shall allow user to enter or change his phone number.
- System shall allow user to enter or change his address.

##### Constraints

- Phone number is required.
- Address is required.

##### Functions

```java
createNewOrder(input:orderItems);
```

#### F07-Profile Management

##### F07.1 Account Informantion

- System shall allow user to change his name.
- System shall allow user to change his birth date.
- System shall allow user to change his gender.

###### Functions

- Update user information.

##### F07.2-Update Saved Addresses

- System shall allow user to update his addresses.
- System shall allow user to delete address.
- System shall allow user to add new address.

###### Functions

```java
updateUserAddress(userID,oldAddress,newAddress)
deleteAddress(userId, address);
addNewAddress(userId, newAddress)
```

##### F07.3-Change Email

- System shall allow user to change his email address.

###### Constraints

- User must enter valid email (user@example.com).
- System must validate email via confirmation mail valid for 1 hour.

###### Funcitons

```java
isValidEmail(email);
@async
sendVerficationMail(mail);
```

##### F07.4-Change Password

- System shall allow user to enter his old password.
- System shall allow user to enter his new password

###### Constraints

- User's old password must be correct.
- User must enter his new password twice.
- User must enter new valid password.

###### Funcitons

```java
isValidPassword(password);
authenticateUser(userId, Password)
isNewPasswordvalid(newPassword, newPasswordConfirmation);
changeUserPassword(newPassword);
```

##### F07.5-Order History

- System shall allow user to view his order history.

##### Functions

```java
getOrderHistory(userId);
```

#### F08-Rating and Reviewes

- System shall allow user to add item review.
- System shall allow user to add restaurant review.
- System shall allow user to rate item.
- System shall allow user to rate resturant.

##### Constraints

- User can only add review for items that he already ordered.
- User can only add review for restaurants that he already ordered from.
- Order or Restaurant ratings is between 1 and 5 stars.

##### Functions

```java
addItemReview(itemId, review);
addResReviewe(resId, review);
rateItem(itemId, rate);
rateRes(resId, rate);
rateReviewItem(itemId, rate, reviewe);
rateReviewRes(resId, rate, reviewe);
```

---

## Technology Stack (Planned)

- **Backend:** Java, Spring, Git.
- **Database:** PostgreSQL
- **Modeling Tools:** Various modeling tools.
- **Documentation:** Markdown.

---

## Contact & Contribution

- **Author:** Abdalla Samir Khalifa
- **Role:** Systems Analyst & Backend Developer
- **Contact**:
  - GitHub: [@AbdallaSamirKhalifa](https://github.com/AbdallaSamirKhalifa)
  - Email: [abdallasamirkhalifa@gmail.com](abdallasamirkhalifa@gmail.com)
  - Linkedin: [Abdalla Khalifa](https://linkedin.com/in/abdalla-khalifa)
