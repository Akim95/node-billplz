# node-billplz
[Billplz API](https://www.billplz.com/api) wrapper for nodejs. This module supports only Billplz API V3.

API Reference: https://www.billplz.com/api

## Usage
### Install
```
npm install billplz
```


### Create a client
```
const Billplz = require('billplz')
const billplz = new Billplz('your-api-key')
```

###### Optional parameter (if needed)
```
const billplz = new Billplz({
  'key': 'your-api-key',
  'endpoint': 'https://www.billplz.com/api/v3/',
  'sandbox': true
})
```


### Create a collection
```
billplz.create_collection({
  'title': 'My Noodle Shop'
}, function(err, res) {
  if (err) {
    //handle http client error
  }

  //success, do your stuff here
  console.log(res)
})
```

### Create an open collection
```
billplz.create_collectionOpen({
  'title': 'Noodle Exhibition Ticket',
  'description': 'VVIP Ticket to Noodle Exhibition!',
  'amount': 25550, //RM255.50
  'reference_1_label': 'MyKAD',
  'reference_2_label': 'First Name'
}, function(err, res) {
  console.log(res)
})
```

### Create a bill
```
billplz.create_bill({
  'collection_id': 'your-collection-id',
  'description': 'Mee Segera Sedap 200g',
  'email': 'sukamakan@meesegera.com',
  'name': 'Ahmad Segera',
  'amount': 550, //RM5.50
  'callback_url': "http://example.com/webhook/",
  'redirect_url': "http://example.com/thank-you",
  'due_at': '2016-08-31'
}, function(err, res) {
  console.log(res)
})
```

### Retrieve a bill
```
billplz.get_bill('your-bill-id', function(err, res) {
  console.log(res)
})
```

### Delete a bill
```
billplz.delete_bill('your-bill-id', function(err, res) {
  console.log(res)
})
```
