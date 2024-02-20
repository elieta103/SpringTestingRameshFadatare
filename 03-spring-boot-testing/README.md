## 03 Spring Testing, Creacion de Tests para capa de Service


### Testing service layer
- Para testear la capa de service, se requiere Mockear la capa de repository
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


