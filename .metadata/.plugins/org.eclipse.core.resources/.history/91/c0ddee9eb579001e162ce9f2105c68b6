package br.com.fiap.fmba.controller;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import br.com.fiap.fmba.controller.payload.autenticacao.LoginRequest;
import br.com.fiap.fmba.controller.payload.autenticacao.LoginResponse;
import br.com.fiap.fmba.resources.exception.AutenticatorException;
import br.com.fiap.fmba.resources.exception.WebServiceException;
import br.com.fiap.fmba.service.AutenticacaoService;
import io.swagger.annotations.ApiOperation;
import io.swagger.annotations.ApiResponse;
import io.swagger.annotations.ApiResponses;

@RestController
@RequestMapping("/login")
public class LoginController extends AbstractController {

	@Autowired
	private AutenticacaoService service = null;
	
	@ApiOperation(value = "Efetivou o login")
    @ApiResponses(value = {
            @ApiResponse(code = 200, message = "Login efetivado com com sucesso"),
            @ApiResponse(code = 500, message = "Foi gerada uma exceção no sistema"),
            @ApiResponse(code = 403, message = "Foi gerada uma exceção de negocio"),
            @ApiResponse(code = 401, message = "Foi gerada uma exceção de autenticação")
    })
	@PostMapping(produces="application/json", consumes="application/json")
	public ResponseEntity<LoginResponse> login(@RequestBody LoginRequest request) throws WebServiceException, AutenticatorException {
		LOGGER.info("Executando Login ... ");
		System.out.println("Executando Login ... ");
		return new ResponseEntity<>(this.service.login(request), HttpStatus.OK);
	}
}
