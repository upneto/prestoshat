package br.com.fiap.fmba.service;

import static org.junit.Assert.assertArrayEquals;
import static org.junit.Assert.assertEquals;

import java.util.ArrayList;
import java.util.Collections;
import java.util.Date;
import java.util.List;

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

import br.com.fiap.fmba.resources.exception.BusinessException;
import br.com.fiap.fmba.resources.exception.WebServiceException;
import br.com.fiap.fmba.service.payload.ClientePayload;

@RunWith(SpringRunner.class)
public class ClienteServiceTest {
	
	static List<ClientePayload> LIST_RESULT = new ArrayList<>();
	static  {
		LIST_RESULT.add(ClientePayload.builder()
				.id(1L)		
				.dataCriacao(new Date())
				.informacao("Mock Informacao")
				.nome("Mock Nome")
				.nomeRazaoSocial("Mock Razao")
				.tipoPessoa(1)						
				.build());
	}

	@InjectMocks
	private ClienteService service = new ClienteService(Mockito.mock(RestTemplateBuilder.class));
	
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
	public void testFindAll() throws WebServiceException, BusinessException {		
		Mockito.when(this.restTemplate.exchange(URL, HttpMethod.GET, new HttpEntity<String>("body", headers), Object[].class))
			.thenReturn(new ResponseEntity<Object[]>(LIST_RESULT.toArray(), HttpStatus.OK));
		
		List<ClientePayload> result = this.service.findAll();
		assertEquals(result.size(), LIST_RESULT.size());
		assertArrayEquals(result.toArray(), LIST_RESULT.toArray());
	}

//	@Test
//	public void testFindBy() throws WebServiceException, BusinessException {
//		
//		BigInteger id = BigInteger.ONE;
//		
//		Mockito.when(this.restTemplate.exchange(URL + id, HttpMethod.GET, new HttpEntity<String>("body", headers), ClientePayload.class))
//			.thenReturn(new ResponseEntity<ClientePayload>(LIST_RESULT.stream().findFirst().get(), HttpStatus.OK));
//		
//		ClientePayload result = this.service.findBy(id);
//		result.
//	}

//	@Test
//	public void testInsert() {
//		fail("Not yet implemented");
//	}
//
//	@Test
//	public void testUpdate() {
//		fail("Not yet implemented");
//	}
//
//	@Test
//	public void testDelete() {
//		fail("Not yet implemented");
//	}

}
