# 3.1 GraphQLSource

For further customizations, can declare `GraphQlSourceBuilderCustomizer` bean

```

@Configuration(proxyBeanMethods = false)
class GraphQlConfig {

    @Bean
    public GraphQlSourceBuilderCustomizer sourceBuilderCustomizer() {
        return (builder) ->
                builder.configureGraphQl(graphQlBuilder ->
                        graphQlBuilder.executionIdProvider(new CustomExecutionIdProvider()));
    }
}

```

## 3.1.1 Schema Resources

By default, the Boot starter looks for schema files with extensions ".graphqls" or ".gqls" under the location classpath:graphql/\*\*, which is typically src/main/resources/graphql


