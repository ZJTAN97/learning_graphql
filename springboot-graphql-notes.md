# Controller

- Similar to REST, Spring Boot uses @Controller annotation to implement GraphQL APIs.
- All you need to do is annotate controller class with @Controller and define @QueryMapping or @SchemaMapping annotation on the handler method.
  - Spring will detect @Controller beans and register their annotated handler methods (@QueryMapping or @SchemaMapping) as Data fetcher which is also known as a resolver
- A resolver/DataFetcher is a function that’s responsible for populating the data for a single field in your GraphQL schema.


# Naming convention

For the following schema to work with DataFetchers and resolvers in Spring

```

type BioData {
    identificationDetails: IdentificationDetails
    addresses: Address
    citizenship: Citizenship
    driverLicense: DriverLicense
}

```

You have to follow the field name conventions defined in the schema so that the resolver can resolve and fetch correctly

```

public record BioData(
    String profileId, // Not in schema, used for argument purposes
    IdentificationDetails identificationDetails, 
    addresses: Address,
    citizenship: Citizenship,
    driverLicense: DriverLicense
) {}


@QueryMapping
BioData bioData(@Argument String profileId) {
    ...
}


```

