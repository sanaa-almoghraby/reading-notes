# Serving Web Content with Spring MVC
### Starting with Spring Initializr
To manually initialize the project:

1. Navigate to https://start.spring.io. This service pulls in all the dependencies you need for an application and does most of the setup for you.

2. Choose either Gradle or Maven and the language you want to use. This guide assumes that you chose Java.

3. Click Dependencies and select Spring Web, Thymeleaf, and Spring Boot DevTools.

4. Click Generate.

5. Download the resulting ZIP file, which is an archive of a web application that is configured 
with your choices.

#### Create a Web Controller
In Spring’s approach to building web sites, HTTP requests are handled by a controller. You can easily identify the controller by the @Controller annotation. In the following example, GreetingController handles GET requests for /greeting by returning the name of a View (in this case, greeting). A View is responsible for rendering the HTML content. The following listing (from src/main/java/com/example/servingwebcontent/GreetingController.java) shows the controller:
package com.example.servingwebcontent;

import org.springframework.stereotype.Controller;
import org.springframework.ui.Model;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;

@Controller
public class GreetingController {

	@GetMapping("/greeting")
	public String greeting(@RequestParam(name="name", required=false, defaultValue="World") String name, Model model) {
		model.addAttribute("name", name);
		return "greeting";
	}

}
### Spring Boot Devtools
* Enables hot swapping.

* Switches template engines to disable caching.

* Enables LiveReload to automatically refresh the browser.

* Other reasonable defaults based on development instead of production.
### Run the Application
package com.example.servingwebcontent;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class ServingWebContentApplication {

    public static void main(String[] args) {
        SpringApplication.run(ServingWebContentApplication.class, args);
    }

}
@SpringBootApplication is a convenience annotation that adds all of the following:

@Configuration: Tags the class as a source of bean definitions for the application context.

@EnableAutoConfiguration: Tells Spring Boot to start adding beans based on classpath settings, other beans, and various property settings. For example, if spring-webmvc is on the classpath, this annotation flags the application as a web application and activates key behaviors, such as setting up a DispatcherServlet.

@ComponentScan: Tells Spring to look for other components, configurations, and services in the com/example package, letting it find the controllers.

The main() method uses Spring Boot’s SpringApplication.run() method to launch an application. Did you notice that there was not a single line of XML? There is no web.xml file, either. This web application is 100% pure Java and you did not have to deal with configuring any plumbing or infrastructure.

### Spring model attributes
There are several ways of adding model attributes to a view in Spring MVC
Add attribute to Model via its addAttribute method:

    @RequestMapping(value = "message", method = RequestMethod.GET)
        public String messages(Model model) {
            model.addAttribute("messages", messageRepository.findAll());
            return "message/list";
        }
Return ModelAndView with model attributes included:

    @RequestMapping(value = "message", method = RequestMethod.GET)
        public ModelAndView messages() {
            ModelAndView mav = new ModelAndView("message/list");
            mav.addObject("messages", messageRepository.findAll());
            return mav;
        }
Expose common attributes via methods annotated with @ModelAttribute:

    @ModelAttribute("messages")
        public List<Message> messages() {
            return messageRepository.findAll();
        }
You can access model attributes in views with Thymeleaf as follows:

    <tr th:each="message : ${messages}">
            <td th:text="${message.id}">1</td>
            <td><a href="#" th:text="${message.title}">Title ...</a></td>
            <td th:text="${message.text}">Text ...</td>
        </tr>

### Request parameters
Request parameters can be easily accessed in Thymeleaf views. Request parameters are passed from the client to server like:

    https://example.com/query?q=Thymeleaf+Is+Great!
Let’s assume we have a @Controller that sends a redirect with a request parameter:

    @Controller
        public class SomeController {
            @RequestMapping("/")
            public String redirect() {
                return "redirect:/query?q=Thymeleaf+Is+Great!";
            }
        }
In order to access the q parameter you can use the param. prefix:

    <p th:text="${param.q}">Test</p>
In the above example if parameter q is not present, empty string will be displayed in the above paragraph otherwise the value of q will be shown.

Since parameters can be multivalued (e.g. `https://example.com/query?q=Thymeleaf%20Is%20Great!&q=Really%3F) you may access them using brackets syntax:

    <p th:text="${param.q[0] + ' ' + param.q[1]}" th:unless="${param.q == null}">Test</p>
Note: If you access multivalued parameter with ${param.q} you will get a serialized array as a value.

Another way to access request parameters is by using the special #request object that gives you direct access to the javax.servlet.http.HttpServletRequest object:

    <p th:text="${#request.getParameter('q')}" th:unless="${#request.getParameter('q') == null}">Test</p>

