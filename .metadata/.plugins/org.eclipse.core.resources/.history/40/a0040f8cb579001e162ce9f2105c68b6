package br.com.fiap.fmba.persistence.model.constants;

import lombok.Getter;

@Getter
public enum TipoStatus {

	A_INICIAR(1, "A INICIAR"),
	INICIADO(2, "INICIADO"),
	FINALIZADO(3, "FINALIZADO");
	
	private int id;
	private String descricao;
	
	private TipoStatus(int id, String descricao) {
		this.id = id;
		this.descricao = descricao;
	}
	
	public static TipoStatus getBy(String descricao) {
		TipoStatus tipo = null;
		for(TipoStatus item : TipoStatus.values()) {
			if(item.getDescricao().equalsIgnoreCase(descricao)) {
				tipo = item;
				break;
			}
		}
		return tipo;
	}
	
	public static TipoStatus getBy(int id) {
		TipoStatus tipo = null;
		for(TipoStatus item : TipoStatus.values()) {
			if(item.getId() == id) {
				tipo = item;
				break;
			}
		}
		return tipo;
	}
}
