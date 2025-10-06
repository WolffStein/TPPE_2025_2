## Aula 25/08/2025

| Área             | Ferramentas / Técnicas                                                                 |
|------------------|-----------------------------------------------------------------------------------------|
| **Requisitos**   | Brainstorm • Questionário • Lean Inception                                              |
| **Prototipação** | Figma (buscar templates pagos) • v0                                                     |
| **Infra**        | Terraform • Docker • Kubernetes • CI/CD                                                 |
| **Banco de Dados** | PostgreSQL • MySQL • ElasticSearch • MongoDB                                          |
| **Back-end**     | Node.js • Next.js • Quarkus (Java) • Spring Boot (Java) • Django (Python) • FastAPI (Python) |
| **Testes**       | Pytest (unitário e integração) • JUnit (unitário e integração) • Selenium (simulação de usuário) |
| **Front-end**    | React (JS) • Vue (JS) • Angular (JS)                                                    |



## Aula 01 27/08/2025

- Verificação e aprovação de trabalho pelo professor

## Aula 02 01/09/2025

- Definição do que é necessário para o trabalho parte 1:
1. Ambiente dockerizado
2. Arquitetura ( estilo django, models, testes, assets bem definidos em pastas)
3. Histórias de usuários ( Fulano de tal, quer acessar o site e realizar cadastro) pelo menos 10
4. Diagrama UML
5. Testes
6. Protótipo  ( Figma / V0 )

## Aula 03 03/09/2025

### Ambiente 

- DevOps + Infra -> Prepara o ambiente de desenvolvimento ( CI / CD )
- Infra -> Cuida do servidor, quantidade de ram, picos de energia, se esta com hd 100%, trafego de rede.

Docker: Ambiente **local** de desenvolvimento

Quando subimos o dokcer compose a versão da imagem é gerada na primeira linha, quando existem divergencias entre docker, devemos olhar por ali

- informações do container: docker spect 
- mostra os containers: docker ps -a 
- mata o container: docker -rm rf < container >    


### Ambiente de DEV

- Ambiente de dev: CI/CD ( Uso de testes ) aciona quando usamos PR. (github actions)
- Ambiente de homologação: 
- Ambiente de produção ( PRD ):


#### Ambientes para o trabalho

- Ambiente local e de Produção (CI / CD com testes de integração 7980)



##  Aula 10/09/2025

- Backend -> API


Boas práticas de API, uma tabela por API.

ORM -> Consome dados do banco e entregam para API

FAST API -> SQL alchemy

SWAGGER -> Documentação da API

https:localhost:<portalocal\>/docs

JWT -> gera token de autenticação ( Ponto de controle 2) em um repositorio separado, container separado.

cobertura de testes de front será feito via selenium.
teste integração ( aponta pro end point para ver se o parametro esta correto)

## Aula 17/09/2025

Refatoração
- Clean Code
- Enum (conjunto de numeros que são variaveis)
- No codigo precisa especificar o enum (no dicionário de dados), nao precisa no uml, mas precisa cita-lo
- Repetição de código.
- ORM
- PEP8 (guia de estilo em python)
- **Lint** vai avaliar se foi escrito no guia corretamente 


## Aula 06/10/2025

Ponto de Controle 2:

- Backend Completo
- Testes Completo ( Unitários / Integração(testa o endpoint) e Parametrizados (passando mais de 2 parametros = parametrizado) )
- Teste dentro do docker (Executar dentro do compose up)
- Lint nota 10
- Refatoração ( Cleancode, Solid )
- API de autenticação em repositorio separado. **Usar o Render para hospedar os repositorios**
- Modelagem completa do Banco ( Modelo Fisico, DDL )
