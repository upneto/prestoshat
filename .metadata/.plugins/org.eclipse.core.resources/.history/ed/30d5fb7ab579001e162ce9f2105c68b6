package br.com.fiap.fmba.usecase;

import java.util.Date;
import java.util.Optional;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import br.com.fiap.fmba.controller.payload.LoginRequest;
import br.com.fiap.fmba.controller.payload.LoginResponse;
import br.com.fiap.fmba.controller.payload.TokenRequest;
import br.com.fiap.fmba.persistence.model.Usuario;
import br.com.fiap.fmba.persistence.model.constants.Status;
import br.com.fiap.fmba.resources.exception.BusinessException;
import br.com.fiap.fmba.resources.exception.DaoException;
import br.com.fiap.fmba.resources.exception.LoginException;
import br.com.fiap.fmba.service.UsuarioService;
import br.com.fiap.fmba.usecase.security.TokenBuilder;

@Service
public class Login {

	@Autowired
	private UsuarioService service;
	
	/**
	 * Login
	 * @param request
	 * @return
	 * @throws DaoException
	 * @throws BusinessException
	 */
	public LoginResponse doLogin(LoginRequest request) throws DaoException, LoginException {		
		Usuario usuario = this.service.findByLogin(request.getUsuario(), request.getSenha());
		if(usuario == null) {	
			this.updateLoginErrorCount(request.getUsuario());
			throw new LoginException("Usuário e(ou) Senha inválidos!");
		}
		else if (usuario.convertStatusToEnum().equals(Status.BLOQUEADO)) {
			throw new LoginException("Usuário Bloqueado!");
		}
		else if (usuario.convertStatusToEnum().equals(Status.INATIVO)) {			
			throw new LoginException("Usuário não possui permissão para acessar o sistema!");
		}
		return LoginResponse.builder()
				.usuario(usuario.getUsuario())
				.nome(usuario.getNome())
				.token(TokenBuilder.getInstance().getToken(usuario.getUsuario())) 
				.build();
	}
	
	/**
	 * Login
	 * @param request
	 * @return
	 * @throws DaoException
	 * @throws BusinessException
	 */
	public void doVerify(TokenRequest request) throws LoginException {		
		TokenBuilder.getInstance().validateToken(request.getToken());
	}
	
	/**
	 * 
	 * @param usuario
	 * @throws DaoException
	 */
	private void updateLoginErrorCount(String usuario) throws DaoException {
		Optional<Usuario> user = this.service.find(usuario);
		if(user.isPresent()) {
			return;
		}	
		Usuario usuarioUp = user.get();
		int errorCount = usuarioUp.getErrorCount();
		if(errorCount < 3) {
			usuarioUp.setErrorCount(errorCount + 1);
		} 
		else {
			usuarioUp.setStatus(Status.BLOQUEADO.ordinal());
		}
		usuarioUp.setDataAlteracao(new Date());
		this.service.update(usuarioUp);
	}	
}
