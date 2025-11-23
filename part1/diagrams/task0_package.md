flowchart TD

subgraph Presentation_Layer [Presentation Layer]
    API[API / Services]
end

subgraph Business_Layer [Business Logic Layer]
    Facade[Facade]
    Models[User, Place, Review, Amenity Models]
end

subgraph Persistence_Layer [Persistence Layer]
    Repository[Repositories / Database Access]
    Database[(Database)]
end

API --> Facade
Facade --> Models
Models --> Facade
Facade --> Repository
Repository --> Database
