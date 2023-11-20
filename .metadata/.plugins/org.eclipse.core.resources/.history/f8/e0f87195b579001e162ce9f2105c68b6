package br.com.fiap.fmba.controller.payload;

import java.util.Date;

import com.fasterxml.jackson.annotation.JsonFormat;

import lombok.AllArgsConstructor;
import lombok.Builder;
import lombok.Getter;
import lombok.NoArgsConstructor;
import lombok.Setter;


/**
 * The persistent class for the dt_enderecos database table.
 * 
 */
@Getter
@Setter
@NoArgsConstructor
@AllArgsConstructor
@Builder
public class EnderecoPayload {

	private Long id;
	private String bairro;
	private String cep;
	private String cidade;
	private String complemento;
	@JsonFormat(pattern="yyyy-MM-dd HH:mm:ss")
	private Date dataCriacao;
	private String estado;
	private String numero;
	private String pais;
	private String rua;
	private Long cliente;

}