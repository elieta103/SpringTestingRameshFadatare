## 06 TestContainers
- Testcontainers is a JavaLibrary that supports JUnit test, providing lightweight
- throwaway instances of common databases, Selenium web browsers, or anything else that can run
- in a Docker container.
- Using Testcontainers is fairly easy and it gives us the opportunity to create integration test
- without the need of pre-installed components.
- Using Testcontainers, we would always start with a clean database and our integration test could run on 
- any machine

### Es requerido tener docker corriendo.
1. Testcontainer pull mysql docker image from the docker hub
2. Deploy MySQL in a docker container
3. Run the integration test with MySQL database (deployed in docker container)


### Dependencias
- No eliminar dependencias de MySQL
```
<dependency>
			<groupId>org.testcontainers</groupId>
			<artifactId>testcontainers</artifactId>
			<version>1.19.5</version>
			<scope>test</scope>
		</dependency>
		<dependency>
			<groupId>org.testcontainers</groupId>
			<artifactId>junit-jupiter</artifactId>
			<version>1.19.5</version>
			<scope>test</scope>
		</dependency>

		<dependency>
			<groupId>org.testcontainers</groupId>
			<artifactId>mysql</artifactId>
			<version>1.19.5</version>
			<scope>test</scope>
		</dependency>
```


## MySQL database to testing integrations with container and without container
- EmployeeRepositoryTests 
  - Descomentar H2 del pom.xml y correr
- EmployeeRepositoryIntegrationTests
  - Descomentar MySQL del pom.xml y correr
  - docker-compose up
- EmployeeRepositoryIntegrationContainerTests
  - Requiere dependencias de testcontainer
  - Tener iniciado docker


  
## @DynamicPropertySource
- Usada en los de test de integracion para agregar properties del PropertySources en el Environment


## Estructura de los metodos para los tests de integración
- Para testear la capa de controllers, son pruebas de integracion, no se usa Mockito
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


