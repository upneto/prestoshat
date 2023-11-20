package br.com.fiap.fmba.controller.payload;

import java.util.ArrayList;
import java.util.Date;
import java.util.List;

import com.fasterxml.jackson.annotation.JsonFormat;

import br.com.fiap.fmba.persistence.model.Contato;
import br.com.fiap.fmba.persistence.model.Endereco;
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
public class ClientePayload {

	private Long id;
	@JsonFormat(pattern="yyyy-MM-dd HH:mm:ss")
	private Date dataCriacao;
	private String informacao;
	private String nome;
	private String nomeRazaoSocial;
	private int tipoPessoa;
	private List<ContatoPayload> contatos;
	private List<EnderecoPayload> enderecos;
	
	public void buildContatosPayload(List<Contato> contatos) {
		this.contatos = new ArrayList<ContatoPayload>();
		if(contatos != null) {
			for(Contato contato : contatos) {
				this.contatos.add(ContatoPayload.builder()
						.id(contato.getId())
						.cliente(contato.getCliente().getId())
						.dataCriacao(contato.getDataCriacao())
						.descricao(contato.getDescricao())
						.tipoContato(contato.getTipoContatoId())						
						.build());
			}
		}
	}
	
	public void buildEnderecosPayload(List<Endereco> enderecos) {
		this.enderecos = new ArrayList<EnderecoPayload>();
		if(enderecos != null) {
			for(Endereco endereco : enderecos) {
				this.enderecos.add(EnderecoPayload.builder()
						.id(endereco.getId())
						.rua(endereco.getRua())
						.numero(endereco.getNumero())
						.complemento(endereco.getComplemento())
						.bairro(endereco.getBairro())
						.cidade(endereco.getCidade())
						.estado(endereco.getEstado())
						.pais(endereco.getPais())
						.cep(endereco.getCep())
						.cliente(endereco.getCliente().getId())
						.dataCriacao(endereco.getDataCriacao())
						.build());
			}
		}
	}
}
