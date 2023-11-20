package br.com.fiap.fmba;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.web.servlet.config.annotation.EnableWebMvc;

@EnableWebMvc
@SpringBootApplication
public class FmbaApplication {
	
	private static final Logger LOGGER = LoggerFactory.getLogger(FmbaApplication.class);

	/**
	 * Bootstrap
	 * @param args
	 */
	public static void main(String[] args) {
		String env = System.getProperty("env");
		if(env == null) {			
			System.getProperties().put("env", "P");
		}
		LOGGER.info("=> Starting with enviroment: '{}'", env);		
		SpringApplication.run(FmbaApplication.class, args);
	}

}
