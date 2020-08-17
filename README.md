# MK Component Challenge

## Application URL
http://mkcomponentchallenge-env.eba-3fbtxtbc.us-east-1.elasticbeanstalk.com/

## About
Build a secure donation portal using the Moqui framework. The first page should present a form containing fields for Name, Email, Phone Number, Donation Amount, and Credit Card info. Upon submission, the form should store the correct data and process a payment. If payment is successful a confirmation page should be displayed.

## Screens
My screen designs were very straight forward, I created a main donation screen that would display my 2 subscreens. My 2 subscreens consist of the DonationForm and Success subscreen, the DonationForm contains all the input fields to process the donation and the Success subscreen it was is shown to the user after the DonationForm submits it's data.

## Transitions
The application has one transition in the DonationForm subscreen which calls the donation.DonationServices.create#Donation service that processes the form inputs and redirects to the Success subscreen.

## Entities
Initially I was going to create a donation entity and create my form using <auto-fields-entity> to populate my <form-list> but I quickly realized that doing things that way would require the user to enter their own donation ID so I opted to used the mantle.party services provided by the moqui framework.
  
## Services
Once the user submits the donation form, the transition calles the create Donation service that creates a person, stores the party contact info, creates a credit card, creates a payment then finally using AuthrizedDotNet processes the payment.

## Deployment
The application was deployed to aws Elastic Beanstalk by first creating the moqui-plus-runtime.war using the ./gradlew addRuntime command then uploading it using the Elastic Beanstalk UI.
