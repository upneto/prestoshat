package br.com.fiap.fmba.resources.exception.handler;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.ExceptionHandler;
import org.springframework.web.bind.annotation.ResponseBody;
import org.springframework.web.bind.annotation.ResponseStatus;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.bind.annotation.RestControllerAdvice;
import org.springframework.web.client.HttpClientErrorException;
import org.springframework.web.context.request.WebRequest;
import org.springframework.web.servlet.mvc.method.annotation.ResponseEntityExceptionHandler;

import br.com.fiap.fmba.resources.exception.AutenticatorException;
import br.com.fiap.fmba.resources.exception.BusinessException;
import br.com.fiap.fmba.resources.exception.WebServiceException;
import br.com.fiap.fmba.resources.exception.handler.payload.ExceptionResponsePayload;
import br.com.fiap.fmba.service.AbstractService;

/**
 * @author Ulisses Neto
 */
@RestController
@RestControllerAdvice
public class AppExceptionHandler extends ResponseEntityExceptionHandler {
	
	/** Logger */
	public static Logger LOGGER = LoggerFactory.getLogger(AbstractService.class);

	/**
	 * Manipulador de exceção para erros do tipo 'AppException'
	 * @param exception
	 * @param request
	 * @return
	 */
	@ExceptionHandler(AutenticatorException.class)
	@ResponseStatus(HttpStatus.UNAUTHORIZED)
    @ResponseBody
	public final ResponseEntity<ExceptionResponsePayload> handleAppExceptions(AutenticatorException exception, WebRequest request){
		LOGGER.error("=> Error type: " + AutenticatorException.class.getName());
		LOGGER.error("=> Error msg: " + exception.getMessage());
		return ResponseEntity.status(HttpStatus.UNAUTHORIZED).body(ExceptionResponsePayload.builder()
				.code(HttpStatus.UNAUTHORIZED.value())
				.description(HttpStatus.UNAUTHORIZED.name())
				.exception(exception.getMessage())
				.build());
	}
	
	/**
	 * Manipulador de exceção para erros do tipo 'AppException'
	 * @param exception
	 * @param request
	 * @return
	 */
	@ExceptionHandler(BusinessException.class)
	@ResponseStatus(HttpStatus.BAD_REQUEST)
    @ResponseBody
	public final ResponseEntity<ExceptionResponsePayload> handleAppExceptions(BusinessException exception, WebRequest request){	
		LOGGER.error("=> Error type: " + BusinessException.class.getName());
		LOGGER.error("=> Error msg: " + exception.getMessage());
		return ResponseEntity.status(HttpStatus.BAD_REQUEST).body(ExceptionResponsePayload.builder()
				.code(HttpStatus.BAD_REQUEST.value())
				.description(HttpStatus.UNAUTHORIZED.name())
				.exception(exception.getMessage())
				.build());
	}
	
	/**
	 * Manipulador de exceção para erros do tipo 'AppException'
	 * @param exception
	 * @param request
	 * @return
	 */
	@ExceptionHandler(WebServiceException.class)
	@ResponseStatus(HttpStatus.INTERNAL_SERVER_ERROR)
    @ResponseBody
	public final ResponseEntity<ExceptionResponsePayload> handleAppExceptions(WebServiceException exception, WebRequest request){		
		LOGGER.error("=> Error type: " + WebServiceException.class.getName());
		LOGGER.error("=> Error msg: " + exception.getMessage());
		return ResponseEntity.status(HttpStatus.INTERNAL_SERVER_ERROR).body(ExceptionResponsePayload.builder()
				.code(HttpStatus.INTERNAL_SERVER_ERROR.value())
				.description(HttpStatus.UNAUTHORIZED.name())
				.exception(exception.getMessage())
				.build());
	}	
	
	/**
	 * Manipulador de exceção para erros do tipo 'AppException'
	 * @param exception
	 * @param request
	 * @return
	 */
	@ExceptionHandler(HttpClientErrorException.class)
	@ResponseStatus(HttpStatus.INTERNAL_SERVER_ERROR)
    @ResponseBody
	public final ResponseEntity<ExceptionResponsePayload> handleAppExceptions(HttpClientErrorException exception, WebRequest request){		
		LOGGER.error("=> Error type: " + WebServiceException.class.getName());
		LOGGER.error("=> Error msg: " + exception.getMessage());
		return ResponseEntity.status(exception.getStatusCode()).body(ExceptionResponsePayload.builder()
				.code(exception.getStatusCode().value())
				.description(exception.getStatusCode().name())
				.exception(exception.getMessage())
				.build());
	}	
}