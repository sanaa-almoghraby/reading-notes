# Working with Relationships in Spring Data REST
2. One-to-One Relationship

2.1. The Data Model

We must be careful to have different names for each association resource. Otherwise, we will encounter a JsonMappingException with the message: “Detected multiple association links with same relation type! Disambiguate association”.

2.2. The Repositories

2.3. Creating the Resources

2.4. Creating the Associations

After persisting both instances, we can establish the relationship by using one of the association resources.
This is done using the HTTP method PUT, which supports a media type of text/uri-list, and a body containing the URI of the resource to bind to the association.

3. One-to-Many Relationship
3.1. The Data Model
To exemplify a one-to-many relationship, let's add a new Book entity that will represent the “many” end of a relationship with the Library entity:

@Entity
public class Book {

    @Id
    @GeneratedValue
    private long id;
    
    @Column(nullable=false)
    private String title;
    
    @ManyToOne
    @JoinColumn(name="library_id")
    private Library library;
    
    // standard constructor, getter, setter
}

3.2. The Repository

3.3. The Association Resources
To remove an association, we can use the DELETE method on the association resource:

curl -i -X DELETE http://localhost:8080/books/1/library

4. Many-to-Many Relationship

4.1. The Data Model

4.2. The Repository

4.3. The Association Resources

5. Testing the Endpoints With TestRestTemplate
5.1. Testing the One-to-One Relationship

5.2. Testing the One-to-Many Relationship

5.3. Testing the Many-to-Many Relationship

For testing the many-to-many relationship between Book and Author entities, we will create a test method that saves one Author record and two Book records.

# Integration Testing in Spring
we'll need the latest junit-jupiter-engine, junit-jupiter-api, and Spring test dependencies:
<dependency>
    <groupId>org.junit.jupiter</groupId>
    <artifactId>junit-jupiter-engine</artifactId>
    <version>5.7.0</version>
    <scope>test</scope>
</dependency>
<dependency>
    <groupId>org.junit.jupiter</groupId>
    <artifactId>junit-jupiter-api</artifactId>
    <version>5.7.0</version>
    <scope>test</scope>
</dependency>
<dependency>
    <groupId>org.springframework</groupId>
    <artifactId>spring-test</artifactId>
    <version>5.3.3</version>
    <scope>test</scope>
</dependency>
For effective asserting of results, we're going to also use Hamcrest and JSON path:

<dependency>
    <groupId>org.hamcrest</groupId>
    <artifactId>hamcrest-library</artifactId>
    <version>2.2</version>
    <scope>test</scope>
</dependency>
<dependency>
    <groupId>com.jayway.jsonpath</groupId>
    <artifactId>json-path</artifactId>
    <version>2.5.0</version>
    <scope>test</scope>
</dependency>

3. Spring MVC Test Configuration

3.1. Enable Spring in Tests with JUnit 5

3.2. The WebApplicationContext Object

3.3. Mocking Web Context Beans
MockMvc provides support for Spring MVC testing. It encapsulates all web application beans and makes them available for testing.
3.4. Verify Test Configuration
Let's verify that we're loading the WebApplicationContext object (webApplicationContext) properly. We'll also check that the right servletContext is being attached:

@Test
public void givenWac_whenServletContext_thenItProvidesGreetController() {
    ServletContext servletContext = webApplicationContext.getServletContext();
    
    Assert.assertNotNull(servletContext);
    Assert.assertTrue(servletContext instanceof MockServletContext);
    Assert.assertNotNull(webApplicationContext.getBean("greetController"));
}

4. Writing Integration Tests

4.1. Verify View Name
@Test
public void givenHomePageURI_whenMockMVC_thenReturnsIndexJSPViewName() {
    this.mockMvc.perform(get("/homePage")).andDo(print())
      .andExpect(view().name("index"));
}
Let's break it down:

perform() method will call a GET request method, which returns the ResultActions. Using this result, we can have assertion expectations about the response, like its content, HTTP status, or header
andDo(print()) will print the request and response. This is helpful to get a detailed view in case of an error
andExpect() will expect the provided argument. In our case, we're expecting “index” to be returned via MockMvcResultMatchers.view()

4.2. Verify Response Body
andExpect(MockMvcResultMatchers.status().isOk()) will verify that response HTTP status is Ok (200). This ensures that the request was successfully executed
andExpect(MockMvcResultMatchers.jsonPath(“$.message”).value(“Hello World!!!”)) will verify that response content matches with the argument “Hello World!!!“. Here, we used jsonPath, which extracts response content and provides the requested value
andReturn() will return the MvcResult object, which is used when we have to verify something that isn't directly achievable by the library. In this case, we've added assertEquals to match the content type of the response that is extracted from the MvcResult object

4.3. Send GET Request With Path Variable

