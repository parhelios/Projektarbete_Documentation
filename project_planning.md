# Webbutveckling / Agil Utveckling, Projektarbete - Projektplanering

## Endpoints

### Event Endpoints

| Path                          | Method | Request         | Response | ResponseCodes | Description            |
| ----------------------------- | ------ | --------------- | -------- | ------------- | ---------------------- |
| "/events"                     | GET    | NONE            | Event[]  | 200, 404      | Get all events         |
| "/events/id/{id}"             | GET    | int Id          | Event    | 200, 404      | Get event by id        |
| "/events/name/{name}"         | GET    | string Name     | Event    | 200, 404      | Get event by name      |
| "/events/category/{category}" | GET    | string Category | Event    | 200, 404      | Get event by category  |
| "/events"                     | POST   | Event           | NONE     | 200, 400      | Add new event          |
| "/events/{id}"                | PUT    | int Id, Event   | NONE     | 200, 404      | Update event           |
| "/events/status/{id}"         | PATCH  | NONE            | NONE     | 200, 400      | Toggle status on event |
| "/events/{id}                 | DELETE | int Id          | NONE     | 200, 404      | Delete event           |

### User Endpoints

| Path                   | Method | Request                 | Response | ResponseCodes | Description       |
| ---------------------- | ------ | ----------------------- | -------- | ------------- | ----------------- |
| "/users/"              | GET    | NONE                    | User[]   | 200           | Get all users     |
| "/users/{userId}"      | GET    | int userId              | User     | 200, 404      | Get user by id    |
| "/users/email/{email}" | GET    | string Email            | User     | 200, 404      | Get user by email |
| "/users/role/{role}"   | GET    | string Role             | User[]   | 200, 404      | Get users by role |
| "/users/"              | POST   | User                    | NONE     | 200, 400      | Add new user      |
| "/users/{userId}"      | PUT    | int userId, ContactInfo | NONE     | 200, 404      | Update user info  |
| "/users/{userId}"      | DELETE | int userId              | NONE     | 200, 404      | Delete user       |

### Category Endpoints

| Path             | Method | Request  | Response   | ResponseCodes | Description        |
| ---------------- | ------ | -------- | ---------- | ------------- | ------------------ |
| "/category"      | GET    | NONE     | Category[] | 200           | Get all categories |
| "/category/{id}" | GET    | int Id   | Category   | 200           | Get category by id |
| "/category"      | POST   | Category | NONE       | 200, 400      | Add new category   |
| "/category/{id}" | DELETE | int Id   | NONE       | 200, 404      | Delete category    |

### Order

| Path                 | Method | Request          | Response | ResponseCodes | Description         |
| -------------------- | ------ | ---------------- | -------- | ------------- | ------------------- |
| "/order"             | GET    | NONE             | Order[]  | 200           | Get all order       |
| "/order/{orderId}"   | GET    | int orderId      | Order    | 200, 404      | Get order by id     |
| "/order/{userEmail}" | POST   | string userEmail | Order    | 200, 400      | Create a user order |

## Entities

### ApplicationUser : IdentityUser

| Property Name | Data Type | Description                  |
| ------------- | --------- | ---------------------------- |
| FirstName     | string    | First name of user           |
| LastName      | string    | Last name of user            |
| FullName      | string    | Full name of user            |
| Address       | string    | Street address of user       |
| Zipcode       | string    | Zip code of user             |
| City          | string    | City of residence            |
| Region        | string    | Region of residence of user  |
| Country       | string    | Country of residence of user |
| OrderIds      | int[]     | List of orders made by user  |
| Role          | string    | Role of user                 |

### Event

| Property Name   | Data Type | Description                         |
| --------------- | --------- | ----------------------------------- |
| Id              | int       | Id of event in database             |
| Title           | string    | Name of event                       |
| Description     | string    | Description of event                |
| Category        | Category  | Category of event                   |
| Price           | double    | Price of event                      |
| DateTimeOfEvent | datetime  | Date and time of event              |
| NumberOfSpots   | int       | Number of available spots for event |
| MinimumAge      | int       | Minimum age for entry               |
| Address         | string    | Street address of user              |
| Zipcode         | string    | Zip code of user                    |
| City            | string    | City of residence                   |
| Participants    | string[]  | Email addresses for participants    |
| Status          | bool      | Status of event                     |

### Category

| Property Name | Data Type | Description                  |
| ------------- | --------- | ---------------------------- |
| Id            | int       | Id for database              |
| Name          | string    | Name of category in database |

### Order

| Property Name | Data Type               | Description                        |
| ------------- | ----------------------- | ---------------------------------- |
| Id            | int                     | Id for database                    |
| CustomerEmail | string                  | Email for customer that made order |
| OrderDateTime | dateTime                | Date and time of making order      |
| TotalPrice    | double                  | Total price of order               |
| EventsInOrder | ICollection<EventOrder> | Many-to-many list                  |

### EventOrder (Junction Table)

| Property Name | Data Type | Description                            |
| ------------- | --------- | -------------------------------------- |
| Id            | int       | Id for database                        |
| EventId       | int       | FK to Event.Id                         |
| Event         | Event     | Events in event order                  |
| OrderId       | int       | FK to Order.Id                         |
| Order         | Order     | Order in product order                 |
| Amount        | int       | Amount of set product in product order |
