package br.com.fiap.fmba.service;

import java.util.ArrayList;
import java.util.Arrays;
import java.util.Collections;
import java.util.List;
import java.util.Map.Entry;

import org.slf4j.Logger;
import org.slf4j.LoggerFactory;
import org.springframework.beans.factory.annotation.Value;
import org.springframework.boot.web.client.RestTemplateBuilder;
import org.springframework.http.HttpEntity;
import org.springframework.http.HttpHeaders;
import org.springframework.http.HttpMethod;
import org.springframework.http.MediaType;
import org.springframework.http.ResponseEntity;
import org.springframework.web.client.RestTemplate;

import com.fasterxml.jackson.databind.ObjectMapper;

public abstract class AbstractService {

	/** Logger */
	public static Logger LOGGER = LoggerFactory.getLogger(AbstractService.class);
	
	@Value("${fmba.token.origin}")
	private String tokenOrigin = null;
	
	private RestTemplate rest = null;
		
	public AbstractService(RestTemplateBuilder builder) { 
	    this.rest = builder.build();
	}
	
	/**
	 * Constroi String com parametros (Query Param)
	 * @param params
	 * @return
	 */
	@SuppressWarnings("unchecked")
	private String buildParans(Entry<String, Object>... params) {
		StringBuilder sb = new StringBuilder();
		for(Entry<String, Object> param : params) {
			if(!sb.toString().isEmpty()) {
				sb.append("&");
			}
			sb.append(param.getKey()).append("=").append(param.getValue());
		}
		return sb.toString();
	}
	
	/**
	 * Headers
	 * @return
	 */
	private HttpHeaders buildHeaders() {
		HttpHeaders headers = new HttpHeaders();
		headers.setContentType(MediaType.APPLICATION_JSON);
		headers.setAccept(Collections.singletonList(MediaType.APPLICATION_JSON));
		headers.set("FMBA-ORIGIN", this.tokenOrigin);
		return headers;
	}
	
	/**
	 * GET
	 * @param <RESPONSE>
	 * @param url
	 * @param listResponseClass
	 * @param params
	 * @return
	 */
	@SuppressWarnings("unchecked")
	protected <RESPONSE> List<RESPONSE> doGetList(String url, Class<RESPONSE> responseClass, Entry<String, Object>... params) {
		LOGGER.info("Executando API: findAll " + this.getClass().getSimpleName());
		
		List<RESPONSE> responseList = new ArrayList<>();
		
		StringBuilder finalUrl = new StringBuilder(url);
		if(params != null && params.length > 0) {
			finalUrl.append("?").append(this.buildParans(params));
		}
		HttpHeaders headers = this.buildHeaders();
		HttpEntity<String> request = new HttpEntity<String>("body", headers);
		ResponseEntity<Object[]> exchange = rest.exchange(finalUrl.toString(), HttpMethod.GET, request, Object[].class);
		
		ObjectMapper mapper = new ObjectMapper();
		Arrays.stream(exchange.getBody()).forEach(object -> {			
			responseList.add(mapper.convertValue(object, responseClass));
		});	
		return responseList;
	}

	/**
	 * GET
	 * @param <T>
	 * @param url
	 * @param responseClass
	 * @return
	 */
	@SuppressWarnings("unchecked")
	protected <RESPONSE> RESPONSE doGet(String url, Class<RESPONSE> responseClass, Entry<String, Object>... params) {
		LOGGER.info("Executando API: doGet " + this.getClass().getSimpleName());
		StringBuilder finalUrl = new StringBuilder(url);
		if(params != null && params.length > 0) {
			finalUrl.append("?").append(this.buildParans(params));
		}
		HttpHeaders headers = this.buildHeaders();
		HttpEntity<String> request = new HttpEntity<String>("body", headers);
		ResponseEntity<RESPONSE> exchange = rest.exchange(finalUrl.toString(), HttpMethod.GET, request, responseClass);
		return exchange.getBody();
	}
	
	/**
	 * POST
	 * @param <RESPONSE>
	 * @param <BODY>
	 * @param url
	 * @param body
	 */
	protected <BODY> void doPost(String url, BODY body) {
		LOGGER.info("Executando API: doPost " + this.getClass().getSimpleName());
		HttpHeaders headers = this.buildHeaders();
		HttpEntity<BODY> request = new HttpEntity<>(body, headers);
		rest.exchange(url, HttpMethod.POST, request, Object.class);
	}
	
	/**
	 * POST
	 * @param <RESPONSE>
	 * @param url
	 * @param listResponseClass
	 * @param params
	 * @return
	 */
	protected <RESPONSE, BODY> List<RESPONSE> doPostList(String url, Class<RESPONSE> responseClass, BODY body) {
		LOGGER.info("Executando API: doPostList " + this.getClass().getSimpleName());
		List<RESPONSE> responseList = new ArrayList<>();		
		HttpHeaders headers = this.buildHeaders();
		HttpEntity<BODY> request = new HttpEntity<>(body, headers);
		ResponseEntity<Object[]> exchange = rest.exchange(url, HttpMethod.POST, request, Object[].class);
		ObjectMapper mapper = new ObjectMapper();
		Arrays.stream(exchange.getBody()).forEach(object -> {			
			responseList.add(mapper.convertValue(object, responseClass));
		});	
		return responseList;
	}
	
	/**
	 * POST
	 * @param <RESPONSE>
	 * @param <BODY>
	 * @param url
	 * @param responseClass
	 * @param body 
	 * @return
	 */
	protected <RESPONSE, BODY> RESPONSE doPost(String url, Class<RESPONSE> responseClass, BODY body) {
		LOGGER.info("Executando API: doPost " + this.getClass().getSimpleName());
		HttpHeaders headers = this.buildHeaders();
		HttpEntity<BODY> request = new HttpEntity<>(body, headers);
		return rest.exchange(url, HttpMethod.POST, request, responseClass).getBody();
	}
	
	/**
	 * PUT
	 * @param <RESPONSE>
	 * @param <BODY>
	 * @param url
	 * @param responseClass
	 * @param body
	 * @return
	 */
	protected <BODY> void doPut(String url, BODY body) {
		LOGGER.info("Executando API: doPut " + this.getClass().getSimpleName());
		HttpHeaders headers = this.buildHeaders();
		HttpEntity<BODY> request = new HttpEntity<>(body, headers);
		rest.exchange(url, HttpMethod.PUT, request, Object.class);
	}
	
	/**
	 * Delete
	 * @param url
	 * @return
	 */
	protected void doDelete(String url) {
		LOGGER.info("Executando API: doDelete " + this.getClass().getSimpleName());
		HttpHeaders headers = this.buildHeaders();
		HttpEntity<String> request = new HttpEntity<>("body", headers);
		rest.exchange(url, HttpMethod.DELETE, request, Object.class);
	}
}
