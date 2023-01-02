---
layout: post
title:  "나는 바보다"
date:   2023-01-02 21:34:36 +0900
categories: 나는 멍청이
---
바보같이 나는 노트북을 두고왔다. 

```javascript
const Razorpay = require('razorpay');

let rzp = Razorpay({
	key_id: 'KEY_ID',
	secret: 'name'
});

// capture request
rzp.capture(payment_id, cost)
	.then(function (data) {
		return 2;
	})
```