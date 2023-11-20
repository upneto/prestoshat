/**
 * 
 */
package br.com.fiap.fmba.service;

import static org.mockito.Mockito.times;
import static org.mockito.Mockito.verify;

import java.util.ArrayList;
import java.util.List;
import java.util.Optional;

import org.junit.Assert;
import org.junit.jupiter.api.BeforeEach;
import org.junit.Test;
import org.junit.runner.RunWith;
import org.mockito.InjectMocks;
import org.mockito.Mock;
import org.mockito.Mockito;
import org.mockito.MockitoAnnotations;
import org.mockito.junit.MockitoJUnitRunner;

import br.com.fiap.fmba.controller.payload.ClientePayload;
import br.com.fiap.fmba.persistence.dao.ClienteRepository;
import br.com.fiap.fmba.persistence.model.Cliente;
import br.com.fiap.fmba.resources.exception.DaoException;

/**
 * @author Ulisses Neto
 *
 */
@RunWith(MockitoJUnitRunner.class)
public class TestClienteService {
	
	@Mock
	private ClienteRepository mockRepository;

	@InjectMocks
	private ClienteService service;

	/**
	 * @throws java.lang.Exception
	 */
	@BeforeEach
	public void setUp() throws Exception {
		MockitoAnnotations.openMocks(this);
	}
	
	public Cliente getMock() {
		return Cliente.builder()
				.id(123)
				.nome("NOME TESTE")
				.nomeRazaoSocial("NOME TESTE")
				.informacao("INFORMACAO")
				.build();
	}
	
	public ClientePayload getMockPayload() {
		return ClientePayload.builder()
				.id(123L)
				.nome("NOME TESTE")
				.nomeRazaoSocial("NOME TESTE")
				.informacao("INFORMACAO")
				.build();
	}

	/**
	 * Test method for {@link br.com.fiap.fmba.service.ClienteService#find(long)}.
	 * @throws DaoException 
	 */
	@Test
	public void testFind() throws DaoException {
		
		Mockito.when(mockRepository.findById(Mockito.anyLong())).thenReturn(Optional.of(getMock()));
		
		ClientePayload find = service.find(123);

		Assert.assertNotNull(find);
		Assert.assertEquals(getMock().getNome(), find.getNome());
		Assert.assertEquals(getMock().getNomeRazaoSocial(), find.getNomeRazaoSocial());
		Assert.assertEquals(getMock().getInformacao(), find.getInformacao());
	}

	/**
	 * Test method for {@link br.com.fiap.fmba.service.ClienteService#find(long)}.
	 * @throws DaoException 
	 */
	@Test
	public void testFindError() throws DaoException {
		
		Mockito.when(mockRepository.findById(Mockito.anyLong())).thenThrow(new RuntimeException());
		
		try {
			service.find(123);			
		} catch (Exception e) {
			Assert.assertTrue(e instanceof DaoException);
		}
	}

	
	/**
	 * Test method for {@link br.com.fiap.fmba.service.ClienteService#findAll()}.
	 * @throws DaoException 
	 */
	@Test
	public void testFindAll() throws DaoException {
		List<Cliente> lista = new ArrayList<Cliente>();
		lista.add(getMock());
		
		Mockito.when(mockRepository.findAll()).thenReturn(lista);
		
		List<ClientePayload> findAll = service.findAll();

		Assert.assertNotNull(findAll);
		Assert.assertEquals(lista.size(), findAll.size());
		Assert.assertEquals(lista.get(0).getNome(), findAll.get(0).getNome());
		Assert.assertEquals(lista.get(0).getNomeRazaoSocial(), findAll.get(0).getNomeRazaoSocial());
		Assert.assertEquals(lista.get(0).getInformacao(), findAll.get(0).getInformacao());
	}
	
	/**
	 * Test method for {@link br.com.fiap.fmba.service.ClienteService#findAll()}.
	 * @throws DaoException 
	 */
	@Test
	public void testFindAllError() {
		List<Cliente> lista = new ArrayList<Cliente>();
		lista.add(getMock());
		
		Mockito.when(mockRepository.findAll()).thenThrow(new RuntimeException());
		
		try {
			service.findAll();
		} catch (Exception e) {
			Assert.assertTrue(e instanceof DaoException);
		}		
	}

	/**
	 * Test method for {@link br.com.fiap.fmba.service.ClienteService#insert(br.com.fiap.fmba.persistence.model.Cliente)}.
	 * @throws DaoException 
	 */
	@Test
	public void testInsert() throws DaoException {		
		
		service.insert(getMockPayload());
		
		verify(mockRepository, times(1)).save(Mockito.any(Cliente.class));
	}

	/**
	 * Test method for {@link br.com.fiap.fmba.service.ClienteService#update(br.com.fiap.fmba.persistence.model.Cliente)}.
	 * @throws DaoException 
	 */
	@Test
	public void testUpdate() throws DaoException {
		
		service.update(getMockPayload());
		
		verify(mockRepository, times(1)).save(Mockito.any(Cliente.class));
	}

	/**
	 * Test method for {@link br.com.fiap.fmba.service.ClienteService#delete(long)}.
	 * @throws DaoException 
	 */
	@Test
	public void testDelete() throws DaoException {
		
		service.delete(1);
		
		verify(mockRepository, times(1)).deleteById(Mockito.anyLong());
	}

}
