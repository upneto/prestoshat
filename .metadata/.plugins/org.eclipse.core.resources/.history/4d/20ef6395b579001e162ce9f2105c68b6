/**
 * 
 */
package br.com.fiap.fmba.controller;

import java.util.ArrayList;
import java.util.List;

import org.junit.Assert;
import org.junit.Test;
import org.junit.jupiter.api.BeforeEach;
import org.junit.runner.RunWith;
import org.mockito.InjectMocks;
import org.mockito.Mock;
import org.mockito.Mockito;
import org.mockito.MockitoAnnotations;
import org.mockito.junit.MockitoJUnitRunner;
import org.springframework.http.ResponseEntity;

import br.com.fiap.fmba.controller.api.ClienteController;
import br.com.fiap.fmba.controller.payload.ClientePayload;
import br.com.fiap.fmba.resources.exception.DaoException;
import br.com.fiap.fmba.service.ClienteService;

/**
 * @author Ulisses Neto
 *
 */
@RunWith(MockitoJUnitRunner.class)
public class TestClienteController {

	@Mock
	private ClienteService mockService;

	@InjectMocks
	private ClienteController controller;

	/**
	 * @throws java.lang.Exception
	 */
	@BeforeEach
	public void setUpBefore() throws Exception {
		MockitoAnnotations.openMocks(this);
	}
	
	public ClientePayload getMock() {
		return ClientePayload.builder()
				.id(123L)
				.nome("NOME TESTE")
				.nomeRazaoSocial("NOME TESTE")
				.informacao("INFORMACAO")
				.build();
	}

	/**
	 * Test method for
	 * {@link br.com.fiap.fmba.controller.api.ClienteController#findAll()}.
	 * @throws DaoException 
	 */
	@Test
	public void testFindAll() throws DaoException {
		
		List<ClientePayload> lista = new ArrayList<ClientePayload>();
		lista.add(getMock());
		
		Mockito.when(mockService.findAll()).thenReturn(lista);
		
		ResponseEntity<List<ClientePayload>> findAll = controller.findAll();

		Assert.assertNotNull(findAll);
        Assert.assertEquals(200, findAll.getStatusCode().value());
        Assert.assertEquals(lista.get(0).getId(), findAll.getBody().get(0).getId());
	}

	/**
	 * Test method for
	 * {@link br.com.fiap.fmba.controller.api.ClienteController#findBy(long)}.
	 * @throws DaoException 
	 */
	@Test
	public void testFindBy() throws DaoException {
		
		Mockito.when(mockService.find(Mockito.anyLong())).thenReturn(getMock());
		
		ResponseEntity<ClientePayload> findBy = controller.findBy(123);

		Assert.assertNotNull(findBy);
        Assert.assertEquals(200, findBy.getStatusCode().value());
        Assert.assertEquals(getMock().getId(), findBy.getBody().getId());
	}

	/**
	 * Test method for
	 * {@link br.com.fiap.fmba.controller.api.ClienteController#insert(br.com.fiap.fmba.persistence.model.Cliente)}.
	 * @throws DaoException 
	 */
	@Test
	public void testInsert() throws DaoException {
				
		ResponseEntity<?> insert = controller.insert(getMock());

		Assert.assertNotNull(insert);
        Assert.assertEquals(200, insert.getStatusCode().value());
	}

	/**
	 * Test method for
	 * {@link br.com.fiap.fmba.controller.api.ClienteController#update(br.com.fiap.fmba.persistence.model.Cliente)}.
	 * @throws DaoException 
	 */
	@Test
	public void testUpdate() throws DaoException {
		ResponseEntity<?> update = controller.update(getMock());

		Assert.assertNotNull(update);
        Assert.assertEquals(200, update.getStatusCode().value());
	}

	/**
	 * Test method for
	 * {@link br.com.fiap.fmba.controller.api.ClienteController#delete(long)}.
	 * @throws DaoException 
	 */
	@Test
	public void testDelete() throws DaoException {
		ResponseEntity<?> delete = controller.delete(123);

		Assert.assertNotNull(delete);
        Assert.assertEquals(200, delete.getStatusCode().value());
	}

}
