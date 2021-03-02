# ResponseEntity

Podemos usar um objeto `ResponseEntity` para configurar as respostas HTTP, pois ele representa toda a resposta HTTP: código de status, cabeçalhos e corpo.

> `ResponseEntity` é um tipo genérico. Consequentemente, podemos usar qualquer tipo como corpo de resposta como, por exemplo, uma String:

```java
@GetMapping("/hello")
public ResponseEntity<String> hello() {
    return ResponseEntity.ok("Hello World!");
}
```

Para os códigos de status HTTP mais populares, obtemos métodos estáticos:

```java
BodyBuilder accepted();
BodyBuilder badRequest();
BodyBuilder created(java.net.URI location);
HeadersBuilder<?> noContent();
HeadersBuilder<?> notFound();
BodyBuilder ok();

```
