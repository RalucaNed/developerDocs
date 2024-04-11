PayArc provides a hosted checkout page that you can use to complete transactions/checkout for Invoices or Manual Subscriptions. The hosted checkout page works across all types of devices and makes checkout easy for merchants and customers.

Let's assume you want to create an order for $100, with a 3% surcharge.

# 1\. Retrieve your API access token

Log into the PAYARC Dashboard (<https://dashboard.payarc.net>), click on the "API" link in the left navigation bar, then click on the "Reveal Token" link on the API page.

Your API Access Token carries many privileges, please make sure to keep it secure. Do not share your API Access Token with anyone or on any websites like GitHub, client-side code, etc.

# 2\. Create an order
 
`POST` <https://testapi.payarc.net/v1/orders/>

A PAYARC-hosted payment page that helps collect payments quickly. It works across devices and is designed to increase conversion. Checkout makes it easy to build a first-class payments experience.

This checkout is valid for one time only. Provide `payment_form_url` value from the response to the customers. The customers can use that url and open checkout page on any browser to make payments.

```python
import http.client

conn = http.client.HTTPSConnection("testapi.payarc.net")
payload = 'amount=10000&surcharge_percent=3'
headers = {
  'Accept': 'application/json',
  'Content-Type': 'application/x-www-form-urlencoded',
  'Authorization': 'Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJhdWQiOiI0NTIyIiwianRpIjoiYmQ5NjhjZDVlMDI5ZDg3MGMzNjljZmExOGZkN2IxMTk3MjJlYWQ4YzcxODMzNTM0ZjE0OTU3Zjc1Y2E4ZWI2NmM5MTIwMDk0NTI0NWFmNzMiLCJpYXQiOjE3MDE5MzU4NjEsIm5iZiI6MTcwMTkzNTg2MSwiZXhwIjoxODU5NjE1ODYxLCJzdWIiOiI4NTI2MTg4Iiwic2NvcGVzIjoiKiJ9.KOJALGZ-u8CuRJcapzV22anTy7VGYyEUm3qzAaXVpQfX5rX_8bmuD9Kl2vF4FfvCreJ-cOem0-c3BZLLd6cEOiV4v0kwA2O70g3HCg80g8YCPsw9F3ggOtVFWgLPofBZp56WI0q-slykAQhXQOeM7MbqnHvLUdVQClCTrxb4-_332wyZUbX_zMj2Q_o-Wunzo0DPQhGrBTV7Va-jTXwOfcHcFMtuGTVoCGoz0qqmpO5E5QuAP9DQW2296SWd-zNF90XJ9RiqKN5BUQjx9-0m7TV0ryYpm4H-bhdOwuDpWBrJyIhNsQ9hpOjF8MXEXPho5weJwMKTsDk3iii6x7AAWv_8WvppC0ZGBLxT-TcV09vVumbsm2JVjG8wKLZRYE16Y2VFXrQc8s7TkZ-h-vHbHEGantICV5XdAZ9eTVnSY9NhgNlvsC4DYdw9hL7mW3F5qpT8mqFVzVGDIUMdXkuGuFpX7BZHw-pKU82ID7P3Jxpv8t1QzES7ITyCCGZswtOiNTh8PaPRIcLHtOWxaNUQTk0BCWuvNDesqkRDKBm8bQKfXu3vjBFq-_MHV4HiylGaec_KBSJv0fLyzTcwfHrXFbFFoevJANzw5BMezMwEPWY7XL-tH2LZ3HfiwiQcjFkNYyYVzrzOa-dIzHx0U35BzQdCxKEqxLpgFUY1T-PIr08'
}
conn.request("POST", "/v1/orders/", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```
```node
var https = require('follow-redirects').https;
var fs = require('fs');

var qs = require('querystring');

var options = {
  'method': 'POST',
  'hostname': 'testapi.payarc.net',
  'path': '/v1/orders/',
  'headers': {
    'Accept': 'application/json',
    'Content-Type': 'application/x-www-form-urlencoded',
    'Authorization': 'Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJhdWQiOiI0NTIyIiwianRpIjoiYmQ5NjhjZDVlMDI5ZDg3MGMzNjljZmExOGZkN2IxMTk3MjJlYWQ4YzcxODMzNTM0ZjE0OTU3Zjc1Y2E4ZWI2NmM5MTIwMDk0NTI0NWFmNzMiLCJpYXQiOjE3MDE5MzU4NjEsIm5iZiI6MTcwMTkzNTg2MSwiZXhwIjoxODU5NjE1ODYxLCJzdWIiOiI4NTI2MTg4Iiwic2NvcGVzIjoiKiJ9.KOJALGZ-u8CuRJcapzV22anTy7VGYyEUm3qzAaXVpQfX5rX_8bmuD9Kl2vF4FfvCreJ-cOem0-c3BZLLd6cEOiV4v0kwA2O70g3HCg80g8YCPsw9F3ggOtVFWgLPofBZp56WI0q-slykAQhXQOeM7MbqnHvLUdVQClCTrxb4-_332wyZUbX_zMj2Q_o-Wunzo0DPQhGrBTV7Va-jTXwOfcHcFMtuGTVoCGoz0qqmpO5E5QuAP9DQW2296SWd-zNF90XJ9RiqKN5BUQjx9-0m7TV0ryYpm4H-bhdOwuDpWBrJyIhNsQ9hpOjF8MXEXPho5weJwMKTsDk3iii6x7AAWv_8WvppC0ZGBLxT-TcV09vVumbsm2JVjG8wKLZRYE16Y2VFXrQc8s7TkZ-h-vHbHEGantICV5XdAZ9eTVnSY9NhgNlvsC4DYdw9hL7mW3F5qpT8mqFVzVGDIUMdXkuGuFpX7BZHw-pKU82ID7P3Jxpv8t1QzES7ITyCCGZswtOiNTh8PaPRIcLHtOWxaNUQTk0BCWuvNDesqkRDKBm8bQKfXu3vjBFq-_MHV4HiylGaec_KBSJv0fLyzTcwfHrXFbFFoevJANzw5BMezMwEPWY7XL-tH2LZ3HfiwiQcjFkNYyYVzrzOa-dIzHx0U35BzQdCxKEqxLpgFUY1T-PIr08'
  },
  'maxRedirects': 20
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = qs.stringify({
  'amount': '10000',
  'surcharge_percent': '3',
});

req.write(postData);

req.end();
```
```csharp
var client = new HttpClient();
var request = new HttpRequestMessage(HttpMethod.Post, "https://testapi.payarc.net/v1/orders/");
request.Headers.Add("Accept", "application/json");
request.Headers.Add("Authorization", "Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJhdWQiOiI0NTIyIiwianRpIjoiYmQ5NjhjZDVlMDI5ZDg3MGMzNjljZmExOGZkN2IxMTk3MjJlYWQ4YzcxODMzNTM0ZjE0OTU3Zjc1Y2E4ZWI2NmM5MTIwMDk0NTI0NWFmNzMiLCJpYXQiOjE3MDE5MzU4NjEsIm5iZiI6MTcwMTkzNTg2MSwiZXhwIjoxODU5NjE1ODYxLCJzdWIiOiI4NTI2MTg4Iiwic2NvcGVzIjoiKiJ9.KOJALGZ-u8CuRJcapzV22anTy7VGYyEUm3qzAaXVpQfX5rX_8bmuD9Kl2vF4FfvCreJ-cOem0-c3BZLLd6cEOiV4v0kwA2O70g3HCg80g8YCPsw9F3ggOtVFWgLPofBZp56WI0q-slykAQhXQOeM7MbqnHvLUdVQClCTrxb4-_332wyZUbX_zMj2Q_o-Wunzo0DPQhGrBTV7Va-jTXwOfcHcFMtuGTVoCGoz0qqmpO5E5QuAP9DQW2296SWd-zNF90XJ9RiqKN5BUQjx9-0m7TV0ryYpm4H-bhdOwuDpWBrJyIhNsQ9hpOjF8MXEXPho5weJwMKTsDk3iii6x7AAWv_8WvppC0ZGBLxT-TcV09vVumbsm2JVjG8wKLZRYE16Y2VFXrQc8s7TkZ-h-vHbHEGantICV5XdAZ9eTVnSY9NhgNlvsC4DYdw9hL7mW3F5qpT8mqFVzVGDIUMdXkuGuFpX7BZHw-pKU82ID7P3Jxpv8t1QzES7ITyCCGZswtOiNTh8PaPRIcLHtOWxaNUQTk0BCWuvNDesqkRDKBm8bQKfXu3vjBFq-_MHV4HiylGaec_KBSJv0fLyzTcwfHrXFbFFoevJANzw5BMezMwEPWY7XL-tH2LZ3HfiwiQcjFkNYyYVzrzOa-dIzHx0U35BzQdCxKEqxLpgFUY1T-PIr08");
var collection = new List<KeyValuePair<string, string>>();
collection.Add(new("amount", "10000"));
collection.Add(new("surcharge_percent", "3"));
var content = new FormUrlEncodedContent(collection);
request.Content = content;
var response = await client.SendAsync(request);
response.EnsureSuccessStatusCode();
Console.WriteLine(await response.Content.ReadAsStringAsync());

```

```json Response
{  
  "id": "1P4R6gBz4MBq1zMx",  
  "payment_form_url": "<https://checkout.payarc.net/pay/order/{{order_id}}?orderToken={{order_token}}">,  
  "token": "{{PAYARC-generated-token}}"  
}
```

# 3\. Add a Checkout Button

Now let's add a checkout button to your webpage 

First, retrieve the `id` and `token` from the Create Order response. These will be used by the PAYARC checkout library to generate the checkout model.

Then, include the payarc.js library in your page.

> 📘 The payarc.js library is available in a [test](https://payarc-checkout.s3.us-east-2.amazonaws.com/test/payarc.js) version, for validating the payment, and a [live](https://payarc-checkout.s3.us-east-2.amazonaws.com/prod/payarc.js) version to be used when you are ready for production.

You can use the events `paymentCompleted` and `paymentDeclined` to handle the results of the payment.

Your customers can complete their payments using the form.

```html
<br></div><div>      body {
<br></div><div>        background: #f9f9f9;
<br></div><div>        overflow-y: scroll;
<br></div><div>        margin: 0;
<br></div><div>      }
<br></div><div>    
    Checkout page
    
    
<br></div><div>    function payarcCheckout(amount, orderId, orderToken) {
<br></div><div>     const payArc = new PayArc({
<br></div><div>      amount: amount,
<br></div><div>      orderId : orderId,
<br></div><div>      orderToken: orderToken,
<br></div><div>      viewScheme: 'light'
<br></div><div>    });
<br></div><div>    payArc.renderModal();
<br></div><div>    payArc.on('paymentCompleted', function() {
<br></div><div>      payArc.closeModal();
<br></div><div>      alert("Payment was Success");
<br></div><div>    });
<br></div><div>    payArc.on('paymentDeclined', function() {
<br></div><div>      payArc.closeModal();
<br></div><div>      alert("Payment Failed!");
<br></div><div>    });
<br></div><div> }
<br></div><div>
  
  
    Checkout
```

# 4\. Check the order status

You can list a customer's orders based on a few parameters, using the order retrieval API: <https://testapi.payarc.net/v1/orders/customer/get>

```python
import http.client

conn = http.client.HTTPSConnection("testapi.payarc.net")
payload = 'amount=9999&status=SUCCESS&customer_id=&order_name=&send_via=&created_at=2021-09-13'
headers = {
  'Authorization': 'Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJhdWQiOiI0NTIyIiwianRpIjoiYmQ5NjhjZDVlMDI5ZDg3MGMzNjljZmExOGZkN2IxMTk3MjJlYWQ4YzcxODMzNTM0ZjE0OTU3Zjc1Y2E4ZWI2NmM5MTIwMDk0NTI0NWFmNzMiLCJpYXQiOjE3MDE5MzU4NjEsIm5iZiI6MTcwMTkzNTg2MSwiZXhwIjoxODU5NjE1ODYxLCJzdWIiOiI4NTI2MTg4Iiwic2NvcGVzIjoiKiJ9.KOJALGZ-u8CuRJcapzV22anTy7VGYyEUm3qzAaXVpQfX5rX_8bmuD9Kl2vF4FfvCreJ-cOem0-c3BZLLd6cEOiV4v0kwA2O70g3HCg80g8YCPsw9F3ggOtVFWgLPofBZp56WI0q-slykAQhXQOeM7MbqnHvLUdVQClCTrxb4-_332wyZUbX_zMj2Q_o-Wunzo0DPQhGrBTV7Va-jTXwOfcHcFMtuGTVoCGoz0qqmpO5E5QuAP9DQW2296SWd-zNF90XJ9RiqKN5BUQjx9-0m7TV0ryYpm4H-bhdOwuDpWBrJyIhNsQ9hpOjF8MXEXPho5weJwMKTsDk3iii6x7AAWv_8WvppC0ZGBLxT-TcV09vVumbsm2JVjG8wKLZRYE16Y2VFXrQc8s7TkZ-h-vHbHEGantICV5XdAZ9eTVnSY9NhgNlvsC4DYdw9hL7mW3F5qpT8mqFVzVGDIUMdXkuGuFpX7BZHw-pKU82ID7P3Jxpv8t1QzES7ITyCCGZswtOiNTh8PaPRIcLHtOWxaNUQTk0BCWuvNDesqkRDKBm8bQKfXu3vjBFq-_MHV4HiylGaec_KBSJv0fLyzTcwfHrXFbFFoevJANzw5BMezMwEPWY7XL-tH2LZ3HfiwiQcjFkNYyYVzrzOa-dIzHx0U35BzQdCxKEqxLpgFUY1T-PIr08',
  'Accept': 'application/json'
}
conn.request("GET", "/v1/orders/customer/get", payload, headers)
res = conn.getresponse()
data = res.read()
print(data.decode("utf-8"))
```
```node
var https = require('follow-redirects').https;
var fs = require('fs');

var qs = require('querystring');

var options = {
  'method': 'GET',
  'hostname': 'api.payarc.net',
  'path': '/v1/orders/customer/get',
  'headers': {
    'Authorization': 'Bearer {{Access-Token-From-Payarc-Dashboard}}',
    'Accept': 'application/json'
  },
  'maxRedirects': 20
};

var req = https.request(options, function (res) {
  var chunks = [];

  res.on("data", function (chunk) {
    chunks.push(chunk);
  });

  res.on("end", function (chunk) {
    var body = Buffer.concat(chunks);
    console.log(body.toString());
  });

  res.on("error", function (error) {
    console.error(error);
  });
});

var postData = qs.stringify({
  'amount': '9999',
  'status': 'SUCCESS',
  'customer_id': '',
  'order_name': '',
  'send_via': '',
  'created_at': '2021-09-13'
});

req.write(postData);

req.end();
```
```csharp
var client = new HttpClient();
var request = new HttpRequestMessage(HttpMethod.Get, "https://testapi.payarc.net/v1/orders/customer/get");
request.Headers.Add("Authorization", "Bearer eyJ0eXAiOiJKV1QiLCJhbGciOiJSUzI1NiJ9.eyJhdWQiOiI0NTIyIiwianRpIjoiYmQ5NjhjZDVlMDI5ZDg3MGMzNjljZmExOGZkN2IxMTk3MjJlYWQ4YzcxODMzNTM0ZjE0OTU3Zjc1Y2E4ZWI2NmM5MTIwMDk0NTI0NWFmNzMiLCJpYXQiOjE3MDE5MzU4NjEsIm5iZiI6MTcwMTkzNTg2MSwiZXhwIjoxODU5NjE1ODYxLCJzdWIiOiI4NTI2MTg4Iiwic2NvcGVzIjoiKiJ9.KOJALGZ-u8CuRJcapzV22anTy7VGYyEUm3qzAaXVpQfX5rX_8bmuD9Kl2vF4FfvCreJ-cOem0-c3BZLLd6cEOiV4v0kwA2O70g3HCg80g8YCPsw9F3ggOtVFWgLPofBZp56WI0q-slykAQhXQOeM7MbqnHvLUdVQClCTrxb4-_332wyZUbX_zMj2Q_o-Wunzo0DPQhGrBTV7Va-jTXwOfcHcFMtuGTVoCGoz0qqmpO5E5QuAP9DQW2296SWd-zNF90XJ9RiqKN5BUQjx9-0m7TV0ryYpm4H-bhdOwuDpWBrJyIhNsQ9hpOjF8MXEXPho5weJwMKTsDk3iii6x7AAWv_8WvppC0ZGBLxT-TcV09vVumbsm2JVjG8wKLZRYE16Y2VFXrQc8s7TkZ-h-vHbHEGantICV5XdAZ9eTVnSY9NhgNlvsC4DYdw9hL7mW3F5qpT8mqFVzVGDIUMdXkuGuFpX7BZHw-pKU82ID7P3Jxpv8t1QzES7ITyCCGZswtOiNTh8PaPRIcLHtOWxaNUQTk0BCWuvNDesqkRDKBm8bQKfXu3vjBFq-_MHV4HiylGaec_KBSJv0fLyzTcwfHrXFbFFoevJANzw5BMezMwEPWY7XL-tH2LZ3HfiwiQcjFkNYyYVzrzOa-dIzHx0U35BzQdCxKEqxLpgFUY1T-PIr08");
request.Headers.Add("Accept", "application/json");
var collection = new List<KeyValuePair<string, string>>();
collection.Add(new("amount", "9999"));
collection.Add(new("status", "SUCCESS"));
collection.Add(new("customer_id", ""));
collection.Add(new("order_name", ""));
collection.Add(new("send_via", ""));
collection.Add(new("created_at", "2021-09-13"));
var content = new FormUrlEncodedContent(collection);
request.Content = content;
var response = await client.SendAsync(request);
response.EnsureSuccessStatusCode();
Console.WriteLine(await response.Content.ReadAsStringAsync());

```

<br>

[block:parameters]
{
  "data": {
    "h-0": "Parameter",
    "h-1": "Description",
    "0-0": "**Amount**  \n_Required_  \nNumeric, Min Length: 1 , Max Length: 8",
    "0-1": "This is the amount of the orders. This must be a positive integer and represented in cents.  \nThe minimum amount for testing a transaction in the test environment is $0.50  \n_Examples_: 9 → would equal $0.09;  \n99999 → would equal $999.99  ",
    "1-0": "**Status**  \n \\_Conditionally Required, if the field is present in the input data and must be one of the below values.  \nAllowable values: `SUCCESS`, `FAILED`, `ORDER_UNDER_PROCESS`",
    "1-1": "Current status of an order.  \n`ORDER_UNDER_PROCESS` is used when the order is sent to the customer but not yet paid.",
    "2-0": "**Customer ID**  \n_Optional_  \nAlpha numeric",
    "2-1": "Customer_ID the order is associated with. Customer IDs are created in the Create Customer API.",
    "3-0": "**Order_name**  \n_Optional_  \nString, Min Length: 0, Max Length: 191",
    "3-1": "The short description of the order. The description is added in the Create an Order API.",
    "4-0": "**Send_via**  \n_Optional_  \nArray, Allowable values: `SMS`,`EMAIL`, `SMS,EMAIL`",
    "4-1": "How you are sending the order to the customer (Email and/or SMS)",
    "5-0": "**Created_at**  \n_Optional_  \nDate (YYYY-MM-DD)",
    "5-1": "The date the order was created.  \nExample: `2023-01-23`"
  },
  "cols": 2,
  "rows": 6,
  "align": [
    "left",
    "left"
  ]
}
[/block]
