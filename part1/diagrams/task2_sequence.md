%% 1. User Registration
sequenceDiagram
participant User
participant API
participant Facade
participant UserModel
participant Repo
participant DB

User->>API: POST /users/register
API->>Facade: registerUser(data)
Facade->>UserModel: validate + create()
UserModel->>Repo: save()
Repo->>DB: INSERT user
DB-->>Repo: OK
Repo-->>Facade: userObj
Facade-->>API: response
API-->>User: 201 Created

%% 2. Place Creation
sequenceDiagram
participant User
participant API
participant Facade
participant PlaceModel
participant Repo
participant DB

User->>API: POST /places
API->>Facade: createPlace(data)
Facade->>PlaceModel: validate + create()
PlaceModel->>Repo: save()
Repo->>DB: INSERT place
DB-->>Repo: OK
Repo-->>Facade: placeObj
Facade-->>API: response
API-->>User: 201 Created

%% 3. Review Submission
sequenceDiagram
participant User
participant API
participant Facade
participant ReviewModel
participant Repo
participant DB

User->>API: POST /reviews
API->>Facade: createReview(data)
Facade->>ReviewModel: validate + create()
ReviewModel->>Repo: save()
Repo->>DB: INSERT review
DB-->>Repo: OK
Repo-->>Facade: reviewObj
Facade-->>API: response
API-->>User: 201 Created

%% 4. Fetch List of Places
sequenceDiagram
participant User
participant API
participant Facade
participant Repo
participant DB

User->>API: GET /places
API->>Facade: getPlaces(filters)
Facade->>Repo: select(filters)
Repo->>DB: SELECT * FROM places
DB-->>Repo: results
Repo-->>Facade: placeList
Facade-->>API: placeList
API-->>User: 200 OK
