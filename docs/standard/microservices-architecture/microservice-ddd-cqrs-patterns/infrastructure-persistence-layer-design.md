---
title: Projetando a camada de persistência da infraestrutura
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Projetando a camada de persistência da infraestrutura
keywords: Docker, Microsserviços, ASP.NET, Contêiner
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/08/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: cab12426308be258134e0385c5a6eb6cdb5d544b
ms.sourcegitcommit: 2e8acae16ae802f2d6d04e3ce0a6dbf04e476513
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2018
---
# <a name="designing-the-infrastructure-persistence-layer"></a>Projetando a camada de persistência da infraestrutura

Os componentes de persistência de dados fornecem acesso aos dados hospedados dentro dos limites de um microsserviço (ou seja, em um banco de dados de microsserviço). Eles contêm a implementação real dos componentes, como repositórios e classes [Unidade de Trabalho](https://martinfowler.com/eaaCatalog/unitOfWork.html), como DBContexts de EF personalizados.

## <a name="the-repository-pattern"></a>O padrão de repositório

Repositórios são classes ou componentes que encapsulam a lógica necessária para acessar fontes de dados. Eles centralizam a funcionalidade comum de acesso a dados, melhorando a sustentabilidade e desacoplando a infraestrutura ou a tecnologia usada para acessar os bancos de dados da camada do modelo de domínio. Se você usa um ORM (mapeamento objeto-relacional) como o Entity Framework, o código que precisa ser implementado é simplificado, graças à LINQ (consulta integrada à linguagem) e à tipagem forte. Isso permite que você se concentre na lógica de persistência de dados e não nos detalhes técnicos do acesso a dados.

O padrão de repositório é uma maneira bem documentada de trabalhar com uma fonte de dados. No livro [Padrões de Arquitetura de Aplicações Corporativas](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/), Martin Fowler descreve um repositório da seguinte maneira:

Um repositório executa as tarefas de um intermediário entre as camadas de modelo de domínio e o mapeamento de dados, funcionando de maneira semelhante a um conjunto de objetos de domínio na memória. Os objetos de clientes criam consultas de forma declarativa e enviam-nas para os repositórios buscando respostas. Conceitualmente, um repositório encapsula um conjunto de objetos armazenados no banco de dados e as operações que podem ser executadas neles, fornecendo uma maneira que é mais próxima da camada de persistência. Os repositórios também oferecem a capacidade de separação, de forma clara e em uma única direção, a dependência entre o domínio de trabalho e a alocação de dados ou o mapeamento.

### <a name="define-one-repository-per-aggregate"></a>Definir um repositório por agregação

Para cada agregação ou raiz de agregação, você deve criar uma classe de repositório. Em um microsserviço baseado nos padrões de design orientado por domínio, o único canal que você deve usar para atualizar o banco de dados são os repositórios. O motivo é que eles têm uma relação um-para-um com a raiz de agregação, que controla as invariáveis e a consistência transacional da agregação. É possível consultar o banco de dados por outros canais [como ao seguir uma abordagem de CQRS (segregação de responsabilidade de comando e consulta)], porque as consultas não alteram o estado do banco de dados. No entanto, a área transacional, ou seja, as atualizações, sempre deve ser controlada pelos repositórios e pelas raízes de agregação.

Basicamente, um repositório permite popular na memória dados que são provenientes do banco de dados, em forma de entidades de domínio. Depois que as entidades estão na memória, elas podem ser alteradas e persistidas novamente no banco de dados por meio de transações.

Conforme observado anteriormente, se você estiver usando o padrão de arquitetura CQS/CQRS, as consultas inicias serão executadas por consultas à parte, fora do modelo de domínio, executadas por instruções SQL simples usando o Dapper. Essa abordagem é muito mais flexível do que os repositórios porque você pode consultar e unir as tabelas necessárias, e essas consultas não são restritas pelas regras das agregações. Esses dados irão para o aplicativo cliente ou para a camada de apresentação.

Se o usuário fizer alterações, os dados a serem atualizados virão da camada de apresentação ou do aplicativo cliente para a camada de aplicativo (como um serviço de API Web). Ao receber um comando (com os dados) em um manipulador de comandos, você usará repositórios para obter os dados que deseja atualizar do banco de dados. Você os atualizará na memória com as informações transmitidas com os comandos e, em seguida, adicionará ou atualizará esses dados (entidades de domínio) no banco de dados por meio de uma transação.

Lembre-se de que apenas um repositório deve ser definido para cada raiz de agregação, conforme é mostrado na Figura 9-17. Para atingir a meta da raiz de agregação de manter a consistência transacional entre todos os objetos na agregação, você nunca deve criar um repositório para cada tabela no banco de dados.

![](./media/image18.png)

**Figura 9-17**. A relação entre repositórios, agregações e tabelas de banco de dados

### <a name="enforcing-one-aggregate-root-per-repository"></a>Impondo uma raiz de agregação por repositório

É importante implementar o design do repositório de uma forma que ele imponha a regra de que apenas as raízes de agregação devem ter repositórios. Você pode criar um tipo de repositório genérico ou de base que restrinja o tipo de entidades com as quais trabalha para garantir que elas tenham a interface de marcador IAggregateRoot.

Assim, cada classe de repositório implementada na camada de infraestrutura implementa seu próprio contrato ou interface, conforme é mostrado no código a seguir:

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
```

Cada interface de repositório específica implementa a interface IRepository genérica:

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

No entanto, uma maneira melhor de fazer com que o código imponha a convenção de que cada repositório deve estar relacionado a uma única agregação seria implementar um tipo de repositório genérico para ficar explícito que você está usando um repositório destinado a uma agregação específica. Isso pode ser feito facilmente com a implementação desse genérico na interface base IRepository, como no código a seguir:

```csharp
  public interface IRepository<T> where T : IAggregateRoot
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a>O padrão de repositório facilita os testes da lógica do aplicativo

O padrão de repositório permite testar facilmente o aplicativo com testes de unidade. Lembre-se de que os testes de unidade testam apenas o código, não a infraestrutura, assim, as abstrações de repositório facilitam alcançar essa meta.

Como observado em uma seção anterior, é recomendável que você defina e coloque as interfaces de repositório na camada de modelo de domínio para que a camada de aplicativo (por exemplo, o microsserviço API Web) não dependa diretamente da camada de infraestrutura em que as classes de repositório reais foram implementadas. Fazendo isso e usando a injeção de dependência nos controladores da API Web, você pode implementar repositórios fictícios que retornam dados falsos em vez de dados do banco de dados. Essa abordagem de desacoplamento permite que você crie e execute testes de unidade que podem testar apenas a lógica do aplicativo sem precisar de conectividade com o banco de dados.

As conexões com bancos de dados podem falhar e, principalmente, executar centenas de testes em relação a um banco de dados é prejudicial por dois motivos. Primeiro, pode demorar muito devido ao grande número de testes. Segundo, os registros do banco de dados podem ser alterados e afetar os resultados dos testes, deixando-os inconsistentes. Testar em relação ao banco de dados não é um teste de unidade, mas sim um teste de integração. É interessante ter muitos testes de unidade em execução rápida, mas menos testes de integração em relação aos bancos de dados.

Em termos de separação de interesses para os testes de unidade, a lógica opera em entidades de domínio na memória. Ela considera que a classe de repositório as entregou. Depois que a lógica modifica as entidades de domínio, ela considera que a classe de repositório as armazenará corretamente. O ponto importante aqui é criar testes de unidade em relação ao seu modelo de domínio e à sua lógica de domínio. As raízes de agregação são os limites de consistência principais em DDD.

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a>A diferença entre o padrão de repositório e o padrão da classe DAL (classe de acesso a dados) herdada

Um objeto de acesso a dados executa operações de acesso e persistência de dados diretamente no armazenamento. O repositório marca os dados com as operações que você deseja executar na memória de um objeto de unidade de trabalho (como no EF ao usar o DbContext), mas essas atualizações não são realizadas imediatamente.

Uma unidade de trabalho é conhecida como uma única transação que envolve várias operações de inserção, atualização ou exclusão. Simplificando, isso significa que, para uma ação de usuário específica (por exemplo, o registro em um site), as transações de inserção, atualização e exclusão são tratadas em uma única transação. Isso é mais eficiente do que tratar várias transações de banco de dados de uma maneira mais intensa.

Essas várias operações de persistência serão executadas mais tarde em uma única ação quando o código da camada de aplicativo executar um comando para isso. A decisão de como aplicar as alterações realizadas na memória ao armazenamento de banco de dados real geralmente se baseia no [padrão de unidade de trabalho](https://martinfowler.com/eaaCatalog/unitOfWork.html). No EF, o padrão de unidade de trabalho é implementado como o DBContext.

Em muitos casos, esse padrão ou uma maneira de aplicar operações em relação ao armazenamento pode aumentar o desempenho do aplicativo e reduzir a possibilidade de inconsistências. Além disso, ele reduz o bloqueio de transações nas tabelas do banco de dados, porque todas as operações pretendidas são confirmadas em uma única transação. Isso é mais eficiente em comparação com a execução de muitas operações isoladas no banco de dados. Portanto, o ORM selecionado é capaz de otimizar a execução no banco de dados agrupando várias ações de atualização na mesma transação, em vez de executar várias transações pequenas e separadas.

### <a name="repositories-should-not-be-mandatory"></a>Os repositórios não devem ser obrigatórios

Os repositórios personalizados são úteis pelos motivos já citados e essa é a abordagem para o microsserviço de pedidos no eShopOnContainers. No entanto, esse não é um padrão essencial a ser implementado em um design DDD (design orientado por domínio) ou até mesmo no desenvolvimento no .NET, em geral.

Por exemplo, Jimmy Bogard, ao fornecer comentários diretos para este guia, diz o seguinte:

Esse provavelmente será meu maior comentário. Eu realmente não sou fã de repositórios, principalmente porque eles ocultam detalhes importantes do mecanismo de persistência subjacente. É por isso que eu também opto pelo MediatR para comandos. Posso usar toda a capacidade da camada de persistência e enviar por push todo esse comportamento de domínio para minhas raízes de agregação. Geralmente, eu não gosto de usar repositórios fictícios, ou seja, eu ainda preciso aplicar esse teste de integração na situação real. Optar por CQRS significa que realmente não precisamos mais de repositórios.

Achamos os repositórios úteis, mas sabemos que eles não são tão críticos para o DDD quanto o padrão de agregação e o modelo de domínio avançado. Portanto, use o padrão de repositório ou não, conforme achar mais adequado.

## <a name="the-specification-pattern"></a>O padrão de especificação

O padrão de especificação (o nome completo é padrão de especificação de consulta) é um padrão de design orientado por domínio projetado para ser o local em que você pode colocar a definição de uma consulta com uma lógica opcional de classificação e paginação.

O padrão de especificação define uma consulta em um objeto. Por exemplo, para encapsular uma consulta paginada que procura por alguns produtos, você poderia criar uma especificação PagedProduct que usasse os parâmetros de entrada necessários (pageNumber, pageSize, filtro, etc.). Então, qualquer método de repositório [geralmente uma sobrecarga List()] aceitaria uma ISpecification e executaria a consulta esperada com base nessa especificação.

Essa abordagem oferece vários benefícios:

* A especificação tem um nome (em vez de apenas um conjunto de expressões LINQ) sobre o qual é possível discutir.

* A especificação pode receber um teste de unidade em isolamento para garantir que ela seja adequada. Ela também poderá ser reutilizada facilmente se você precisar de um comportamento semelhante. Por exemplo, em uma ação de exibição de MVC e em uma ação de API Web, bem como em vários serviços.

* Uma especificação também pode ser usada para descrever a forma dos dados a serem retornados, para que as consultas possam retornar apenas os dados necessários. Isso elimina a necessidade de carregamento lento em aplicativos Web (que geralmente não é uma boa ideia) e ajuda a eliminar a complexidade de detalhamento das implementações do repositório.

Um exemplo de uma interface de especificação genérica é o código a seguir de [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb ).

```csharp
// https://github.com/dotnet-architecture/eShopOnWeb 
public interface ISpecification<T>
{
    Expression<Func<T, bool>> Criteria { get; }
    List<Expression<Func<T, object>>> Includes { get; }
    List<string> IncludeStrings { get; }
}
```

Nas próximas seções, é explicado como implementar o padrão de especificação com o Entity Framework Core 2.0 e como usá-lo de qualquer classe de repositório.

**Observação importante:** o padrão de especificação é um padrão antigo que pode ser implementado de várias maneiras diferentes, como nos seguintes recursos adicionais. Como uma padrão/ideia, é bom conhecer as abordagens mais antigas, mas lembre-se de que as implementações mais antigas não usufruem dos recursos de linguagem modernos, como LINQ e expressões.

## <a name="additional-resources"></a>Recursos adicionais

### <a name="the-repository-pattern"></a>O padrão de repositório

-   **Edward Hieatt e Rob Mee. Padrão de Repositório**
    [*https://martinfowler.com/eaaCatalog/repository.html*](https://martinfowler.com/eaaCatalog/repository.html)

-   **O Padrão de Repositório**
    [*https://msdn.microsoft.com/library/ff649690.aspx*](https://msdn.microsoft.com/library/ff649690.aspx)

-   **Padrão de Repositório: uma abstração da persistência de dados**
    [*http://deviq.com/repository-pattern/*](http://deviq.com/repository-pattern/)

-   **Eric Evans. Domain-Driven Design: Tackling Complexity in the Heart of Software (Design orientado por domínio: lidando com a complexidade no núcleo do software).** (Livro; inclui uma discussão sobre o padrão de Repositório) [*https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

### <a name="unit-of-work-pattern"></a>Padrão de unidade de trabalho

-   **Martin Fowler. Padrão de Unidade de Trabalho.**
    [*https://martinfowler.com/eaaCatalog/unitOfWork.html*](https://martinfowler.com/eaaCatalog/unitOfWork.html)

<!-- -->

-   **Implementando os padrões de repositório e de unidade de trabalho em um aplicativo ASP.NET MVC**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)

### <a name="the-specification-pattern"></a>O padrão de especificação

-   **O Padrão de Especificação.**
    [*http://deviq.com/specification-pattern/*](http://deviq.com/specification-pattern/)

-   **Evans, Eric (2004). Domain Driven Design (Design orientado por domínio). Addison-Wesley. pág. 224.**

-   **Especificações. Martin Fowler**
    [*https://www.martinfowler.com/apsupp/spec.pdf/*](https://www.martinfowler.com/apsupp/spec.pdf)

>[!div class="step-by-step"]
[Anterior] (domain-events-design-implementation.md) [Próximo] (infrastructure-persistence-layer-implemenation-entity-framework-core.md)
