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
import br.com.fiap.fmba.service.VeiculoService;
import br.com.fiap.fmba.service.payload.VeiculoPayload;
import io.swagger.annotations.ApiOperation;
import io.swagger.annotations.ApiResponse;
import io.swagger.annotations.ApiResponses;

@RestController
@RequestMapping("/api/veiculo")
public class VeiculoController extends AbstractController {

	@Autowired
	private VeiculoService service = null;
	
	@ApiOperation(value = "Pesquisa todos os Veiculos")
    @ApiResponses(value = {
            @ApiResponse(code = 200, message = "Retorna lista de veiculos"),
            @ApiResponse(code = 500, message = "Foi gerada uma exceção"),
    })
	@GetMapping(produces="application/json")
	public ResponseEntity<List<VeiculoPayload>> findAll() throws WebServiceException, BusinessException, AutenticatorException {		
		return new ResponseEntity<>(this.service.findAll(), HttpStatus.OK);
	}
}
