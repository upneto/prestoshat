package br.com.fiap.fmba.resources.exception.handler;

import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.ExceptionHandler;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.bind.annotation.RestControllerAdvice;
import org.springframework.web.context.request.WebRequest;
import org.springframework.web.servlet.mvc.method.annotation.ResponseEntityExceptionHandler;

import br.com.fiap.fmba.resources.exception.DaoException;
import lombok.AllArgsConstructor;
import lombok.Getter;

/**
 * @author Ulisses Neto
 */
@RestController
@RestControllerAdvice
public class AppExceptionHandler extends ResponseEntityExceptionHandler {
	
	@Getter
	@AllArgsConstructor
	private class ResponseError {
		private String type;
		private String message;
	}

	/**
	 * Manipulador de exceção para erros do tipo 'AppException'
	 * @param exception
	 * @param request
	 * @return
	 */
	@ExceptionHandler(DaoException.class)
	public final ResponseEntity<ResponseError> handleAppExceptions(DaoException exception, WebRequest request){		
		return new ResponseEntity<ResponseError>(
				new ResponseError(DaoException.class.getName(), exception.getMessage()), 
				HttpStatus.INTERNAL_SERVER_ERROR);
	}
}
