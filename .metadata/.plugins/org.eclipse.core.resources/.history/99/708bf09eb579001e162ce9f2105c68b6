package br.com.fiap.fmba.controller;

import static org.junit.Assert.assertArrayEquals;
import static org.junit.jupiter.api.Assertions.assertEquals;

import java.math.BigInteger;
import java.text.SimpleDateFormat;
import java.util.ArrayList;
import java.util.Date;
import java.util.List;

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

import br.com.fiap.fmba.controller.api.OrdemServicoController;
import br.com.fiap.fmba.controller.payload.ordemservico.OrdemServicoRequest;
import br.com.fiap.fmba.controller.payload.ordemservico.OrdemServicoResponse;
import br.com.fiap.fmba.resources.exception.AutenticatorException;
import br.com.fiap.fmba.resources.exception.BusinessException;
import br.com.fiap.fmba.resources.exception.WebServiceException;
import br.com.fiap.fmba.service.OrdemServicoService;

@RunWith(SpringRunner.class)
public class OrdemServicoControllerTest {
	
	static final List<OrdemServicoResponse> LIST_PAYLOAD = new ArrayList<>();
	static {
		LIST_PAYLOAD.add(OrdemServicoResponse.builder()				
				.codigo(1L)
		 		.dataInicio((new SimpleDateFormat()).format(new Date()))
		 		.dataFinal((new SimpleDateFormat()).format(new Date()))
		 		.nomeCliente("Mock Cliente")
		 		.veiculo("Mock Veiculo")
		 		.placa("XPT1234")
				.build());
	}
	
	static final OrdemServicoRequest REQUEST = OrdemServicoRequest.builder()
			.id(1L)
			.cliente(new BigInteger("1"))
			.dataCriacao(new Date())
			.dataFinal(new Date())
			.status(1)				
			.build();
	
	@TestConfiguration
    static class OrdemServicoControllerTestConfiguration {        
		
		@Bean
        public OrdemServicoController ordemServicoController() {
            return new OrdemServicoController();
        }
    }
	
	@Autowired
	private OrdemServicoController controller;
	
	@MockBean
	private OrdemServicoService service;

	@Before
	public void setUp() throws Exception {
		Mockito.when(service.findAll()).thenReturn(LIST_PAYLOAD);
		Mockito.when(service.find(Mockito.anyLong())).thenReturn(LIST_PAYLOAD.get(0));	
		Mockito.doNothing().when(service).insert(Mockito.any(OrdemServicoRequest.class));
		Mockito.doNothing().when(service).update(Mockito.any(OrdemServicoRequest.class));
		Mockito.doNothing().when(service).delete(Mockito.anyLong());
	}

	@Test
	public void testFindAll() throws WebServiceException, BusinessException, AutenticatorException {
		ResponseEntity<List<OrdemServicoResponse>> result = this.controller.findAll();
		assertEquals(result.getStatusCode(), HttpStatus.OK);
		assertEquals(result.getBody().size(), LIST_PAYLOAD.size());
		assertArrayEquals(result.getBody().toArray(), LIST_PAYLOAD.toArray());
	}

	@Test
	public void testFindBy() throws WebServiceException, BusinessException, AutenticatorException {
		ResponseEntity<OrdemServicoResponse> result = this.controller.findBy(1L);
		assertEquals(result.getStatusCode(), HttpStatus.OK);
		assertEquals(result.getBody(), LIST_PAYLOAD.get(0));
	}

	@Test
	public void testInsert() throws WebServiceException, BusinessException, AutenticatorException {				
		ResponseEntity<?> result = this.controller.insert(REQUEST);
		Mockito.verify(service, Mockito.times(1)).insert(REQUEST);
		assertEquals(result.getStatusCode(), HttpStatus.OK);
	}

	@Test
	public void testUpdate() throws WebServiceException, BusinessException, AutenticatorException {
		ResponseEntity<?> result = this.controller.update(REQUEST);
		Mockito.verify(service, Mockito.times(1)).update(REQUEST);
		assertEquals(result.getStatusCode(), HttpStatus.OK);
	}

	@Test
	public void testDelete() throws WebServiceException, BusinessException, AutenticatorException {
		ResponseEntity<?> result = this.controller.delete(1L);
		Mockito.verify(service, Mockito.times(1)).delete(1l);
		assertEquals(result.getStatusCode(), HttpStatus.OK);
	}

}
