Here’s what our smart contract should be able to handle:

Creation of a new event:

-A unique ID
-A reference to who created the event (a wallet address of the creator)
-The time of the event, so we know when refunds should become available.
-The maximum capacity of attendees for that event
-The deposit amount for that event
-Keep track of those who RSVP’d
-Keep track of users who check into the event
-Find the difference between those who RSVP’d and those who checked in, and refund everyone except those.

RSVP to an event:

-Pass in a unique event ID the user wishes to RSVP to:
-Ensure that the value of their deposit is sufficient for that event’s deposit requirement
-Ensure that the event hasn’t already started based on the timestamp of the event - people shouldn’t be able to RSVP after the event has started
-Ensure that the event is under max capacity

Check in attendees:

-Pass a unique event ID for the event the user wants to confirm users for
-Ensure that only the creator of the event can confirm attendees
-Pass in the attendee address of the user who is checking in and check if their address is saved in RSVP list
-If they are found in the RSVP list, add them to a list of confirmed attendees
-If user is in the confirmed attendees list, return their deposit

Withdraw any remaining deposits from guests who didn’t check in and send them to the owner of the event:

-Pass in a unique event ID for the event the user wishes to withdraw funds from
-Ensure that at least 7 days have passed since the event
-Find the difference in the number of guests who rsvp’d and guests who checked in
-Multiply the deposit amount times the discrepancy of guests between rsvp and check in and send the amount back to the owner

Events and Subgraphs
As we’re writing our smart contract, we’re going to create custom events that will help us build our subgraph. 
Events are triggers that the frontend and subgraph can listen to, and this makes them perfect for conditionally executing code on the front end and conditionally indexing data.
