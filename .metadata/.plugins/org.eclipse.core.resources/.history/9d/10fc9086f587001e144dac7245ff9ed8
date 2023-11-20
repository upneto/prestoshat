package br.com.prestoshat.usecase.security;

import java.nio.charset.StandardCharsets;
import java.time.LocalDateTime;
import java.time.ZoneId;
import java.util.Date;

import br.com.prestoshat.resources.exception.LoginException;
import io.jsonwebtoken.Jwts;
import io.jsonwebtoken.security.Keys;

public final class TokenBuilder {

	/**
	 * Chave da criptografia
	 */
	private final String SECRET = "BwyAnkAUDOzZm+mAUdCMDMPV8o3RfczNzQBbHgiLGiA=";
	
	/**
	 * 
	 * @return
	 */
	public static final TokenBuilder getInstance() {
		return new TokenBuilder();
	}
	
	/**
	 * Gera JWT
	 * @param usuario
	 * @return
	 */
	public final String getToken(String usuario) {
		return "Bearer " + Jwts.builder()
				.setSubject(usuario)
				.setIssuer("fmba-backent-user")
				.setIssuedAt(new Date())
				.setExpiration(Date.from(LocalDateTime.now().plusMinutes(60L).atZone(ZoneId.systemDefault()).toInstant()))
				.signWith(Keys.hmacShaKeyFor(SECRET.getBytes(StandardCharsets.UTF_8)))
				.compact();
	}
	
	/**
	 * Valida JWT
	 * @param token
	 * @return
	 * @throws LoginException
	 */
	public final boolean validateToken(String token) throws LoginException {
		final String _TOKEN = token.substring("Bearer".length()).trim();
		try {
			Jwts.parserBuilder().setSigningKey(Keys.hmacShaKeyFor(SECRET.getBytes(StandardCharsets.UTF_8))).build().parseClaimsJws(_TOKEN);
			return true;
		} catch (Exception e) {
			throw new LoginException("Sessão encerrada! Favor efetivar novo login.", e);
		}
	}
}
