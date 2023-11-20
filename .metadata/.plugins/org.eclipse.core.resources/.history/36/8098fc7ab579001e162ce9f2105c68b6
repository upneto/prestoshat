package br.com.fiap.fmba.controller.api;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import br.com.fiap.fmba.controller.payload.LoginRequest;
import br.com.fiap.fmba.controller.payload.TokenRequest;
import br.com.fiap.fmba.resources.exception.DaoException;
import br.com.fiap.fmba.resources.exception.LoginException;
import br.com.fiap.fmba.usecase.Login;
import io.swagger.annotations.ApiOperation;
import io.swagger.annotations.ApiResponse;
import io.swagger.annotations.ApiResponses;

@RestController
@RequestMapping("/login")
public class LoginController {
	
	@Autowired
	private Login loginService;
	
	@ApiOperation(value = "Efetivou o login")
    @ApiResponses(value = {
            @ApiResponse(code = 200, message = "Login efetivado com com sucesso"),
            @ApiResponse(code = 500, message = "Foi gerada uma exceção no sistema"),
            @ApiResponse(code = 403, message = "Foi gerada uma exceção de negocio"),
            @ApiResponse(code = 401, message = "Foi gerada uma exceção de autenticação")
    })
	@PostMapping(produces="application/json", consumes="application/json")
	public ResponseEntity<?> login(@RequestBody LoginRequest request) throws DaoException, LoginException {
		return new ResponseEntity<>(this.loginService.doLogin(request), HttpStatus.OK);
	}


	@ApiOperation(value = "Validou a sessão ")
    @ApiResponses(value = {
            @ApiResponse(code = 200, message = "A sessão expirou ou está inativa"),
            @ApiResponse(code = 500, message = "Foi gerada uma exceção no sistema"),
            @ApiResponse(code = 403, message = "Foi gerada uma exceção de negocio"),
            @ApiResponse(code = 401, message = "Foi gerada uma exceção de autenticação")
    })
	@PostMapping(path = "/verify", produces="application/json", consumes="application/json")
	public ResponseEntity<?> verify(@RequestBody TokenRequest request) throws LoginException {
		this.loginService.doVerify(request);
		return new ResponseEntity<>(HttpStatus.OK);
	}
	
}
