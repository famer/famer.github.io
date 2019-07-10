---
title: Spring CORS for Data REST Repository
---

Contemporary trend of microservices and service oriented architectures states new challenges for interconnecting modules and creating channels for communication of those modules. 
Some of the solutions involve common BUS to tie up services. But in many cases it's cheaper to avoid communication BUS and to place service to separate domain.

So consumers of those API's could be web applications as well. Those clients require remote server to allow them to access the data from different domain in order to protect security.

For those purposes CORS header has been stated. It's a special HTTP header produced by server that is going to be accessed and points to domains from which it could be done.

Spring Data based REST repositories are really easy to be implemented and by default do not allow cross domain access. To enable their data for web based clients following class must be included to the project.

```
import java.io.IOException;
import javax.servlet.Filter;
import javax.servlet.FilterChain;
import javax.servlet.FilterConfig;
import javax.servlet.ServletException;
import javax.servlet.ServletRequest;
import javax.servlet.ServletResponse;
import javax.servlet.http.HttpServletResponse;
import org.springframework.stereotype.Component;

@Component
public class SimpleCORSFilter implements Filter {

	public void doFilter(ServletRequest req, ServletResponse res, FilterChain chain) throws IOException, ServletException {
		HttpServletResponse response = (HttpServletResponse) res;
		response.setHeader("Access-Control-Allow-Origin", "*");
		response.setHeader("Access-Control-Allow-Methods", "POST, GET, PUT, OPTIONS, DELETE");
		response.setHeader("Access-Control-Max-Age", "3600");
		response.setHeader("Access-Control-Allow-Headers", "Origin, X-Requested-With, Content-Type, Accept");
		chain.doFilter(req, res);
	}

	public void init(FilterConfig filterConfig) {}

	public void destroy() {}

}
```

So mentioned filter will attach required headers to every request. 
