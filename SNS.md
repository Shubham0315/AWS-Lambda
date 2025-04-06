What is AWS SNS?
-
- Simple Notification Service
- Fully managed messaging service of AWS used to send messages or notifications using email, SMS, lambda functions, mobile apps
  - Create topic :- Logical access point for publishing messages
  - Subscribe to topic :- Add endpoints (email, SMS) that will receive message
  - Publish Messages to subscribers
 
---------------------------------------------------------------------------

What are the main components of SNS?
-
- **Topics** :- Logical channel for sending messages. Publishers send messages to topic, they dont send directly to subscribers
- **Publishers** :- Any system/app that sends messages to SNS topic
- **Subscribers (Consumers)** :- Endpoints that receive messages published to topic. Each subscriber must confirm the subscription before receiving messages

---------------------------------------------------------------------------

What are the supported protocols in SNS?
-
- SNS supports multiple protocols for delivering messages to different types of endpoints
- HTTP :- Delivers JSON formatted messages to HTTP endpoint via POST request
- HTTPS :-
- Email :- sends messages as plain text emails
- Email-JSON :- JSON formatted email
- SMS :- Sends messages to mobile phones
- Lambda :- Triggers lambda function with message as input

---------------------------------------------------------------------------

What is the difference between SNS and SQS?
-
- SNS is pub/sub model (Publisher/subscriber) while SQS is message queue service
- SNS is push based (sends to subscribers) while SQS is pull based (messages are retrieved by receivers)
- SNS has no message retention while SQS has 14 days period

- Use both SNS+SQS
  - SNS sends message to topic
  - That topic has SQS queues subscribed
  - Each queue gets copy of message
  - Consumers pull from queues when ready
 
---------------------------------------------------------------------------

Can an SNS topic have multiple subscribers?
-
- SNS topic can have multiple subscribers as it uses pub/sub model
- Using SNS topic we ccan subscribe multile endpoints like :- Email, SMS, SQS, Lambda, Mobile push
- Whenever message is published to topic, all subscribers receive it at same time

---------------------------------------------------------------------------

How does SNS ensure message delivery?
-
- AWS SNS ensures message delivery using combo of retries, durability and protocol-specific mechanisms, depending on type of subscriber
- SQS :- Delivers message to queue. Guaranteed delivery
- Lambda :- Invokes function with message
- Email :- Tries to deliver via SMTP
- SMS :- Best effort delivery via mobile carriers

---------------------------------------------------------------------------

What is message filtering in SNS?
-
- It lets us send messages only to specific subscribers based on content of message, not every subscriber receive every message
- This helps to reduce noise and keeps our systems efficient
- We can define filter policies on each subscription
- Only messages that match sub filter will be delivered to sub

---------------------------------------------------------------------------

How do you secure SNS topics?
-
- IAM policies :- to control whom can publish/subscribe
- Topic policies :- Direct access rules from topic
- SSE :- Encrypt messages at rest
- Sub confirmation :- prevent unauthorized subs
- Cloudwatch :- monitor metrics

---------------------------------------------------------------------------

Can SNS messages be encrypted?
-
- SNS messages can be encrypted using SSE with KMS to protect data at rest
- When we enable SSE on SNS topic
  - Messages are encrypted as soon as they are received by SNS
  - They are stored in encrypted form
  - Only authorized services or users with right KMS permissions can decrypt and access them
 
---------------------------------------------------------------------------

How would you use SNS in a CI/CD pipeline?
-
- Build complete :- Notify via email/SMS/webhook
- Test success/fail :- trigger alert or logging service
- Error occured :- send alert to team

---------------------------------------------------------------------------

What are delivery retries for HTTP/S endpoints? 
-
- Delivery retries for HTTp/S endpoints in SNS are part of automatic retry mechanism which SNS uses to ensure delivery when HTTP/S endpoint is temporarily unavailable or encounters failure during messaging processing
- SNS will auto retry delivery acc to exponential backoff strategy
- Gradually retries slow down. Performed for 24 hr at most. Then SNS stops retries and message is considered as undelivered.

---------------------------------------------------------------------------
