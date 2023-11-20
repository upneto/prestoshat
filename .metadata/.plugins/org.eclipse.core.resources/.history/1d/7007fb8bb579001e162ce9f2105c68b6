package br.com.fiap.fmba.controller.payload;

import java.util.Date;

import com.fasterxml.jackson.annotation.JsonFormat;

import lombok.AllArgsConstructor;
import lombok.Builder;
import lombok.Getter;
import lombok.NoArgsConstructor;
import lombok.Setter;


/**
 * The persistent class for the dt_contatos database table.
 * 
 */
@Getter
@Setter
@NoArgsConstructor
@AllArgsConstructor
@Builder
public class ContatoPayload {

	private Long id;
	@JsonFormat(pattern="yyyy-MM-dd HH:mm:ss")
	private Date dataCriacao;
	private String descricao;
	private int tipoContato;
	private Long cliente;

}