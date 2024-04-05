# Webbutveckling / Agil Utveckling, Projektarbete - Projektplanering

## Endpoints

### Event Endpoints

| Path                          | Method | Request         | Response | ResponseCodes | Description       |
| ----------------------------- | ------ | --------------- | -------- | ------------- | ----------------- |
| "/events"                     | GET    | NONE            | Event[]  | 200, 404      | Get all events    |
| "/events/id/{id}"             | GET    | int Id          | Event    | 200, 404      | Get event by id   |
| "/events/name/{name}"         | GET    | string Name     | Event    | 200, 404      | Get event by name |
| "/events/category/{category}" | GET    | string Category | Event    | 200, 404      | Get event by name |

### User Endpoints

| Path                   | Method | Request      | Response | ResponseCodes | Description       |
| ---------------------- | ------ | ------------ | -------- | ------------- | ----------------- |
| "/users/"              | GET    | NONE         | User[]   | 200           | Get all users     |
| "/users/{userId}"      | GET    | int userId   | User     | 200, 404      | Get user by id    |
| "/users/email/{email}" | GET    | string Email | User     | 200, 404      | Get user by email |
| "/users/role/{role}"   | GET    | string Role  | User     | 200, 404      | Get user by role  |
| "/users/"              | POST   | User         | NONE     | 200, 400      | Add new user      |
| "/users/{userId}"      | DELETE | int userId   | NONE     | 200, 404      | Delete user       |

## Data

### ApplicationUser : IdentityUser

| Property Name | Data Type | Description                  |
| ------------- | --------- | ---------------------------- |
| FirstName     | string    | First name of user           |
| LastName      | string    | Last name of user            |
| Address       | string    | Street address of user       |
| Zipcode       | string    | Zip code of user             |
| City          | string    | City of residence            |
| Region        | string    | Region of residence of user  |
| Country       | string    | Country of residence of user |
| Orders        | Order[]   | List of orders made by user  |
| Role          | string    | Role of user                 |

### Event

| Property Name | Data Type | Description                         |
| ------------- | --------- | ----------------------------------- |
| Id            | int       | Id of event in database             |
| Title         | string    | Name of event                       |
| Description   | string    | Description of event                |
| Category      | string    | Category of event                   |
| Price         | double    | Price of event                      |
| DateOfEvent   | datetime  | Date and time of event              |
| NumberOfSpots | int       | Number of available spots for event |
| MinimumAge    | int       | Minimum age for entry               |
| Address       | string    | Street address of user              |
| Zipcode       | string    | Zip code of user                    |
| City          | string    | City of residence                   |
| Participants  | string[]  | Email addresses for participants    |

### Category

| Property Name | Data Type | Description                  |
| ------------- | --------- | ---------------------------- |
| Id            | int       | Id for database              |
| Name          | string    | Name of category in database |

### Order

| Property Name | Data Type               | Description                     |
| ------------- | ----------------------- | ------------------------------- |
| Id            | int                     | Id for database                 |
| CustomerId    | int                     | Id for customer that made order |
| OrderDate     | DateTime                | Date and time of making order   |
| TotalPrice    | Double                  | Total price of order            |
| EventsInOrder | ICollection<EventOrder> | Many-to-many list               |

### EventOrder (Junction Table)

| Property Name | Data Type | Description                            |
| ------------- | --------- | -------------------------------------- |
| Id            | int       | Id for database                        |
| EventId       | int       | FK to Event.Id                         |
| Event         | Event     | Events in event order                  |
| OrderId       | int       | FK to Order.Id                         |
| Order         | Order     | Order in product order                 |
| Amount        | int       | Amount of set product in product order |
