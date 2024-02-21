## 05 Spring Testing, Creacion de Tests integracion con MySQL
- As the name suggests, integration tests focus on integrating different layers of the application
- That also means no mocking is involved.
- @SpringBootTest it will load complete application context

### @SpringBootTest
- Spring Boot provides @SpringBootTest annotation for Integration testing. This annotation creates an application 
- context and loads full application context.
- @SpringBootTest will bootstrap the full application context, which means we can @Autowire any bean that's picked up
- by component scanning into our test.

- @SpringBootTest By default does not start a server. We need to add attribute webEnvironment to further refine how
- tests run. It has several options:
  - MOCK(DEFAULT): Loads a web Application Context and provides a mock web environment.
  - RANDOM_PORT : Loads a WebServerApplicationContext and provides a real web environment. The embedded server is started
  - and listen on a random port.
  - DEFINED_PORT : Loads a WebServerApplicationContext and provides a real web environment.
  - NONE : Loads an ApplicationContext by using SpringApplication but does not provide any web environment.

## MySQL database to integration testing
- docker-compose up

## Estructura de los metodos para los tests de integración
- Para testear la capa de controllers, se requiere Mockear la capa de service
- Sintaxis para BDD:
  - @Test
  - public void given_when_then(){
  - // given - precondition or setup. IN INTEGRATION TEST NOT USE MOCKITO
  - // when - action ot the behaviour we're testing
  - // then - verify the output
  - }

## Test EmployeeRepository using MySQL
- EmployeeRepositoryIntegrationTests
  - @DataJpaTest
  - @AutoConfigureTestDatabase(replace = AutoConfigureTestDatabase.Replace.NONE)
  - Uses MySQL databse
- EmployeeRepositoryTests
  - @DataJpaTest 
  - Uses H2 In-memory database


