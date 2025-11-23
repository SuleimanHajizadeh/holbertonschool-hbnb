classDiagram

class User {
  +UUID id
  +string first_name
  +string last_name
  +string email
  +string password
  +bool is_admin
  +datetime created_at
  +datetime updated_at
  +create()
  +update()
  +delete()
}

class Place {
  +UUID id
  +string title
  +string description
  +float price
  +float latitude
  +float longitude
  +datetime created_at
  +datetime updated_at
  +create()
  +update()
  +delete()
}

class Review {
  +UUID id
  +int rating
  +string comment
  +datetime created_at
  +datetime updated_at
  +create()
  +update()
  +delete()
}

class Amenity {
  +UUID id
  +string name
  +string description
  +datetime created_at
  +datetime updated_at
  +create()
  +update()
  +delete()
}

User "1" --> "many" Place : owns
User "1" --> "many" Review : writes
Place "1" --> "many" Review : has
Place "many" -- "many" Amenity : includes
