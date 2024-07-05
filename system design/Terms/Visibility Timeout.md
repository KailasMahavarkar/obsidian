![](https://i.imgur.com/kGWX72R.png)


When a Lambda function polls an SQS queue and retrieves a message, the message becomes invisible to other consumers for a specified period (visibility timeout). This ensures that multiple Lambda instances (if scaled) don't process the same message simultaneously, avoiding duplicate processing.

-----
#SNS #SQS #visibility-timeout #aws #system-design-terms 
