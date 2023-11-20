package br.com.fiap.fmba.controller;

import static org.junit.jupiter.api.Assertions.assertEquals;

import org.junit.Before;
import org.junit.Test;
import org.junit.runner.RunWith;
import org.mockito.Mockito;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.boot.test.context.TestConfiguration;
import org.springframework.boot.test.mock.mockito.MockBean;
import org.springframework.context.annotation.Bean;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.test.context.junit4.SpringRunner;

import br.com.fiap.fmba.controller.payload.autenticacao.LoginRequest;
import br.com.fiap.fmba.controller.payload.autenticacao.LoginResponse;
import br.com.fiap.fmba.resources.exception.AutenticatorException;
import br.com.fiap.fmba.resources.exception.WebServiceException;
import br.com.fiap.fmba.service.AutenticacaoService;

@RunWith(SpringRunner.class)
public class LoginControllerTest {
	
	static final LoginResponse LOGIN = LoginResponse.builder()
			.usuario("Mock Usuario")
			.nome("Mock Nome")
			.token("Mock Token")
			.build(); 

	@TestConfiguration
    static class LoginControllerTestConfiguration {        
		
		@Bean
        public LoginController loginController() {
            return new LoginController();
        }
    }
	
	@Autowired
	private LoginController controller;
	
	@MockBean
	private AutenticacaoService service;
	
	@Before
	public void setUp() throws AutenticatorException {
	    Mockito.when(service.login(Mockito.any(LoginRequest.class))).thenReturn(LOGIN);
	}

	@Test
	public void testLogin() throws AutenticatorException, WebServiceException {
		ResponseEntity<LoginResponse> login = controller.login(LoginRequest.builder()
				.usuario("Mock Usuario")
				.senha("Mock Senha")
				.build());
		
		assertEquals(login.getStatusCode(), HttpStatus.OK);
		assertEquals(login.getBody(), LOGIN);
	}

}
