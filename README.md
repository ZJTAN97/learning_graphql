# Graphql

-   Draft of key learning points

---

# Custom Object Type

-   The resolvers must match the schema defined in graphql

`schema.graphql`

```

type Job {
    id: ID
    title: String
    description: String
}

```

`resolvers`

```

export const resolvers = {
    Query: {
        job: () => {
            return {
                id: "some-id"
                title: "The title",
                description: "Some Description"
            }
        }
    }
}

```

---

# Arrays and Non-Nullability

To make fields non null, add "!"

```

type Job {
    id: ID! # cannot be null
    title: String! # cannot be null
    description: String
}

```

To make arrays

```

// Schema
type Query {
    jobs: [Job!] // to define array and prevent nullable
}

// resolver
// note the "jobs" and return array
export const resolvers = {
    Query: {
        jobs: () => {
            return [
                {
                    id: "test-id",
                    title: "The title",
                    description: "Some description"
                }
            ]
        }
    }
}

```
