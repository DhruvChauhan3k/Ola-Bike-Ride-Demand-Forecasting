# Ola-Bike-Ride-Demand-Forecasting
Data File Link: https://drive.google.com/file/d/17Wkljr22Su5zYd8CDmYcCaE0OjZtRxC-/view?usp=sharing


Goal

We have to predict ride requests (demand forecast) for a particular latitude
and longitude for a requested future time window/duration.

Data Description

Raw Data contains a `number` (unique for every user), ride request DateTime (IST
time),
pickup and drop location latitude, and longitude.

Data Fields

1. number: unique id for every user
2. ts: DateTime of booking ride (IST time)
3. pick_lat: ride request pickup latitude
4. pick_lng: ride request pickup longitude
5. drop_lat: ride request drop latitude
6. drop_lng: ride request drop longitude

Defining a Good Ride Request
some guidelines to follow.

1. Count only 1 ride request by a user, if there are multiple bookings from the
same latitude and longitude within 1hour of the last booking time.
2. If there are ride requests within 8mins of the last booking time consider only 1
ride
request from a user (latitude and longitude may or may not be the same).
3. If the geodesic distance from pickup and drop point is less than 50meters
consider that ride request as a fraud ride request.
4. Consider all ride requests where pick up or drop location is outside India
bounding box: ['6.2325274', '35.6745457', '68.1113787', '97.395561'] as
system error.
5. Karnataka is our prime city where we have a lot of drivers and ride requests to
fulfill. We would not love to serve rides that are outside Karnataka and have
pickup and drop geodesic distance > 500kms. Karnataka bounding box:
['11.5945587', '18.4767308','74.0543908', '78.588083']

