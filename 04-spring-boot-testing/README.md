## 04 Spring Testing, Creacion de Tests para capa de Controller


### Testing controller layer
- @WebMvcTest, Spring provee la anotacion para testear controllers
- @WebMvcTest, Carga solo el controller especificado y sus dependencias sin  cargar la app entera.
- @SpringBootTest, Para test de integracion, Crea un contexto de la applicacion y la carga completamente.
- @MockBean, Tells Spring to create a mock instance of an EmployeeService and add it to the application context,
  so that's injected into EmployeeController
- MockMvc Es un utilitario para pruebas de integracion.
- ObjectMapper Serialize & Deserialize objects

### willReturn && willAnswer
- Dentro de la prueba, se aprovecha willAnswer() para calcular dinámicamente el valor de retorno para el método simulado. 
- En lugar de simplemente devolver un valor constante, el método procesa sus argumentos de entrada, 
- mostrando la flexibilidad de willAnswer(). 
- La función willAnswer() de BDDMockito otorga a los desarrolladores el poder de crear respuestas dinámicas en pruebas 
- unitarias de estilo BDD. Si bien los métodos más simples como willReturn() tienen su lugar, 
- willAnswer() destaca cuando necesitas dar cabida a respuestas más complejas y dependientes de argumentos.
- Adoptar willAnswer() puede conducir a pruebas más flexibles y adaptables, asegurando que nuestros comportamientos 
- simulados puedan adaptarse a una variedad de escenarios de prueba.


- Para testear la capa de controllers, se requiere Mockear la capa de service
- Sintaxis para BDD:
  - @Test
  - public void given_when_then(){
  - // given - precondition or setup
  - // when - action ot the behaviour we're testing
  - // then - verify the output
  - }

### @Mock @InjectMocks
- @Mock annotation creates mocks.
- @InjectMocks creates actual objects and injects mocked dependencies into it.

### Testing metodos void
- willDoNothing().given(employeeRepository).deleteById(employeeId);
- No se puede testear con Asset, entonces :
- verify(employeeRepository, times(1)).deleteById(employeeId);


