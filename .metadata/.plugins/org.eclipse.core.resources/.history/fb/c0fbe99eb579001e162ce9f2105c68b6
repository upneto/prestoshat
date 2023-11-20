package br.com.fiap.fmba.service;

import static org.junit.jupiter.api.Assertions.assertEquals;

import java.util.Collections;

import org.junit.Before;
import org.junit.Test;
import org.junit.runner.RunWith;
import org.mockito.InjectMocks;
import org.mockito.Mock;
import org.mockito.Mockito;
import org.springframework.boot.web.client.RestTemplateBuilder;
import org.springframework.http.HttpEntity;
import org.springframework.http.HttpHeaders;
import org.springframework.http.HttpMethod;
import org.springframework.http.HttpStatus;
import org.springframework.http.MediaType;
import org.springframework.http.ResponseEntity;
import org.springframework.test.context.junit4.SpringRunner;
import org.springframework.test.util.ReflectionTestUtils;
import org.springframework.web.client.RestTemplate;

import br.com.fiap.fmba.controller.payload.autenticacao.LoginRequest;
import br.com.fiap.fmba.controller.payload.autenticacao.LoginResponse;
import br.com.fiap.fmba.controller.payload.autenticacao.TokenRequest;
import br.com.fiap.fmba.resources.exception.AutenticatorException;

@RunWith(SpringRunner.class)
public class AutenticacaoServiceTest {
	

	@InjectMocks
	private AutenticacaoService service = new AutenticacaoService(Mockito.mock(RestTemplateBuilder.class));
	
	@Mock
	private RestTemplate restTemplate;
	
	private final String URL = "http://teste:8080/mock/";
	private HttpHeaders headers = new HttpHeaders();
	
	@Before
	public void setUp() throws Exception {
		ReflectionTestUtils.setField(service, "url", URL);
		
		headers.setContentType(MediaType.APPLICATION_JSON);
		headers.setAccept(Collections.singletonList(MediaType.APPLICATION_JSON));
	}

	@Test
	public void testLogin() throws AutenticatorException {
		
		LoginResponse response = LoginResponse.builder()
				.nome("Mock nome")
				.token("Mock token")
				.build();
		
		LoginRequest body = LoginRequest.builder()
				.usuario("Mock Usuario")
				.senha("Mock Senha")
				.build();
		
		Mockito.when(this.restTemplate.exchange(URL + "login", HttpMethod.POST, new HttpEntity<>(body, headers), LoginResponse.class))
			.thenReturn(new ResponseEntity<LoginResponse>(response, HttpStatus.OK));
		
		LoginResponse result = this.service.login(body);
		assertEquals(result, response);
	}

	@Test
	public void testVerify() throws AutenticatorException {
		
		LoginResponse response = LoginResponse.builder()
				.nome("Mock nome")
				.token("Mock token")
				.build();
		
		TokenRequest body = TokenRequest.builder()
				.token("Mock Token")
				.build();
		
		Mockito.when(this.restTemplate.exchange(URL + "login/verify", HttpMethod.POST, new HttpEntity<>(body, headers), LoginResponse.class))
			.thenReturn(new ResponseEntity<LoginResponse>(response, HttpStatus.OK));
		
		LoginResponse result = this.service.verify(body);
		assertEquals(result, response);
	}

}
