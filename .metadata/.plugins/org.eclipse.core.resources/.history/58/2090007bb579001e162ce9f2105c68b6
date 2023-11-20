package br.com.fiap.fmba.persistence.dao;

import java.util.Optional;

import org.springframework.data.jpa.repository.JpaRepository;
import org.springframework.data.jpa.repository.Query;

import br.com.fiap.fmba.persistence.model.Usuario;

/**
 * Repositorio Usuario
 * @author Ulisses Neto
 *
 */
public interface UsuarioRepository extends JpaRepository<Usuario, String> {

	@Query("SELECT u FROM Usuario u WHERE u.usuario = ?1 AND u.senha = ?2")
	Optional<Usuario> findByLogin(String usuario, String senha);
	
	@Query("SELECT u FROM Usuario u WHERE u.usuario = ?1 AND u.email = ?2")
	Optional<Usuario> findByEmail(String usuario, String email);
}
