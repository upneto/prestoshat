package br.com.fiap.fmba.resources.aspect;

import javax.servlet.http.HttpServletRequest;

import org.aspectj.lang.annotation.Aspect;
import org.aspectj.lang.annotation.Before;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.core.annotation.Order;
import org.springframework.stereotype.Component;

import br.com.fiap.fmba.controller.payload.autenticacao.TokenRequest;
import br.com.fiap.fmba.service.AutenticacaoService;

@Aspect
@Component
@Order(value = 1)
public class Autenticador {
	
	@Autowired
	private HttpServletRequest request = null;
	
	@Autowired
	private AutenticacaoService autenticacaoService = null;
	
	/** Logger */
	protected static final Logger LOGGER = LoggerFactory.getLogger(Autenticador.class);

	/**
	 * Valida autenticacao pelo token JWT
	 * @throws Throwable
	 */
	@Before("execution(* br.com.fiap.fmba.controller.api.*.*(..))")
	public void execute() throws Throwable  {
		LOGGER.info("Request {}", this.request.getRequestURI());	    	    
    	String token = this.request.getHeader("JWT_TOKEN");
    	LOGGER.info("Is Tokenized {}", (token != null && !token.isEmpty()));
    	
   		this.autenticacaoService.verify(new TokenRequest(token));
	}
}
