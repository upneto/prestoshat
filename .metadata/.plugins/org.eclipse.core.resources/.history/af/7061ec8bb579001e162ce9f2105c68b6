package br.com.fiap.fmba.resources.aspect;

import javax.security.sasl.AuthenticationException;
import javax.servlet.http.HttpServletRequest;

import org.aspectj.lang.annotation.Aspect;
import org.aspectj.lang.annotation.Before;
import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.core.annotation.Order;
import org.springframework.stereotype.Component;

@Aspect
@Component
@Order(value = 1)
public class OriginCalled {

	@Autowired
	private HttpServletRequest request = null;
	
	@Value("${fmba.token.origin}")
	private String tokenOrigin = null;
	
	/** Logger */
	protected static final Logger LOGGER = LoggerFactory.getLogger(OriginCalled.class);
	
	/**
	 * Valida autenticacao pelo token JWT
	 * @throws Throwable
	 */
	@Before("execution(* br.com.fiap.fmba.controller.api.*.*(..))")
	public void execute() throws Throwable  {
		LOGGER.info("Request {}", this.request.getRequestURI());	    	    
    	String token = this.request.getHeader("FMBA-ORIGIN");
    	LOGGER.info("Origin: {}", (token != null && !token.isEmpty()));
    	
    	if(!this.tokenOrigin.equals(token)) {
    		throw new AuthenticationException("Origem da requisicao não reconhecida!!!");
    	}
	}
}
