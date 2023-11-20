package br.com.fiap.fmba.service;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.boot.web.client.RestTemplateBuilder;
import org.springframework.stereotype.Service;

import br.com.fiap.fmba.controller.payload.autenticacao.LoginRequest;
import br.com.fiap.fmba.controller.payload.autenticacao.LoginResponse;
import br.com.fiap.fmba.controller.payload.autenticacao.TokenRequest;
import br.com.fiap.fmba.resources.exception.AutenticatorException;


@Service
public class AutenticacaoService extends AbstractService {
	
	@Autowired
	public AutenticacaoService(RestTemplateBuilder builder) {
	    super(builder);
	}
	
	/**
	 * Variavel injetada pelo contexto Spring
	 * 		'env' = variavel injetada da runtime jvm
	 * 		'.url.backend.ordem_servico' = arquivo application.properties  
	 */
	@Value("${${env}.url.backend.user}")
	private String url = null;
	
	/**
	 * Efetua Login
	 * @param request
	 * @return
	 * @throws AutenticatorException
	 */
	public LoginResponse login(LoginRequest request) throws AutenticatorException {
		LOGGER.info("Executando API: " + url + "login");
		return super.doPost(url + "login", LoginResponse.class, request);
	}

	/**
	 * Verifica Login Ativo
	 * @param request
	 * @return
	 * @throws AutenticatorException
	 */
	public LoginResponse verify(TokenRequest request) throws AutenticatorException {
		LOGGER.info("Executando API: " + url + "login/verify");
		return super.doPost(url + "login/verify", LoginResponse.class, request);
	}
}
