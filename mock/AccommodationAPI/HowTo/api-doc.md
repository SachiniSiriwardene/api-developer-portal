# How to Use the Accommodation API

## Samples

The **Accommodation API** allows you to search, retrieve, and manage accommodation listings, availability, and bookings. This guide provides step-by-step instructions on how to integrate and use the API effectively.

## Prerequisites

Before you begin, ensure you have:

- An **API key** (sign up at [Developer Portal](https://developer.example.com)).
- A valid **OAuth 2.0 token** for authentication.
- A basic understanding of **RESTful API principles**.

## Authentication

The API uses **OAuth 2.0** for authentication. Include your **Bearer Token** in the `Authorization` header of each request:

```http
GET /accommodations HTTP/1.1
Host: api.example.com
Authorization: Bearer YOUR_ACCESS_TOKEN
```

## Searching for Accommodations

To retrieve available accommodations based on location and date range, use the following request:

```http
GET /accommodations/search?location=NewYork&checkin=2025-06-01&checkout=2025-06-10&guests=2
Host: api.example.com
Authorization: Bearer YOUR_ACCESS_TOKEN
```

### Sample Response

```json
{
  "results": [
    {
      "id": "12345",
      "name": "Grand Hotel NYC",
      "location": "New York, USA",
      "price_per_night": 150,
      "availability": true
    }
  ]
}
```

## Retrieving Accommodation Details

To get detailed information about a specific accommodation:

```http
GET /accommodations/{id}
Host: api.example.com
Authorization: Bearer YOUR_ACCESS_TOKEN
```

### Example Response

```json
{
  "id": "12345",
  "name": "Grand Hotel NYC",
  "location": "New York, USA",
  "description": "A luxury hotel in the heart of NYC.",
  "amenities": ["WiFi", "Pool", "Gym"],
  "price_per_night": 150
}
```

## Creating a Booking

To create a new booking, send a `POST` request with booking details:

```http
POST /bookings
Host: api.example.com
Authorization: Bearer YOUR_ACCESS_TOKEN
Content-Type: application/json

{
  "accommodation_id": "12345",
  "checkin": "2025-06-01",
  "checkout": "2025-06-10",
  "guests": 2
}
```

### Sample Response

```json
{
  "booking_id": "67890",
  "status": "confirmed",
  "total_price": 1350
}
```

## Cancelling a Booking

To cancel a booking, send a `DELETE` request:

```http
DELETE /bookings/{booking_id}
Host: api.example.com
Authorization: Bearer YOUR_ACCESS_TOKEN
```

### Sample Response

```json
{
  "status": "cancelled",
  "refund_amount": 1200
}
```

## Error Handling

The API returns standard HTTP status codes. Common errors include:

| Status Code | Meaning                                 |
| ----------- | --------------------------------------- |
| 400         | Bad Request (Invalid parameters)        |
| 401         | Unauthorized (Invalid API key or token) |
| 404         | Not Found (Invalid resource ID)         |
| 500         | Internal Server Error                   |

## Conclusion

With these endpoints, you can integrate accommodation search, retrieval, booking, and cancellation into your applications. For further details, refer to the [API Reference](https://developer.example.com/docs/accommodation-api).

