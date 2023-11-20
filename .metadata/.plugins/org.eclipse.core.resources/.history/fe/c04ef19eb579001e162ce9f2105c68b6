package br.com.fiap.fmba.service;

import java.math.BigInteger;
import java.util.ArrayList;
import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.boot.web.client.RestTemplateBuilder;
import org.springframework.stereotype.Service;

import br.com.fiap.fmba.controller.payload.ordemservico.OrdemServicoRequest;
import br.com.fiap.fmba.controller.payload.ordemservico.OrdemServicoResponse;
import br.com.fiap.fmba.resources.exception.BusinessException;
import br.com.fiap.fmba.resources.exception.WebServiceException;
import br.com.fiap.fmba.service.payload.ClientePayload;
import br.com.fiap.fmba.service.payload.OrdemServicoPayload;
import br.com.fiap.fmba.service.payload.VeiculoPayload;

@Service
public class OrdemServicoService extends AbstractService {

	@Autowired
	public OrdemServicoService(RestTemplateBuilder builder) {
	    super(builder);
	}
	
	/**
	 * Variavel injetada pelo contexto Spring
	 * 		'env' = variavel injetada da runtime jvm
	 * 		'.url.backend.ordem_servico' = arquivo application.properties  
	 */
	@Value("${${env}.url.backend.ordem_servico}") 
	private String url = null;
	
	@Autowired
	private VeiculoService veiculoService = null;
	
	@Autowired
	private ClienteService clienteService = null;
	
	@Autowired
	private FilaOrdemServicoService filaOrdemServicoService = null;

	/**
	 * Find
	 * @param id
	 * @return
	 * @throws WebServiceException
	 * @throws BusinessException
	 */
	@SuppressWarnings("unchecked")
	public OrdemServicoResponse find(long id) throws WebServiceException, BusinessException {
		try {
			OrdemServicoPayload payload = super.doGet(this.url + id, OrdemServicoPayload.class);	
			
			VeiculoPayload veiculo = this.getVeiculo(payload.getVeiculo(), false);
			ClientePayload cliente = this.getCliente(payload.getCliente(), false);
			
			return OrdemServicoResponse.builder()
					.codigo(payload.getId())
					.dataInicio(payload.getDataInicioFormat())
					.dataFinal(payload.getDataFinalFormat())
					.idCliente(cliente.getId())
					.nomeCliente(cliente.getNome())
					.idVeiculo(veiculo.getId())
					.veiculo(veiculo.getMarca() + " " + veiculo.getModelo())
					.placa(veiculo.getPlaca())
					.descricaoServico(payload.getDescricao())
					.build();
		}catch (Exception e) {
			throw new WebServiceException(e.getMessage(), e);
		}		
	}

	/**
	 * Find All
	 * @return
	 * @throws WebServiceException
	 * @throws BusinessException
	 */
	@SuppressWarnings("unchecked")
	public List<OrdemServicoResponse> findAll() throws WebServiceException, BusinessException {
		List<OrdemServicoResponse> response = new ArrayList<>();
		try {
			List<OrdemServicoPayload> listaPayload = super.doGetList(this.url, OrdemServicoPayload.class);
			for(OrdemServicoPayload payload : listaPayload) {
				
				VeiculoPayload veiculo = this.getVeiculo(payload.getVeiculo(), false);
				ClientePayload cliente = this.getCliente(payload.getCliente(), false);
				
				response.add(OrdemServicoResponse.builder()
						.codigo(payload.getId())
						.dataInicio(payload.getDataInicioFormat())
						.dataFinal(payload.getDataFinalFormat())
						.idCliente(cliente.getId())
						.nomeCliente(cliente.getNome())
						.veiculo(veiculo.getMarca() + " " + veiculo.getModelo())
						.idVeiculo(veiculo.getId())
						.placa(veiculo.getPlaca())
						.descricaoServico(payload.getDescricao())
						.build());
			}			
		}
		catch (Exception e) {
			throw new WebServiceException(e.getMessage(), e);
		}		
		return response;
	}

	/**
	 * Insert
	 * @param ordemServico
	 * @throws WebServiceException
	 * @throws BusinessException
	 */
	public void insert(OrdemServicoRequest ordemServico) throws WebServiceException, BusinessException {
		try {
			// TODO super.doPost(this.url, OrdemServicoPayload.class, ordemServico);
		}
		catch (Exception e) {
			throw new WebServiceException(e.getMessage(), e);
		}
		try {
			// Envia para fila de envio de emails!
			this.filaOrdemServicoService.send(ordemServico);
		}
		catch (Exception e) {
			LOGGER.error("Não foi possível enviar a mensagem!", e);
		}
	}

	/**
	 * Update
	 * @param ordemServico
	 * @throws WebServiceException
	 * @throws BusinessException
	 */
	public void update(OrdemServicoRequest ordemServico) throws WebServiceException, BusinessException {
		try {
			super.doPut(this.url, ordemServico);
		}
		catch (Exception e) {
			throw new WebServiceException(e.getMessage(), e);
		}
		
		try {
			// Envia para fila de envio de emails!
			this.filaOrdemServicoService.send(ordemServico);
		}
		catch (Exception e) {
			LOGGER.error("Não foi possível enviar a mensagem!", e);
		}
	}

	/**
	 * Delete
	 * @param id
	 * @throws WebServiceException
	 * @throws BusinessException
	 */
	public void delete(long id) throws WebServiceException, BusinessException {
		try {
			super.doDelete(this.url + id);
		}catch (Exception e) {
			throw new WebServiceException(e.getMessage(), e);
		}
	}
	
	// ***** Metodos auxiliares ****
	
	private VeiculoPayload getVeiculo(BigInteger id, boolean trataErro) throws WebServiceException, BusinessException {
		VeiculoPayload response = new VeiculoPayload();
		try {			
			response = this.veiculoService.findBy(id);
		}
		catch (WebServiceException | BusinessException e) {
			LOGGER.error(e.getMessage(), e);
			if(trataErro) {
				throw e;
			}
		}
		return response;
	}
	
	private ClientePayload getCliente(BigInteger id, boolean trataErro) throws WebServiceException, BusinessException {
		ClientePayload response = new ClientePayload();
		try {			
			response = this.clienteService.findBy(id);
		}
		catch (WebServiceException | BusinessException e) {
			LOGGER.error(e.getMessage(), e);
			if(trataErro) {
				throw e;
			}
		}
		return response;
	}
}
