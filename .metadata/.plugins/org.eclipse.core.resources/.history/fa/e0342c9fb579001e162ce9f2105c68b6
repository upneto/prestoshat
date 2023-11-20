package br.com.fiap.fmba.service.payload;

import java.math.BigInteger;
import java.text.SimpleDateFormat;
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
public class OrdemServicoPayload {
	
	private static final SimpleDateFormat SDF = new SimpleDateFormat("dd/MM/yyyy");
	
	private long id;	
	@JsonFormat(pattern="yyyy-MM-dd HH:mm:ss")
	private Date dataCriacao;	
	@JsonFormat(pattern="yyyy-MM-dd HH:mm:ss")
	private Date dataFinal;	
	@JsonFormat(pattern="yyyy-MM-dd HH:mm:ss")
	private Date dataInicio;	
	private int status;	
	private BigInteger veiculo;
	private BigInteger cliente;
	private String descricao;
	
	// Metodos auxiliares
	
	public String getDataInicioFormat() {
		if(dataInicio == null) {
			return "";
		}
		return SDF.format(dataInicio);
	}
	
	public String getDataFinalFormat() {
		if(dataFinal == null) {
			return "";
		}
		return SDF.format(dataFinal);
	}
}
