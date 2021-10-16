# Authentication and Access Control
Application security boils down to two more or less independent problems: authentication (who are you?) and authorization (what are you allowed to do?). Sometimes people say “access control” instead of "authorization", which can get confusing, but it can be helpful to think of it that way because “authorization” is overloaded in other places. Spring Security has an architecture that is designed to separate authentication from authorization and has strategies and extension points for both.

### Authentication
The main strategy interface for authentication is AuthenticationManager
An AuthenticationManager can do one of 3 things in its authenticate() method:

* Return an Authentication (normally with authenticated=true) if it can verify that the input represents a valid principal.

* Throw an AuthenticationException if it believes that the input represents an invalid principal.

* Return null if it cannot decide.
![](https://raw.githubusercontent.com/spring-guides/top-spring-security-architecture/main/images/authentication.png)

### Customizing Authentication Managers
AuthenticationManagerBuilder, which is great for setting up in-memory, JDBC, or LDAP user details or for adding a custom UserDetailsService. The following example shows an application that configures the global (parent) AuthenticationManager:

@Configuration
public class ApplicationSecurity extends WebSecurityConfigurerAdapter {

   ... // web stuff here

  @Autowired
  public void initialize(AuthenticationManagerBuilder builder, DataSource dataSource) {
    builder.jdbcAuthentication().dataSource(dataSource).withUser("dave")
      .password("secret").roles("USER");
  }

}
# Authorization or Access Control
Once authentication is successful, we can move on to authorization, and the core strategy here is AccessDecisionManager. There are three implementations provided by the framework and all three delegate to a chain of AccessDecisionVoter instances, a bit like the ProviderManager delegates to AuthenticationProviders.
# Web Security
Spring Security in the web tier (for UIs and HTTP back ends) is based on Servlet Filters, so it is helpful to first look at the role of Filters generally. The following picture shows the typical layering of the handlers for a single HTTP request.

![](https://raw.githubusercontent.com/spring-guides/top-spring-security-architecture/main/images/filters.png)
# Creating and Customizing Filter Chains
The default fallback filter chain in a Spring Boot application (the one with the /** request matcher) has a predefined order of SecurityProperties.BASIC_AUTH_ORDER. You can switch it off completely by setting security.basic.enabled=false, or you can use it as a fallback and define other rules with a lower order. To do the latter, add a @Bean of type WebSecurityConfigurerAdapter (or WebSecurityConfigurer) and decorate the class with @Order, as follows:

@Configuration
@Order(SecurityProperties.BASIC_AUTH_ORDER - 10)
public class ApplicationConfigurerAdapter extends WebSecurityConfigurerAdapter {
  @Override
  protected void configure(HttpSecurity http) throws Exception {
    http.antMatcher("/match1/**")
     ...;
  }
}
Spring Auth Cheat Sheet
Step 1: set up a user model and repo
Step 2: create a controller for that model
Step 3: UserDetailsServiceImpl implements UserDetailsService
gets a User from the database by username (make sure your repository has the method to make this easy!)

Step 4: ApplicationUser implements UserDetails
use IntelliJ to implement the methods; make the boolean ones all return true

Step 5: WebSecurityConfig extends WebSecurityConfigurerAdapter
has a UserDetailsService
passwordEncoder bean
configure AuthManagerBuilder
auth.userDetailsService(userDetailsService).passwordEncoder(passwordEncoder());
configure HttpSecurity
cors? csrf?
matchers for URLs that are allowed
ensure that login and signup URLs allowed; also consider homepage etc.
formLogin with login page set up
logout
    @Override
    @Bean
    public AuthenticationManager authenticationManagerBean() throws Exception {
        return super.authenticationManagerBean();
    }
Step 6: registration page
create it w/ form
ensure it posts to a route your controller is ready for
check it's saving in the DB
    // maybe autologin?
    Authentication authentication = new UsernamePasswordAuthenticationToken(newUser, null, new ArrayList<>());
    SecurityContextHolder.getContext().setAuthentication(authentication);
Step 7: login page
create it w/ form
ensure it posts to the route you specified in web config
try it out!
add to a template w/ things about the Principal