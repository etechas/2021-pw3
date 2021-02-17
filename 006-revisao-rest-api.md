# Revisão de Conceitos


## REST API

REST (**Representational State Transfer**) é um estilo de arquitetura de software que define uma série de restrições para a criação de web-services (serviços Web), isto é, restringe como seus componentes interagem entre si.

> Esse termo foi introduzido e definido por Roy Fielding em sua tese de doutorado no final dos anos 90.

## E RESTful?

Dizemos que uma API é RESTful se sua implementação está de acordo com a arquitetura REST proposta por Roy Fielding. 

## Anotações para API RESTful

- `@RestController:` permite criar um controlador REST que manipula as requisições vindas dos clientes.

- `@RequestMapping:` anotação responsável por fazer o mapeamento de um recurso.

- `@GetMapping:` mapeia solicitações HTTP GET em métodos de tratamento específicos.
 
- `@PostMapping:` mapeia solicitações HTTP POST em métodos de tratamento específicos.

- `@PutMapping:` mapeia solicitações HTTP PUT em métodos de tratamento específicos.

- `@DeleteMapping:` mapeia solicitações HTTP DELETE em métodos de tratamento específicos.

- `@PathVariable:` utilizado quando o valor da variável é passada diretamente na URL.

- `@RequestParam:` utilizado quando temos vários parâmetros passados por url, mas que não são parte da url em sí.

