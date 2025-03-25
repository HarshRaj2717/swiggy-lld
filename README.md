# swiggy-lld

A low-level design of Swiggy (my interpretation)

# Requirements/Features

> Put output at a place (other than console; use console only for inputting stuff) where every entity can concurrently write to, make all run in separate threads to handle different requests from different entities at once

## top level controller/manager (aka admin control)

- can ban users
- can ban resturants
- can ban delivery partners
- can add/remove available payment methods (affective for all users at once)
- can send notifications
- has a bank/money balance, which acts as the mediator between user, delivery partner and resturant
- sets multiple configs (swiggy one price, festive discounts, surge/bad weather fees, platform fees (for both user & resturant))

## users

- handle users (name, passwd, gender, addr, phone, location(s), saved payment methods(like paytm upi), order history, search history)
- users can have a swiggy one membership (no delivery & surge fee)
- users can place orders
- users can see resturants at their selected location
- users can rate resturants, dishes, and delivery partners
- every user has a unique cart (a cart can have items from a single resturant only at a time)
- users can pick payment method for an order
- users can see order status
- users can make payment
- user1 can place an order for another user2
- users can recieve notifications (like: "IND vc PAK final match hai.. mithai khareed lo <3"); notifications are also based on gender (some notifications go to all genders, some go to only specific ones)

## resturants

- handle resturants (name, address, rating, cuisine(s), menu{item name, description, price, discount, rating, isAvailable}, payment info (to submit user's payment), coupon discounts (the one's you see under the menu in a sliding carousel))
- resturant can cancel an order (causing a refund)

### resturant-views

- resturants show dynamically calculated distance & estimated delivery time based on user's location
- resturants show dynamically generated menu_item recommendations based on user's order & search history
- resturants show dynamically generated "want to repeat" section
- resturants show dynamically generated "< search_term >" section (*user can search any one from a pre-defined list of cuisines eg: north-indian, italin, etc; or from a pre-defined list of dishes eg: pizza, burger, etc*)

## search
