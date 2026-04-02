<!-- l10n-sync: source-file="01-add-endpoint.md" -->
# Adicionar um endpoint simples

## Cenário

O PetClinic é principalmente uma aplicação MVC (Thymeleaf + Spring MVC). Para ferramentas internas e integrações, a clínica quer um **pequeno endpoint JSON** que forneça:

- hora atual do servidor
- versão do Java em execução
- mensagem personalizada opcional

Isso é intencionalmente pequeno: é uma boa maneira de praticar o **code completion do Copilot** e **mudanças pequenas e seguras**.

> [!NOTE]
> Se a aplicação parar de funcionar, verifique o terminal onde você executou `spring-boot:run` para erros. Reinicie se necessário.

## Onde você trabalhará

Todas as alterações de código acontecem no seu clone local do Spring PetClinic.

Você criará um novo controller:

- package: `org.springframework.samples.petclinic.system.api`
- classe: `ClinicInfoController`

## Criar o endpoint (assistido pelo Copilot)

1. No IntelliJ, abra seu projeto `spring-petclinic`.
2. Crie um novo arquivo Java:
   - `src/main/java/org/springframework/samples/petclinic/system/api/ClinicInfoController.java`
3. Use o **code completion** do Copilot para implementar um `@RestController` com:
   - `@GetMapping("/api/clinic-info")`
   - resposta JSON contendo:
     - `serverTime` (string ISO-8601)
     - `javaVersion` (de `System.getProperty("java.version")`)
     - `message` (padrão: `"Welcome to PetClinic"`)
   - parâmetro de consulta opcional `name`:
     - quando presente, a mensagem se torna `"Welcome to PetClinic, <name>"`

### Nome da função + trecho de exemplo

Use este nome de função para o handler:

- `getClinicInfo`

Esta é uma implementação de exemplo (você não precisa seguir a implementação exata; digite-a para experimentar os completions):

```java
package org.springframework.samples.petclinic.system.api;

import java.time.OffsetDateTime;
import java.util.LinkedHashMap;
import java.util.Map;

import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@RestController
class ClinicInfoController {

    @GetMapping("/api/clinic-info")
    Map<String, String> getClinicInfo(@RequestParam(required = false) String name) {
        Map<String, String> result = new LinkedHashMap<>();
        result.put("serverTime", OffsetDateTime.now().toString());
        result.put("javaVersion", System.getProperty("java.version"));
        String message = (name == null || name.isBlank()) ? "Welcome to PetClinic" : "Welcome to PetClinic, " + name;
        result.put("message", message);
        return result;
    }
}
```

> [!IMPORTANT]
> Digite o código (não cole) para que você experimente os completions.

### Prompt sugerido (inline chat)

Se você preferir usar o inline chat no editor, peça ao Copilot algo como:

```
Create a Spring Boot RestController at /api/clinic-info that returns serverTime, javaVersion, and a message. If query param name is provided, personalize the message.
```
Você pode acessar o recurso de Inline Chat clicando com o botão direito no editor e selecionando "Open Inline Chat."
Você também pode abri-lo usando o atalho Shift + Ctrl + I (Mac) ou Shift + Ctrl + G (Windows).

## Validar o endpoint

1. Certifique-se de que a aplicação está rodando.
2. Abra:
   - http://localhost:8080/api/clinic-info
   - http://localhost:8080/api/clinic-info?name=Taylor

Você deverá ver a saída em JSON.

> [!NOTE]
> Após adicionar novo código, o Maven wrapper pode falhar devido a regras de formatação (frequentemente após o code completion). Você pode ver um erro como:
>
> ```
> spring-petclinic: Formatting violations found in the following files:
> [ERROR]  * C:\dev\spring-petclinic\src\main\java\org\springframework\samples\petclinic\system\ClinicController.java
> [ERROR]
> [ERROR] Run `spring-javaformat:apply` to fix.
> ```
>
> Corrija executando isso na raiz do repositório PetClinic:
> - macOS/Linux (e Git Bash): `./mvnw spring-javaformat:apply`
> - Windows PowerShell: `.\mvnw.cmd spring-javaformat:apply`

## Resumo e próximos passos

Você adicionou um pequeno endpoint e o validou de ponta a ponta. A seguir, você explorará a estrutura do projeto usando o Copilot Chat para construir contexto para mudanças maiores.
