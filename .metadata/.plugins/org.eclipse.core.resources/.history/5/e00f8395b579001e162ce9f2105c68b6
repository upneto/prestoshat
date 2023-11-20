package br.com.fiap.fmba.persistence.model;

import java.io.Serializable;
import java.util.Date;

import javax.persistence.Column;
import javax.persistence.Entity;
import javax.persistence.GeneratedValue;
import javax.persistence.GenerationType;
import javax.persistence.Id;
import javax.persistence.JoinColumn;
import javax.persistence.ManyToOne;
import javax.persistence.Table;
import javax.persistence.Temporal;
import javax.persistence.TemporalType;

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
@Entity
@Table(name="dt_enderecos")
public class Endereco implements Serializable {

	/**
	 * Serial
	 */
	private static final long serialVersionUID = -57769865239937585L;

	@Id
	@GeneratedValue(strategy=GenerationType.AUTO)
	private long id;

	private String bairro;

	private String cep;

	private String cidade;

	private String complemento;

	@Column(name="data_criacao")
	@Temporal(TemporalType.TIMESTAMP)
	private Date dataCriacao;

	private String estado;

	private String numero;

	private String pais;

	private String rua;

	@ManyToOne
	@JoinColumn(name="cliente_endereco_id")
	private Cliente cliente;

}