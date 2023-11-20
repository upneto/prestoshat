package br.com.fiap.fmba.service;

import java.util.Optional;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.stereotype.Service;

import br.com.fiap.fmba.persistence.dao.UsuarioRepository;
import br.com.fiap.fmba.persistence.model.Usuario;
import br.com.fiap.fmba.resources.exception.DaoException;

/**
 * Servico de manipulação dos dados do usuário 
 * @author Ulisses Neto
 */
@Service
public class UsuarioService {

	@Autowired
	private UsuarioRepository repository;
	
	/**
	 * Find
	 * @param usuario
	 * @return
	 * @throws DaoException
	 */
	public Optional<Usuario> find(String usuario)  {		
		return this.repository.findById(usuario);
	}
	
	/**
	 * Find
	 * @param usuario
	 * @param passworld
	 * @return
	 * @throws DaoException
	 */
	public Usuario findByLogin(String usuario, String senha) throws DaoException {
		try {
			return this.repository.findByLogin(usuario, senha).get();						
		} catch (Exception e) {
			throw new DaoException(e.getMessage(), e);
		}
	}
	
	/**
	 * Find
	 * @param usuario
	 * @param passworld
	 * @return
	 * @throws DaoException
	 */
	public Usuario findByEmail(String usuario, String email) throws DaoException {
		try {
			return this.repository.findByEmail(usuario, email).get();						
		} catch (Exception e) {
			throw new DaoException(e.getMessage(), e);
		}
	}
	
	/**
	 * Insert
	 * @param cliente
	 * @throws DaoException
	 */
	public void insert(Usuario usuario) throws DaoException {
		try {
			this.repository.save(usuario);
		} catch (Exception e) {
			throw new DaoException(e.getMessage(), e);
		}
	}

	/**
	 * Update
	 * @param cliente
	 * @throws DaoException
	 */
	public void update(Usuario usuario) throws DaoException {
		try {
			this.repository.save(usuario);
		} catch (Exception e) {
			throw new DaoException(e.getMessage(), e);
		}
	}
}
