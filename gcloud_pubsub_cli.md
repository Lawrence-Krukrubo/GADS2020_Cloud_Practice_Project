#Overview

#Google Cloud Pub/Sub is a messaging service for exchanging event data among applications 
#and services. By decoupling senders and receivers, it allows for secure and highly available 
#communication between independently written applications. Google Cloud Pub/Sub delivers 
#low-latency/durable messaging, and is commonly used by developers in implementing 
#asynchronous workflows, distributing event notifications, 
#and streaming data from various processes or devices.

#In this lab, you will do the following:

#1. Learn the basics of Pub/Sub.
#2. Create, delete, and list Pub/Sub topics.
#3. Create, delete, and list Pub/Sub subscriptions.
#4. Publish messages to a topic.
#5. Use a pull subscriber to output individual topic messages.
#6. Use a pull subscriber with a flag to output multiple messages.

#Running this file in cloud shell using: bash gcloud_pubsub_cli.md auto-runs all commands.

#step 1
echo "Let's create a pubsub topic called myTopic..."
gcloud pubsub topics create myTopic
echo " "

#step 2
echo "Let's create 2 more topics:- test1 and test2..."
gcloud pubsub topics create test1
gcloud pubsub topics create test2
echo " "

#step 3
echo "Let's list out all the topics..."
gcloud pubsub topics list
echo " "

#step 4
echo "Let's delete topics test1 and test2..."
gcloud pubsub topics delete test1
gcloud pubsub topics delete test2
echo " "

#step 5
echo "Let's list out the remaining topics..."
gcloud pubsub topics list
echo " "

#step 6
echo "Let's create 3 new subscriptions for myTopic..."
gcloud pubsub subscriptions create --topic=myTopic sports
gcloud pubsub subscriptions create --topic=myTopic cars
gcloud pubsub subscriptions create --topic=myTopic wines
echo " "

#step 7
echo "Let's see our subscription topics:- sports, cars and wines..."
gcloud pubsub topics list-subscriptions myTopic
echo " "

#step 8
echo "Let's delete the subscriptions for cars and wines..."
gcloud pubsub subscriptions delete cars
gcloud pubsub subscriptions delete wines
echo " "

#step 9
echo "Let's list the subscriptions to confirm cars and wines are deleted..."
gcloud pubsub topics list-subscriptions myTopic
echo " "

#step 10
echo "Now, let's publish a message to myTopic..."
gcloud pubsub topics publish myTopic --message "Hello, Sports Lovers!"
echo " "

#step 11
echo "Now, let's publish 3 more messages to myTopic..."
gcloud pubsub topics publish myTopic --message "Welcome to Today's Show."
gcloud pubsub topics publish myTopic --message "Today is all about Cricket!"
gcloud pubsub topics publish myTopic --message "My name is Lawrence and I'm your Presenter."
echo " "

#step 12
echo "Now, let's pull just one message out using the sports subscription..."
gcloud pubsub subscriptions pull sports --auto-ack
echo " "

#step 13
echo "To pull the 3 remaining messages we pass the flag --limit=3 to pull..."
gcloud pubsub subscriptions pull sports --auto-ack --limit=3
echo " "

#step 14
echo "Finally, we can delete myTopic and sports subscription..."
gcloud pubsub subscriptions delete sports
gcloud pubsub topics delete myTopic
echo " "

#step 15
echo "Let's confirm all deleted..."
gcloud pubsub topics list
echo " "

#step 16
echo "Exiting Cloud Shell..."
echo ".........."
exit










