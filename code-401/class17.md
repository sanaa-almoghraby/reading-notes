# Spring Boot and OAuth2
The samples are all single-page apps using Spring Boot and Spring Security on the back end. They also all use plain jQuery on the front end. But, the changes needed to convert to a different JavaScript framework or to use server-side rendering would be minimal.
There are several samples building on each other, adding new features at each step:

* simple: a very basic static app with just a home page and unconditional login via Spring Boot’s OAuth 2.0 configuration properties (if you visit the home page, you will be automatically redirected to GitHub).
* click: adds an explicit link that the user has to click to login.

* logout: adds a logout link as well for authenticated users.

* two-providers: adds a second login provider so the user can choose on the home page which one to use.
* custom-error: adds an error message for unauthenticated users, and a custom authentication based on GitHub’s API.
## Add a New GitHub App
To use GitHub’s OAuth 2.0 authentication system for login, you must first Add a new GitHub app.

Select "New OAuth App" and then the "Register a new OAuth application" page is presented. Enter an app name and description. Then, enter your app’s home page, which should be http://localhost:8080, in this case. Finally, indicate the Authorization callback URL as http://localhost:8080/login/oauth2/code/github and click Register Application.

The OAuth redirect URI is the path in the application that the end-user’s user-agent is redirected back to after they have authenticated with GitHub and have granted access to the application on the Authorize application 
# Add a Welcome Page
In this section, you’ll modify the simple app you just built by adding an explicit link to login with GitHub. Instead of being redirected immediately, the new link will be visible on the home page, and the user can choose to login or to stay unauthenticated. Only when the user has clicked on the link will the secure content be rendered.
To render content on the condition that the user is authenticated, you have the option of either server-side or client-side rendering.

Here, you’ll change the client side with JQuery, though if you prefer to use something else, it shouldn’t be very hard to translate the client code.

To get started with the dynamic content, you need to mark a couple of HTML elements like so:

index.html
<div class="container unauthenticated">
    With GitHub: <a href="/oauth2/authorization/github">click here</a>
</div>
<div class="container authenticated" style="display:none">
    Logged in as: <span id="user"></span>
</div>

#### The /user Endpoint
Now, you’ll add the server-side endpoint just mentioned, calling it /user. It will send back the currently logged-in user, which we can do quite easily in our main class:

SocialApplication.java
@SpringBootApplication
@RestController
public class SocialApplication {

    @GetMapping("/user")
    public Map<String, Object> user(@AuthenticationPrincipal OAuth2User principal) {
        return Collections.singletonMap("name", principal.getAttribute("name"));
    }

    public static void main(String[] args) {
        SpringApplication.run(SocialApplication.class, args);
    }

}
Note the use of @RestController, @GetMapping, and the OAuth2User injected into the handler method.

### Adding a Logout Endpoint

### Adding the CSRF Token in the Client
Since we are not using a higher level framework in this sample, you’ll need to explicitly add the CSRF token, which you just made available as a cookie from the backend. To make the code a bit simpler, include the js-cookie library:

pom.xml
<dependency>
    <groupId>org.webjars</groupId>
    <artifactId>js-cookie</artifactId>
    <version>2.1.0</version>
</dependency>COPY
And then, you can reference it in your HTML:

index.html
<script type="text/javascript" src="/webjars/js-cookie/js.cookie.js"></script>

#### How to Add a Local User Database
Many applications need to hold data about their users locally, even if authentication is delegated to an external provider. We don’t show the code here, but it is easy to do in two steps.
1. Choose a backend for your database, and set up some repositories (using Spring Data, say) for a custom User object that suits your needs and can be populated, fully or partially, from external authentication.
2. Implement and expose OAuth2UserService to call the Authorization Server as well as your database. Your implementation can delegate to the default implementation, which will do the heavy lifting of calling the Authorization Server. Your implementation should return something that extends your custom User object and implements OAuth2User.


