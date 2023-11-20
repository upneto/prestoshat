package br.com.fiap.fmba.persistence.model.constants;

import lombok.Getter;

@Getter
public enum TipoContato {

	TELEFONE(1, "TELEFONE"),
	EMAIL(2, "EMAIL"),
	WEB_SITE(3, "WEB SITE"),
	WHATS_APP(4, "WHATS APP");
	
	private int id;
	private String descricao;
	
	private TipoContato(int id, String descricao) {
		this.id = id;
		this.descricao = descricao;
	}
	
	public static TipoContato getBy(String descricao) {
		TipoContato tipo = null;
		for(TipoContato item : TipoContato.values()) {
			if(item.getDescricao().equalsIgnoreCase(descricao)) {
				tipo = item;
				break;
			}
		}
		return tipo;
	}
	
	public static TipoContato getBy(int id) {
		TipoContato tipo = null;
		for(TipoContato item : TipoContato.values()) {
			if(item.getId() == id) {
				tipo = item;
				break;
			}
		}
		return tipo;
	}
}
