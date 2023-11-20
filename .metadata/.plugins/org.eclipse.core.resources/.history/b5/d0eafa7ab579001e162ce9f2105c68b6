package br.com.fiap.fmba.resources.exception.handler;

import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.ExceptionHandler;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.bind.annotation.RestControllerAdvice;
import org.springframework.web.context.request.WebRequest;
import org.springframework.web.servlet.mvc.method.annotation.ResponseEntityExceptionHandler;

import br.com.fiap.fmba.resources.exception.BusinessException;
import br.com.fiap.fmba.resources.exception.DaoException;
import br.com.fiap.fmba.resources.exception.LoginException;

/**
 * @author Ulisses Neto
 */
@RestController
@RestControllerAdvice
public class AppExceptionHandler extends ResponseEntityExceptionHandler {

	/**
	 * Manipulador de exceção para erros do tipo 'DaoException'
	 * @param exception
	 * @param request
	 * @return
	 */
	@ExceptionHandler(DaoException.class)
	public final ResponseEntity<String> handleAppExceptions(DaoException exception, WebRequest request){		
		return new ResponseEntity<String>(exception.getMessage(), HttpStatus.INTERNAL_SERVER_ERROR);
	}
	
	/**
	 * Manipulador de exceção para erros do tipo 'BusinessException'
	 * @param exception
	 * @param request
	 * @return
	 */
	@ExceptionHandler(BusinessException.class)
	public final ResponseEntity<String> handleAppExceptions(BusinessException exception, WebRequest request){		
		return new ResponseEntity<String>(exception.getMessage(), HttpStatus.FORBIDDEN);
	}
	
	/**
	 * Manipulador de exceção para erros do tipo 'LoginException'
	 * @param exception
	 * @param request
	 * @return
	 */
	@ExceptionHandler(LoginException.class)
	public final ResponseEntity<String> handleAppExceptions(LoginException exception, WebRequest request){		
		return new ResponseEntity<String>(exception.getMessage(), HttpStatus.UNAUTHORIZED);
	}
}
