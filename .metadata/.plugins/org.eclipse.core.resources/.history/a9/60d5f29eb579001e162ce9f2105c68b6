package br.com.fiap.fmba.controller;

import static org.junit.Assert.assertArrayEquals;
import static org.junit.jupiter.api.Assertions.assertEquals;

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

import br.com.fiap.fmba.controller.api.VeiculoController;
import br.com.fiap.fmba.resources.exception.AutenticatorException;
import br.com.fiap.fmba.resources.exception.BusinessException;
import br.com.fiap.fmba.resources.exception.WebServiceException;
import br.com.fiap.fmba.service.VeiculoService;
import br.com.fiap.fmba.service.payload.VeiculoPayload;

@RunWith(SpringRunner.class)
public class VeiculoControllerTest {
	
	static final List<VeiculoPayload> LIST_PAYLOAD = new ArrayList<>();
	static {
		LIST_PAYLOAD.add(VeiculoPayload.builder()
				.id(1L)		
				.dataCriacao(new Date())
				.informacao("Mock Informacao")
				.marca("Mock MARCA")
				.modelo("Mock MODELO")
				.placa("XPT1234")
				.build());
	}
	
	@TestConfiguration
    static class VeiculoControllerTestConfiguration {        
		
		@Bean
        public VeiculoController veiculoController() {
            return new VeiculoController();
        }
    }
	
	@Autowired
	private VeiculoController controller;
	
	@MockBean
	private VeiculoService service;
	
	@Before
	public void setUp() throws WebServiceException, BusinessException {
	    Mockito.when(service.findAll()).thenReturn(LIST_PAYLOAD);
	}
	
	@Test
	public void testFindAll() throws WebServiceException, BusinessException, AutenticatorException {
		ResponseEntity<List<VeiculoPayload>> result = this.controller.findAll();
		assertEquals(result.getStatusCode(), HttpStatus.OK);
		assertEquals(result.getBody().size(), LIST_PAYLOAD.size());
		assertArrayEquals(result.getBody().toArray(), LIST_PAYLOAD.toArray());
	}

}
