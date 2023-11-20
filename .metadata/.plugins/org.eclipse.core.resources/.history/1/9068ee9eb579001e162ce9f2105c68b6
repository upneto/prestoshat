package br.com.fiap.fmba.controller;

import static org.junit.jupiter.api.Assertions.assertEquals;

import org.junit.Test;
import org.junit.runner.RunWith;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.TestConfiguration;
import org.springframework.context.annotation.Bean;
import org.springframework.http.HttpStatus;
import org.springframework.test.context.junit4.SpringRunner;

@RunWith(SpringRunner.class)
public class HealthControllerTest {
	
	@TestConfiguration
    static class HealthControllerTestConfiguration {        
		
		@Bean
        public HealthController healthController() {
            return new HealthController();
        }
    }
	
	@Autowired
	private HealthController controller;
	
	@Test
	public void testHealth() {
		assertEquals(this.controller.health().getStatusCode(), HttpStatus.OK);
	}

}
