### API Implementation
- The API relies on generated interfaces based on the OpenAPI specification
- The Gradle task `generateApi` needs to be executed before being able to run the project
- When the API is started the swagger UI is available at `http://localhost:8080/swagger-ui.html`
- API und DB models are transformed to each other by classes that inherit from ModelTransformer under `src/main/java/de/tudresden/inf/st/mathgrassserver/transform`
- Endpoints are described in OpenAPI specification