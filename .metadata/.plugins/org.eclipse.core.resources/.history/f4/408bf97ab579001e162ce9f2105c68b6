package br.com.fiap.fmba.controller.api;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import br.com.fiap.fmba.controller.payload.UsuarioRequest;
import br.com.fiap.fmba.resources.exception.BusinessException;
import br.com.fiap.fmba.resources.exception.DaoException;
import br.com.fiap.fmba.usecase.Access;
import io.swagger.annotations.ApiOperation;
import io.swagger.annotations.ApiResponse;
import io.swagger.annotations.ApiResponses;

@RestController
@RequestMapping("/access")
public class AccessController {

	@Autowired
	private Access accessService;
	
	@ApiOperation(value = "Criou novo cadastro de acesso")
    @ApiResponses(value = {
            @ApiResponse(code = 200, message = "Acesso criado com com sucesso"),
            @ApiResponse(code = 500, message = "Foi gerada uma exceção no sistema"),
            @ApiResponse(code = 403, message = "Foi gerada uma exceção de negocio"),
            @ApiResponse(code = 401, message = "Foi gerada uma exceção de autenticação")
    })
	@PostMapping(produces="application/json", consumes="application/json")
	public ResponseEntity<?> newAccess(@RequestBody UsuarioRequest request) throws DaoException, BusinessException {
		this.accessService.doCreateAccess(request);
		return new ResponseEntity<>(HttpStatus.OK);
	}

}
