![Alt text](/images/charge_payments.png?raw=true 'charge_payments') 

---

:moneybag: Charge Payments :moneybag: is an ecommerce platform that enables merchants to easily charge credit cards. It also allows buyers to validate their transactions prior to processing. 

<p align="center">
  <img src="../images/screens/payments_checkout.png" width="420" alt="paymnets_checkout"/> 
  <img src="../images/screens/mobile_payments_checkout.png" width="420" alt="mobile_payments_checkout" />
</p>

## Merchant Integration

The Charge Payments Widget is cross domain component built with [zoid](https://github.com/krakenjs/zoid) that enables merchants to securely sell their items.

<div align="center">
  
  :star: Integration is easy! :star:

</div>

### Integration

Include the source in your `index.html`

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="shortcut icon" href="%PUBLIC_URL%/favicon.png">
    <title>My Checkout Store</title>
  </head>
  <body>
    <div id="root"></div>
    <script src="https://cdnjs.charge.io/checkout/charge-checkout.frame.js"></script>
  </body>
</html>
```

Then render the component on the parent page:

```html
<!-- Charge Checkout -->
<div id="container"></div>
<!-- Container to display the result of  call -->
<div id="chargeContainer"></div>
<script>
    // Render the component and pass down props to the iframe
    Charge.ButtonComponent({
        env: "development",
        publicKey: "1234",
        guestCheckout: false,
        transaction: {
        orderId: "123ABC", // your internal oder id - not required
        storeName: "My store name", // your store name - not required
        checkoutUrl: "https://my-store/checkout", // the url for your checkout
        thankyouUrl: "https://my-store/thankyou", // the url for your confirmation
        lineItems: [
            {
                productId: "456BGF", // your internal product id - not required
                title: "The Item Name",  // the name of the item being sold - required
                imageUrl: "https://my-store/image/456BGF", // the url for the item image - required
                unitPrice: "2412", // the price of the item in cents - required
                quantity: "1", // the quantity of this item - required
            }
        ],
        transactionAdjustment: [
            {
                description: "This is discount coupon", // the description for this adjustment - required
                amount: "250", // the quantity to adjust in cents - required
            }
        ],
        total: "2162", // the total amount for this transaction in cents - required
        date: "2020-01-14 18:51:04.936456+00", // the timestamp for the transaction
        status: "pending", // the status of the transaction - defaults to pending
    }
    }).render("#container");
</script>
```

### React

To integrate with your React ecommerce store, include the script in your `index.html`:

```html
<!doctype html>
<html lang="en">
  <head>
    <meta charset="utf-8">
    <meta name="viewport" content="width=device-width, initial-scale=1">
    <link rel="shortcut icon" href="%PUBLIC_URL%/favicon.png">
    <title>My Checkout Store</title>
  </head>
  <body>
    <div id="root"></div>
    <script src="https://cdnjs.charge.io/checkout/charge-checkout.frame.js"></script>
  </body>
</html>
```

then render the component:

```jsx
/**
 *  Shop Checkout Page
 */
import React, { Component } from 'react'
import ReactDOM from 'react-dom'

let ChargeComponent = window.Charge.ButtonComponent.driver('react', {
  React: React,
  ReactDOM: ReactDOM,
})

class CheckOut extends Component {
  // Code omitted for clarity
  render() {
    const publicKey = this.publicKey
    const guestCheckout = true
    const transaction = this.myTransaction

    return (
      <div class="site-content">
          {/* Code omitted for clarity */}
          <div id="loginContainer">
            <ChargeComponent
              env={env}
              publicKey={publicKey}
              guestCheckout={guestCheckout}
              transaction={transaction}
            />
          </div>
          {/* Code omitted for clarity */}
      </div>
    )
  }
}
export default CheckOut
```

That's it! :fire: Your store now has Charge payments integrated :moneybag:
<p align="center">
  <img src="../images/screens/tablet_payments_checkout.png" width="4000" alt="tablet_payments_checkout" />
</p>

And your Merchant Dashboard to :

:white_check_mark: Check your transactions :chart_with_upwards_trend:

:white_check_mark: Withdraw your money :money_with_wings:

:white_check_mark: Manage your inventory :rugby_football:

<p align="center">
  <img src="../images/screens/payments_dashboard.png" width="400" alt="payments_dashboard" />
  <img src="../images/screens/tablet_payments_transaction.png" width="400" alt="tablet_payments_transactions" />
</p>

<div align="center">

> [charge.io](https://www.charge.io) &nbsp;&middot;&nbsp;
> [info@charge.io](mailto:info@charge.io?subject=[GitHub]) &nbsp;&middot;&nbsp;
> [payments@charge.io](mailto:payments@charge.io?subject=[GitHub]) &nbsp;&middot;&nbsp;
> [wallet@charge.io](mailto:wallet@charge.io?subject=[GitHub]) &nbsp;&middot;&nbsp;
> [identity@charge.io](mailto:identity@charge.io?subject=[GitHub])

</div>
