package br.com.fiap.fmba.usecase;

import java.util.Date;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import br.com.fiap.fmba.controller.payload.RescueRequest;
import br.com.fiap.fmba.persistence.model.Usuario;
import br.com.fiap.fmba.persistence.model.constants.Status;
import br.com.fiap.fmba.resources.exception.BusinessException;
import br.com.fiap.fmba.resources.exception.DaoException;
import br.com.fiap.fmba.service.UsuarioService;

@Service
public class Rescue {
	
	@Autowired
	private UsuarioService service;

	/**
	 * 
	 * @param usuario
	 * @throws DaoException
	 * @throws BusinessException 
	 */
	public void doUpdateStatusToActive(RescueRequest usuario) throws DaoException, BusinessException {
		Usuario user = this.service.findByEmail(usuario.getUsuario(), usuario.getEmail());
		if(user == null) {
			throw new BusinessException("Usuário não possui conta nessa aplicação!");
		}
		user.setStatus(Status.ATIVO.ordinal());
		user.setDataAlteracao(new Date());
		user.setErrorCount(0);
		this.service.update(user);
	}
}
