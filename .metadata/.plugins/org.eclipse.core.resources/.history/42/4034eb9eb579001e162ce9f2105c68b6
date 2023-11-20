package br.com.fiap.fmba.controller.api;

import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import br.com.fiap.fmba.controller.AbstractController;
import br.com.fiap.fmba.resources.exception.AutenticatorException;
import br.com.fiap.fmba.resources.exception.BusinessException;
import br.com.fiap.fmba.resources.exception.WebServiceException;
import br.com.fiap.fmba.service.ClienteService;
import br.com.fiap.fmba.service.payload.ClientePayload;
import io.swagger.annotations.ApiOperation;
import io.swagger.annotations.ApiResponse;
import io.swagger.annotations.ApiResponses;

@RestController
@RequestMapping("/api/cliente")
public class ClienteController extends AbstractController {

	@Autowired
	private ClienteService service = null;
	
	@ApiOperation(value = "Pesquisa todos os clientes")
    @ApiResponses(value = {
            @ApiResponse(code = 200, message = "Retorna lista de clientes"),
            @ApiResponse(code = 500, message = "Foi gerada uma exceção"),
    })
	@GetMapping(produces="application/json")
	public ResponseEntity<List<ClientePayload>> findAll() throws WebServiceException, BusinessException, AutenticatorException { 		
		return new ResponseEntity<>(this.service.findAll(), HttpStatus.OK);
	}
}
