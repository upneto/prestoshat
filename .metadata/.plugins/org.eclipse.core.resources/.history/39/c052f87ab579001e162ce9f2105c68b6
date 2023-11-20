package br.com.fiap.fmba.usecase;

import java.util.Date;
import java.util.Optional;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import br.com.fiap.fmba.controller.payload.UsuarioRequest;
import br.com.fiap.fmba.persistence.model.Usuario;
import br.com.fiap.fmba.persistence.model.constants.Status;
import br.com.fiap.fmba.resources.exception.BusinessException;
import br.com.fiap.fmba.resources.exception.DaoException;
import br.com.fiap.fmba.service.UsuarioService;

@Service
public class Access {

	@Autowired
	private UsuarioService service;
	
	/**
	 * 
	 * @param request
	 * @throws DaoException
	 * @throws BusinessException 
	 */
	public void doCreateAccess(UsuarioRequest request) throws DaoException, BusinessException {
		Optional<Usuario> user = this.service.find(request.getUsuario());
		if(user.isPresent() && user.get().getUsuario().equalsIgnoreCase(request.getUsuario())) {
			throw new BusinessException("Usuário já possui conta de acesso nessa aplicação!");
		}
		this.service.insert(Usuario.builder()
			.usuario(request.getUsuario())
			.nome(request.getNome())
			.senha(request.getSenha())
			.email(request.getEmail())
			.errorCount(0)
			.status(Status.ATIVO.ordinal())
			.dataCriacao(new Date())
			.build());
	}
}
