package br.com.fiap.fmba.persistence.model.constants;

import lombok.Getter;

@Getter
public enum TipoPessoa {
	
	FISICA(1, "FISICA"),
	JURIDICA(2, "JURIDICA");

	private int id;
	private String descricao;
	
	private TipoPessoa(int id, String descricao) {
		this.id = id;
		this.descricao = descricao;
	}
	
	public static TipoPessoa getBy(String descricao) {
		TipoPessoa tipo = null;
		for(TipoPessoa item : TipoPessoa.values()) {
			if(item.getDescricao().equalsIgnoreCase(descricao)) {
				tipo = item;
				break;
			}
		}
		return tipo;
	}
	
	public static TipoPessoa getBy(int id) {
		TipoPessoa tipo = null;
		for(TipoPessoa item : TipoPessoa.values()) {
			if(item.getId() == id) {
				tipo = item;
				break;
			}
		}
		return tipo;
	}
}
