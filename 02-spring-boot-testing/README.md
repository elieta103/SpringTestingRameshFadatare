## 02 Spring Testing, Creacion de Tests para capa de Repository

- La capa de repository no se conecta a la base de datos real.
- La capa de repository no usa Mockito, ya que no usa dependencies.

- Sintaxis para BDD:
  - @Test
  - public void given_when_then(){
  -    // given - precondition or setup
  -    // when  - action ot the behaviour we're testing
  -    // then  - verify the output
  - }

###  @DataJpaTest
- @DataJpaTest provee una BD in memory para testing
- @DataJpaTest, no carga beans (@Components, @Controller, @Service) en el ApplicationContext
- Por default busca @Entity, @Repository
- Tests anotados con @DataJpaTest son : @Transactional and roll back al final de cada test.
- Se puede agregar @RollbackTest en cada test para desactivar el rollback.
- Permite testear otros componentes JPA :

```
   @ExtendedWith(SpringExtension.class)
   @DataJpaTest
   class UserTest{
    @Autowired private DataSource dataSource;
    @Autowired private JdbcTemplate jdbcTemplate;
    @Autowired private EntityManager entityManager;
    @Autowired private UserRepository userRepository;
    
    @Test
    void injectedComponentsAreNotNull(){
      assertThat(dataSource).isNotNull();
      assertThat(jdbcTemplate).isNotNull();
      assertThat(entityManager).isNotNull();
      assertThat(userRepository).isNotNull();
    }
   }
```

###  @BeforeEach
- Usado para indicar lo que se debe ejecutar antes de cada metodo @Test 

