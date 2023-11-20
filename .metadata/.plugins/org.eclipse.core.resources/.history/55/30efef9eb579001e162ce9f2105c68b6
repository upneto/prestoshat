package br.com.fiap.fmba.controller.api;

import java.util.List;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.HttpStatus;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.DeleteMapping;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.PathVariable;
import org.springframework.web.bind.annotation.PostMapping;
import org.springframework.web.bind.annotation.PutMapping;
import org.springframework.web.bind.annotation.RequestBody;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import br.com.fiap.fmba.controller.AbstractController;
import br.com.fiap.fmba.controller.payload.ordemservico.OrdemServicoRequest;
import br.com.fiap.fmba.controller.payload.ordemservico.OrdemServicoResponse;
import br.com.fiap.fmba.resources.exception.AutenticatorException;
import br.com.fiap.fmba.resources.exception.BusinessException;
import br.com.fiap.fmba.resources.exception.WebServiceException;
import br.com.fiap.fmba.service.OrdemServicoService;
import io.swagger.annotations.ApiOperation;
import io.swagger.annotations.ApiResponse;
import io.swagger.annotations.ApiResponses;

@RestController
@RequestMapping("/api/ordem_servico")
public class OrdemServicoController extends AbstractController {

	@Autowired
	private OrdemServicoService service = null;
	
	@ApiOperation(value = "Pesquisa todas as Ordens de Servico")
    @ApiResponses(value = {
            @ApiResponse(code = 200, message = "Retorna lista de Ordens de Servico"),
            @ApiResponse(code = 500, message = "Foi gerada uma exceção"),
    })
	@GetMapping(produces="application/json")
	public ResponseEntity<List<OrdemServicoResponse>> findAll() throws WebServiceException, BusinessException, AutenticatorException {		
		return new ResponseEntity<>(this.service.findAll(), HttpStatus.OK);
	}
	
	@ApiOperation(value = "Pesquisa Ordem de Servico por ID")
    @ApiResponses(value = {
            @ApiResponse(code = 200, message = "Retorna OrdemServico"),
            @ApiResponse(code = 500, message = "Foi gerada uma exceção"),
    })
	@GetMapping(value = "/{id}", produces="application/json")
	public ResponseEntity<OrdemServicoResponse> findBy(@PathVariable long id) throws WebServiceException, BusinessException, AutenticatorException {		
		return new ResponseEntity<>(this.service.find(id), HttpStatus.OK);
	}
	
	@ApiOperation(value = "Grava nova Ordem de Servico")
    @ApiResponses(value = {
            @ApiResponse(code = 200, message = "Gravou Ordem de Servico com sucesso"),
            @ApiResponse(code = 500, message = "Foi gerada uma exceção"),
    })
	@PostMapping(produces="application/json", consumes="application/json")
	public ResponseEntity<?> insert(@RequestBody OrdemServicoRequest ordemServico) throws WebServiceException, BusinessException, AutenticatorException {		
		this.service.insert(ordemServico);
		return new ResponseEntity<>(HttpStatus.OK);
	}
	
	@ApiOperation(value = "Altera Ordem de Servico")
    @ApiResponses(value = {
            @ApiResponse(code = 200, message = "Alterou Ordem de Servico com sucesso"),
            @ApiResponse(code = 500, message = "Foi gerada uma exceção"),
    })
	@PutMapping(produces="application/json", consumes="application/json")
	public ResponseEntity<?> update(@RequestBody OrdemServicoRequest ordemServico) throws WebServiceException, BusinessException, AutenticatorException {
		this.service.update(ordemServico);
		return new ResponseEntity<>(HttpStatus.OK);
	}
	
	@ApiOperation(value = "Remove Ordem de Servico")
    @ApiResponses(value = {
            @ApiResponse(code = 200, message = "Removeu Ordem de Servico com sucesso"),
            @ApiResponse(code = 500, message = "Foi gerada uma exceção"),
    })
	@DeleteMapping(value = "/{id}", produces="application/json")
	public ResponseEntity<?> delete(@PathVariable long id) throws WebServiceException, BusinessException, AutenticatorException {		
		this.service.delete(id);
		return new ResponseEntity<>(HttpStatus.OK);
	}
}
