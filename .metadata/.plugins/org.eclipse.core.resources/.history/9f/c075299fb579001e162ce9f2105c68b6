package br.com.fiap.fmba.service.payload;

import java.util.Date;
import java.util.List;

import com.fasterxml.jackson.annotation.JsonFormat;

import lombok.AllArgsConstructor;
import lombok.Builder;
import lombok.EqualsAndHashCode;
import lombok.Getter;
import lombok.NoArgsConstructor;
import lombok.Setter;

@Getter
@Setter
@NoArgsConstructor
@AllArgsConstructor
@Builder
@EqualsAndHashCode
public class ClientePayload {

	@EqualsAndHashCode.Exclude
	private Long id;
	
	@EqualsAndHashCode.Exclude
	@JsonFormat(pattern="yyyy-MM-dd HH:mm:ss")
	private Date dataCriacao;
	
	@EqualsAndHashCode.Exclude
	private String informacao;
	
	private String nome;
	
	@EqualsAndHashCode.Exclude
	private String nomeRazaoSocial;
	
	@EqualsAndHashCode.Exclude
	private int tipoPessoa;
	
	@EqualsAndHashCode.Exclude
	private List<ContatoPayload> contatos;
	
	@EqualsAndHashCode.Exclude
	private List<EnderecoPayload> enderecos;
}
