package br.com.fiap.fmba.service;

import java.math.BigInteger;
import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.boot.web.client.RestTemplateBuilder;
import org.springframework.stereotype.Service;

import br.com.fiap.fmba.resources.exception.BusinessException;
import br.com.fiap.fmba.resources.exception.WebServiceException;
import br.com.fiap.fmba.service.payload.ClientePayload;

@Service
public class ClienteService extends AbstractService {
	
	@Autowired
	public ClienteService(RestTemplateBuilder builder) {
	    super(builder);
	}
	
	/**
	 * Variavel injetada pelo contexto Spring
	 * 		'env' = variavel injetada da runtime jvm
	 * 		'.url.backend.ordem_servico' = arquivo application.properties  
	 */
	@Value("${${env}.url.backend.cliente}")
	private String url = null;
	
	/**
	 * 
	 * @return
	 * @throws WebServiceException
	 * @throws BusinessException
	 */
	@SuppressWarnings("unchecked")
	public List<ClientePayload> findAll() throws WebServiceException, BusinessException {
		return super.doGetList(url, ClientePayload.class);
	}
	
	/**
	 * 
	 * @param id
	 * @return
	 * @throws WebServiceException
	 * @throws BusinessException
	 */
	@SuppressWarnings("unchecked")
	public ClientePayload findBy(BigInteger id) throws WebServiceException, BusinessException {
		return super.doGet(url + id, ClientePayload.class);
	}
	
	/**
	 * 
	 * @param cliente
	 * @throws WebServiceException
	 * @throws BusinessException
	 */
	public void insert(ClientePayload cliente) throws WebServiceException, BusinessException {
		super.doPost(url, cliente);
	}
	
	/**
	 * 
	 * @param cliente
	 * @throws WebServiceException
	 * @throws BusinessException
	 */
	public void update(ClientePayload cliente) throws WebServiceException, BusinessException {
		super.doPut(url, cliente);
	}
	
	/**
	 * 
	 * @param id
	 * @throws WebServiceException
	 * @throws BusinessException
	 */
	public void delete(BigInteger id) throws WebServiceException, BusinessException {
		super.doDelete(url + id);
	}
}
