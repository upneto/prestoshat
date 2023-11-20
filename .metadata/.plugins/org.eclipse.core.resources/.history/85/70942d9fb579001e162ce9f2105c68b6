package br.com.fiap.fmba.service.payload;

import java.util.Date;

import com.fasterxml.jackson.annotation.JsonFormat;

import lombok.AllArgsConstructor;
import lombok.Builder;
import lombok.Getter;
import lombok.NoArgsConstructor;
import lombok.Setter;

@Getter
@Setter
@NoArgsConstructor
@AllArgsConstructor
@Builder
public class OrdemServicoMessage {

	@JsonFormat(pattern="yyyy-MM-dd HH:mm:ss")
	private Date dataEnvio;	
	private String nomeDestinatario;
	private String emailDestinatario;
	
	private long codigoServico;
	@JsonFormat(pattern="yyyy-MM-dd HH:mm:ss")
	private Date dataInicioServico;	
	@JsonFormat(pattern="yyyy-MM-dd HH:mm:ss")
	private Date dataFinalServico;
	private String descricaoServico;
	
	private String modeloVeiculo;
	private String marcaVeiculo;
	private String placaVeiculo;
	
}
