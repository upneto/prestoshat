package br.com.fiap.fmba.service;

import java.math.BigInteger;
import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.boot.web.client.RestTemplateBuilder;
import org.springframework.stereotype.Service;

import br.com.fiap.fmba.resources.exception.BusinessException;
import br.com.fiap.fmba.resources.exception.WebServiceException;
import br.com.fiap.fmba.service.payload.VeiculoPayload;

@Service
public class VeiculoService extends AbstractService {
	
	@Autowired
	public VeiculoService(RestTemplateBuilder builder) {
	    super(builder);
	}

	/**
	 * Variavel injetada pelo contexto Spring
	 * 		'env' = variavel injetada da runtime jvm
	 * 		'.url.backend.ordem_servico' = arquivo application.properties  
	 */
	@Value("${${env}.url.backend.veiculo}")
	private String url = null;

	/**
	 * 
	 * @return
	 * @throws WebServiceException
	 * @throws BusinessException
	 */
	@SuppressWarnings("unchecked")
	public List<VeiculoPayload> findAll() throws WebServiceException, BusinessException {
		return super.doGetList(url, VeiculoPayload.class);
	}
	
	/**
	 * 
	 * @param id
	 * @return
	 * @throws WebServiceException
	 * @throws BusinessException
	 */
	@SuppressWarnings("unchecked")
	public VeiculoPayload findBy(BigInteger id) throws WebServiceException, BusinessException {
		return super.doGet(url + id, VeiculoPayload.class);
	}
	
	/**
	 * 
	 * @param veiculo
	 * @throws WebServiceException
	 * @throws BusinessException
	 */
	public void insert(VeiculoPayload veiculo) throws WebServiceException, BusinessException {
		super.doPost(url, veiculo);
	}
	
	/**
	 * 
	 * @param veiculo
	 * @throws WebServiceException
	 * @throws BusinessException
	 */
	public void update(VeiculoPayload veiculo) throws WebServiceException, BusinessException {
		super.doPut(url, veiculo);
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
