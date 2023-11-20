package br.com.fiap.fmba.service;

import java.util.Date;
import java.util.Optional;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.boot.web.client.RestTemplateBuilder;
import org.springframework.stereotype.Service;

import br.com.fiap.fmba.controller.payload.ordemservico.OrdemServicoRequest;
import br.com.fiap.fmba.resources.exception.BusinessException;
import br.com.fiap.fmba.resources.exception.WebServiceException;
import br.com.fiap.fmba.service.payload.ClientePayload;
import br.com.fiap.fmba.service.payload.ContatoPayload;
import br.com.fiap.fmba.service.payload.OrdemServicoMessage;
import br.com.fiap.fmba.service.payload.VeiculoPayload;

@Service
public class FilaOrdemServicoService extends AbstractService {
	
	@Autowired
	private ClienteService clienteService = null;
	
	@Autowired
	private VeiculoService veiculoService = null;

	@Autowired
	public FilaOrdemServicoService(RestTemplateBuilder builder) {
	    super(builder);
	}
	
	/**
	 * Variavel injetada pelo contexto Spring
	 * 		'env' = variavel injetada da runtime jvm
	 * 		'.url.backend.ordem_servico' = arquivo application.properties  
	 */
	@Value("${${env}.url.backend.fila_ordem_servico}") 
	private String url = null;
	
	/**
	 * Insert
	 * @param ordemServico
	 * @throws WebServiceException
	 * @throws BusinessException
	 */
	public void send(OrdemServicoRequest ordemServico) throws WebServiceException, BusinessException {
		try {
			super.doPost(this.url + "api/ordem_servico", OrdemServicoMessage.class, this.buildMessageObj(ordemServico));
		}catch (Exception e) {
			throw new WebServiceException(e.getMessage(), e);
		}		
	}
	
	/**
	 * Cria objeto para mensagem da fila
	 * @param ordemServico
	 * @return
	 * @throws WebServiceException
	 * @throws BusinessException
	 */
	private OrdemServicoMessage buildMessageObj(OrdemServicoRequest ordemServico) throws WebServiceException, BusinessException {
		VeiculoPayload veiculo = this.veiculoService.findBy(ordemServico.getVeiculo());
		ClientePayload cliente = this.clienteService.findBy(ordemServico.getCliente());		
		Optional<ContatoPayload> contato = cliente.getContatos()
				.stream()
				.filter(obj -> obj.getTipoContato() == 2 /* Tipo: Email */)
				.findFirst();
		
		return OrdemServicoMessage.builder()
				.dataEnvio(new Date())
				.nomeDestinatario(cliente.getNome())
				.emailDestinatario(contato.get().getDescricao())
				.codigoServico(ordemServico.getId())				
				.dataInicioServico(ordemServico.getDataInicio())	
				.dataFinalServico(ordemServico.getDataFinal())
				.descricaoServico(ordemServico.getDescricaoServico())
				.modeloVeiculo(veiculo.getModelo())
				.marcaVeiculo(veiculo.getMarca())
				.placaVeiculo(veiculo.getPlaca())
				.build();
	}
}
