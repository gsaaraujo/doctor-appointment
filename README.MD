**[Work in progress]**

Doctor appointment é sobre marcar consultas médicas.
A ideia desse repositório é mostrar como a aplicação está sendo feita e quais os motivos pela escolha das abordagens.

Microserviços disponíveis no momento
* [rauru](https://github.com/gsaaraujo/rauru) 
* [saria](https://github.com/gsaaraujo/saria) 

### Conceitos e como estão sendo utilizados
#### Domain Driven Design
* Concentração das regras de negócio nas entidades de domínio.
* Concentração de validações nos objetos de valor.
* Clusterizar entidades de domínio e objetos de valor. Essa clusterização é conhecido como agregado.
* Uso do Repository Pattern exclusivamente para trabalhar com agregados.


#### Hexagonal Architecture
* Para trazer independêcia aos usecases. Assim sendo, os usecases podem ser usados tanto por http (rest, graphql, etc), sockets ou mensageria, por exemplo, sem a necessidade de serem refatorados. Ou seja, não há acoplamento entre o domínio da aplicação e quem o usa.
* Do mesmo jeito, a aplicação pode se integrar à qualquer sistema externo sem se acoplar.


#### Clean Architecture
* Usecases para expressar as ações do usuário dentro da aplicação.
* Fluxo de dependência entre camadas, onde as camadas inferiores não conhecem as superiores e para isso é usado uma abstração entre elas.

#### Event Driven Architecture
* Emissão de eventos para comunicação assíncrona dos microserviços.
* Não obrigatório, mas os eventos também ajudam com CQRS.


#### CQRS
* Não existe necessidade para que as consultas à api passem pelo domínio. Reconstruir as entidades de domínio e objetos de valor em memória apenas para retornar dados ao cliente é desnecessário e pode causar problemas de escalabilidade. Outra coisa é que vai poluir a camada de domínio com usecases de consulta que não tem nada haver com o domínio.
Então a escrita vai ser feita pelo Repository Pattern e a leitura por Gateway Pattern.

#### Factory Method Pattern (uma versão mais simplificada)
* Usado para proteger as entidades de domínio e objetos de valor contra invariância. Logo, a existência de um objeto com algum dado inválido é impossível.

#### Adapter Pattern
* Adapter Pattern para criar um wrapper em bibliotecas externas trazendo desacoplamento e bastante facilidade para fazer testes.

#### Repository Pattern
* Usado com o objetivo único e exclusivo para trabalhar com agregados. 
  
#### Gateway Pattern
* Abstração de acessos à sistemas externos como banco de dados, apis etc.








