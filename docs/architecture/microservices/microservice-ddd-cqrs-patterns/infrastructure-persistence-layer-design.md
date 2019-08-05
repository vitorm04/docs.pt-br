---
title: Projetando a camada de persistência da infraestrutura
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Explore o padrão de repositório no design da camada de persistência da infraestrutura.
ms.date: 10/08/2018
ms.openlocfilehash: 76f545403a1b595ce7a541a96d212b9406d89c10
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/30/2019
ms.locfileid: "68674113"
---
# <a name="design-the-infrastructure-persistence-layer"></a>Projetar a camada de persistência da infraestrutura

Os componentes de persistência de dados fornecem acesso aos dados hospedados dentro dos limites de um microsserviço (ou seja, em um banco de dados de microsserviço). Eles contêm a implementação real dos componentes, como repositórios e classes [Unidade de Trabalho](https://martinfowler.com/eaaCatalog/unitOfWork.html), como objetos <xref:Microsoft.EntityFrameworkCore.DbContext> personalizados do EF (Entity Framework). O DbContext do EF implementa os padrões de Repositório e de Unidade de Trabalho.

## <a name="the-repository-pattern"></a>O padrão de repositório

Repositórios são classes ou componentes que encapsulam a lógica necessária para acessar fontes de dados. Eles centralizam a funcionalidade comum de acesso a dados, melhorando a sustentabilidade e desacoplando a infraestrutura ou a tecnologia usada para acessar os bancos de dados da camada do modelo de domínio. Se você usar um ORM (Mapeador Objeto-Relacional) como o Entity Framework, o código que precisa ser implementado será simplificado, graças à LINQ e à tipagem forte. Isso permite que você se concentre na lógica de persistência de dados e não nos detalhes técnicos do acesso a dados.

O padrão de repositório é uma maneira bem documentada de trabalhar com uma fonte de dados. No livro [Padrões de Arquitetura de Aplicações Corporativas](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/), Martin Fowler descreve um repositório da seguinte maneira:

> Um repositório executa as tarefas de um intermediário entre as camadas de modelo de domínio e o mapeamento de dados, funcionando de maneira semelhante a um conjunto de objetos de domínio na memória. Os objetos de clientes criam consultas de forma declarativa e enviam-nas para os repositórios buscando respostas. Conceitualmente, um repositório encapsula um conjunto de objetos armazenados no banco de dados e as operações que podem ser executadas neles, fornecendo uma maneira que é mais próxima da camada de persistência. Os repositórios também oferecem a capacidade de separação, de forma clara e em uma única direção, a dependência entre o domínio de trabalho e a alocação de dados ou o mapeamento.

### <a name="define-one-repository-per-aggregate"></a>Definir um repositório por agregação

Para cada agregação ou raiz de agregação, você deve criar uma classe de repositório. Em um microsserviço baseado nos padrões de DDD (Design Orientado por Domínio), o único canal que você deve usar para atualizar o banco de dados são os repositórios. O motivo é que eles têm uma relação um-para-um com a raiz de agregação, que controla as invariáveis e a consistência transacional da agregação. É possível consultar o banco de dados por outros canais (como ao seguir uma abordagem de CQRS), porque as consultas não alteram o estado do banco de dados. No entanto, a área transacional (ou seja, as atualizações) sempre precisa ser controlada pelos repositórios e pelas raízes de agregação.

Basicamente, um repositório permite popular na memória dados que são provenientes do banco de dados, em forma de entidades de domínio. Depois que as entidades estão na memória, elas podem ser alteradas e persistidas novamente no banco de dados por meio de transações.

Conforme observado anteriormente, se você estiver usando o padrão de arquitetura CQS/CQRS, as consultas inicias serão executadas por consultas à parte, fora do modelo de domínio, executadas por instruções SQL simples usando o Dapper. Essa abordagem é muito mais flexível do que os repositórios porque você pode consultar e unir as tabelas necessárias, e essas consultas não são restringidas pelas regras das agregações. Esses dados vão para o aplicativo cliente ou de camada de apresentação.

Se o usuário fizer alterações, os dados a serem atualizados virão da camada de apresentação ou do aplicativo cliente para a camada do aplicativo (como um serviço de API Web). Ao receber um comando em um manipulador de comandos, use repositórios para obter os dados que deseja atualizar do banco de dados. Você os atualizará na memória com os dados transmitidos com os comandos e, em seguida, adicionará ou atualizará esses dados (entidades de domínio) no banco de dados por meio de uma transação.

É importante enfatizar novamente que você deve definir apenas um repositório para cada raiz de agregação, conforme mostrado na Figura 7-17. Para atingir a meta da raiz de agregação de manter a consistência transacional entre todos os objetos na agregação, você nunca deve criar um repositório para cada tabela no banco de dados.

![Relações entre as camadas de domínio e de infraestrutura: A Agregação de Comprador depende de IBuyerRepository e a Agregação de Pedido depende das interfaces IOrderRepository; essas interfaces são implementadas na camada de infraestrutura pelos repositórios correspondentes que dependem de UnitOfWork, também implementados nela, que acessam as tabelas na camada de dados.](./media/image18.png)

**Figura 7-17**. A relação entre repositórios, agregações e tabelas de banco de dados

### <a name="enforce-one-aggregate-root-per-repository"></a>Impor uma raiz de agregação por repositório

É importante implementar o design do repositório de uma forma que ele imponha a regra de que apenas as raízes de agregação devem ter repositórios. Você pode criar um tipo de repositório genérico ou de base que restrinja o tipo de entidades com as quais trabalha para garantir que elas tenham a interface de marcador `IAggregateRoot`.

Assim, cada classe de repositório implementada na camada de infraestrutura implementa seu próprio contrato ou interface, conforme é mostrado no código a seguir:

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
      // ...
    }
}
```

Cada interface de repositório específica implementa a interface IRepository genérica:

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

No entanto, uma maneira melhor de fazer com que o código imponha a convenção de que cada repositório seja relacionado a uma única agregação é implementar um tipo de repositório genérico. Dessa forma, é obrigatório que você esteja usando um repositório para direcionar a uma agregação específica. Isso pode ser feito facilmente com a implementação de uma interface base `IRepository` genérica, como no código a seguir:

```csharp
public interface IRepository<T> where T : IAggregateRoot
{
    //....
}
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a>O padrão de repositório facilita os testes da lógica do aplicativo

O padrão de repositório permite testar facilmente o aplicativo com testes de unidade. Lembre-se de que os testes de unidade testam apenas o código, não a infraestrutura, assim, as abstrações de repositório facilitam alcançar essa meta.

Como observado em uma seção anterior, é recomendado que você defina e coloque as interfaces de repositório na camada de modelo de domínio para que a camada de aplicativo, como o microsserviço API Web, não dependa diretamente da camada de infraestrutura em que as classes de repositório reais foram implementadas. Fazendo isso e usando a injeção de dependência nos controladores da API Web, você pode implementar repositórios fictícios que retornam dados falsos em vez de dados do banco de dados. Essa abordagem desacoplada permite que você crie e execute testes de unidade que se focam na lógica do aplicativo sem precisar de conectividade com o banco de dados.

As conexões com bancos de dados podem falhar e, principalmente, executar centenas de testes em relação a um banco de dados é prejudicial por dois motivos. Primeiro, pode demorar muito devido ao grande número de testes. Segundo, os registros do banco de dados podem ser alterados e afetar os resultados dos testes, deixando-os inconsistentes. Testar em relação ao banco de dados não é um teste de unidade, mas sim um teste de integração. É interessante ter muitos testes de unidade em execução rápida, mas menos testes de integração em relação aos bancos de dados.

Em termos de separação de interesses para os testes de unidade, a lógica opera em entidades de domínio na memória. Ela considera que a classe de repositório as entregou. Depois que a lógica modifica as entidades de domínio, ela considera que a classe de repositório as armazenará corretamente. O ponto importante aqui é criar testes de unidade em relação ao seu modelo de domínio e à sua lógica de domínio. As raízes de agregação são os limites de consistência principais em DDD.

Os repositórios implementados no eShopOnContainers dependem da implementação do DbContext do EF Core dos padrões Repositório e Unidade de Trabalho usando seu rastreador de alteração, portanto, eles não duplicam essa funcionalidade.

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a>A diferença entre o padrão de repositório e o padrão da classe DAL (classe de acesso a dados) herdada

Um objeto de acesso a dados executa operações de acesso e persistência de dados diretamente no armazenamento. Um repositório marca os dados com as operações que você deseja executar na memória de um objeto de unidade de trabalho (como no EF ao usar a classe <xref:Microsoft.EntityFrameworkCore.DbContext>), mas essas atualizações não são realizadas imediatamente no banco de dados.

Uma unidade de trabalho é conhecida como uma única transação que envolve várias operações de inserção, atualização ou exclusão. Simplificando, isso significa que, para uma ação de usuário específica, como o registro em um site, as operações de inserção, atualização e exclusão são tratadas em uma única transação. Isso é mais eficiente do que tratar várias transações de banco de dados de uma maneira mais intensa.

Essas várias operações de persistência serão executadas mais tarde em uma única ação quando o código da camada de aplicativo executar um comando para isso. A decisão de como aplicar as alterações realizadas na memória ao armazenamento de banco de dados real geralmente se baseia no [padrão de unidade de trabalho](https://martinfowler.com/eaaCatalog/unitOfWork.html). No EF, o padrão de Unidade de Trabalho é implementado como o <xref:Microsoft.EntityFrameworkCore.DbContext>.

Em muitos casos, esse padrão ou uma maneira de aplicar operações em relação ao armazenamento pode aumentar o desempenho do aplicativo e reduzir a possibilidade de inconsistências. Além disso, ele reduz o bloqueio de transações nas tabelas do banco de dados, porque todas as operações pretendidas são confirmadas em uma única transação. Isso é mais eficiente em comparação com a execução de muitas operações isoladas no banco de dados. Portanto, o ORM selecionado é capaz de otimizar a execução no banco de dados agrupando várias ações de atualização na mesma transação, em vez de executar várias transações pequenas e separadas.

### <a name="repositories-shouldnt-be-mandatory"></a>Os repositórios não são obrigatórios

Os repositórios personalizados são úteis pelos motivos já citados e essa é a abordagem para o microsserviço de pedidos no eShopOnContainers. No entanto, esse não é um padrão essencial a ser implementado em um design DDD ou até mesmo no desenvolvimento para .NET, em geral.

Por exemplo, Jimmy Bogard, ao fornecer comentários diretos para este guia, diz o seguinte:

> Esse provavelmente será meu maior comentário. Eu realmente não sou fã de repositórios, principalmente porque eles ocultam detalhes importantes do mecanismo de persistência subjacente. É por isso que eu também opto pelo MediatR para comandos. Posso usar toda a capacidade da camada de persistência e enviar por push todo esse comportamento de domínio para minhas raízes de agregação. Geralmente, eu não gosto de usar repositórios fictícios, ou seja, eu ainda preciso aplicar esse teste de integração na situação real. Optar por CQRS significa que realmente não precisamos mais de repositórios.

Os repositórios podem ser úteis, mas eles não são críticos para o design DDD como são o padrão de Agregação e o modelo de domínio avançado. Portanto, use o padrão de repositório ou não, conforme achar mais adequado. De qualquer forma, você usará o padrão de repositório sempre que usar o EF Core, embora, nesse caso, o repositório aborde todo o contexto de microsserviço ou limitado.

## <a name="additional-resources"></a>Recursos adicionais

### <a name="repository-pattern"></a>Padrão de Repositório

- **O Padrão de Repositório** \
  <https://deviq.com/repository-pattern/>

- **Edward Hieatt e Rob Mee. Padrão de Repositório.** \
  <https://martinfowler.com/eaaCatalog/repository.html>

- **O Padrão de Repositório** \
  <https://docs.microsoft.com/previous-versions/msp-n-p/ff649690(v=pandp.10)>

- **Eric Evans. Design orientado por domínio: Lidando com a complexidade no núcleo do software.** (Livro; inclui uma discussão sobre o padrão de Repositório) \
  <https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/>

### <a name="unit-of-work-pattern"></a>Padrão de unidade de trabalho

- **Martin Fowler. Padrão de Unidade de Trabalho.** \
  <https://martinfowler.com/eaaCatalog/unitOfWork.html>

- **Implementando os padrões de repositório e de unidade de trabalho em um aplicativo ASP.NET MVC** \
  <https://docs.microsoft.com/aspnet/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

>[!div class="step-by-step"]
>[Anterior](domain-events-design-implementation.md)
>[Próximo](infrastructure-persistence-layer-implemenation-entity-framework-core.md)
