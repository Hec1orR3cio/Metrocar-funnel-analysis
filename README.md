# Metrocar funnel analysis:

## The dataset:

### Access importing URL
postgres://Test:bQNxVzJL4g6u@ep-noisy-flower-846766-pooler.us-east-2.aws.neon.tech/Metrocar

### app_downloads: contains information about app downloads
- app_download_key: unique id of an app download
- platform: ios, android or web
- download_ts: download timestamp

### signups: contains information about new user signups
- user_id: primary id for a user
- session_id: id of app download
- signup_ts: signup timestamp
- age_range: the age range the user belongs to

### ride_requests: contains information about rides
- ride_id: primary id for a ride
- user_id: foreign key to user (requester)
- driver_id: foreign key to driver
- request_ts: ride request timestamp
- accept_ts: driver accept timestamp
- pickup_location: pickup coordinates
- destination_location: destination coordinates
- pickup_ts: pickup timestamp
- dropoff_ts: dropoff timestamp
- cancel_ts: ride cancel timestamp (accept, pickup and dropoff timestamps may be null)

### transactions: contains information about financial transactions based on completed rides:
- ride_id: foreign key to ride
- purchase_amount_usd: purchase amount in USD
- charge_status: approved, cancelled
- transaction_ts: transaction timestamp
  
### reviews: contains information about driver reviews once rides are completed
- review_id: primary id of review
- ride_id: foreign key to ride
- driver_id: foreign key to driver
- user_id: foreign key to user (requester)
- rating: rating from 0 to 5
- free_response: text response given by user/requester
