---
title: "Criando a camada de persistência de infraestrutura"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Criando a camada de persistência de infraestrutura"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: ce0f1d608eed909a7707f3c580afc5253f3eef06
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="designing-the-infrastructure-persistence-layer"></a>Criando a camada de persistência de infraestrutura

Componentes de persistência de dados fornecem acesso aos dados hospedados dentro dos limites de um microsserviço (ou seja, banco de dados do microsserviço). Eles contêm a implementação real de componentes, como repositórios e [unidade de trabalho](http://martinfowler.com/eaaCatalog/unitOfWork.html) classes, como DBContexts de EF personalizado.

## <a name="the-repository-pattern"></a>O padrão de repositório

Repositórios são classes ou componentes que encapsulam a lógica necessária para acessar fontes de dados. Centralizar a funcionalidade comum de acesso de dados, fornecendo melhor sustentabilidade e desacoplamento de infraestrutura ou a tecnologia usada para acessar bancos de dados da camada de modelo de domínio. Se você usar um ORM como Entity Framework, o código que deve ser implementado é simplificado, graças ao LINQ e tipagem forte. Isso permite que você se concentre na lógica de persistência de dados em vez de em dados acessar detalhes técnicos.

O padrão de repositório é uma maneira bem documentada de trabalhar com uma fonte de dados. No catálogo de [padrões de arquitetura de aplicativo empresarial](https://www.amazon.com/Patterns-Enterprise-Application-Architecture-Martin/dp/0321127420/), Martin Fowler descreve um repositório da seguinte maneira:

Um repositório executa as tarefas de um intermediário entre as camadas de modelo de domínio e o mapeamento de dados, funciona de maneira semelhante a um conjunto de objetos de domínio na memória. Objetos de cliente declarativamente criar consultas e enviá-los para os repositórios para respostas. Conceitualmente, um repositório encapsula um conjunto de objetos armazenados no banco de dados e operações que podem ser executadas neles, fornecendo uma maneira mais próxima camada de persistência. Repositórios, também, suportam para a finalidade de separação, claramente e em uma única direção, a dependência entre o domínio de trabalho e a alocação de dados ou de mapeamento.

### <a name="define-one-repository-per-aggregate"></a>Definir um repositório por agregação

Para cada raiz de agregação ou de agregação, você deve criar uma classe de repositório. Em um microsserviço com base nos padrões de design controlado por domínio, o único canal que você deve usar para atualizar o banco de dados deve ser os repositórios. Isso ocorre porque eles têm uma relação um para um com a raiz de agregação, que controla a agregação invariáveis e consistência transacional. É okey consultar o banco de dados por meio de outros canais (como você pode fazer seguindo uma abordagem CQRS), porque as consultas não altera o estado do banco de dados. No entanto, a área transacional, as atualizações — sempre devem ser controladas pelos repositórios e as raízes de agregação.

Basicamente, um repositório permite que você popular os dados na memória vem do banco de dados na forma de entidades de domínio. Depois que as entidades estão na memória, eles podem ser alterados e persistidos no banco de dados através de transações.

Conforme observado anteriormente, se você estiver usando o padrão de arquitetura CQS/CQRS, as consultas inicias serão executadas por consultas de lado fora do modelo de domínio, executada por instruções SQL simples usando Dapper. Essa abordagem é muito mais flexível que repositórios porque você pode consultar e unir tabelas que você precisa, e essas consultas não estão restrito por regras de agregações. Esses dados para ir para o aplicativo cliente ou de camada de apresentação.

Se o usuário fizer alterações, os dados a serem atualizadas virão da camada de aplicativo ou apresentação de cliente para a camada de aplicativo (como um serviço de API da Web). Quando você receber um comando (com dados) em um manipulador de comando, use repositórios para obter os dados que você deseja atualizar a partir do banco de dados. Atualizá-la na memória com as informações transmitidas com os comandos e, em seguida, adicionar ou atualizar os dados (entidades de domínio) no banco de dados por meio de uma transação.

Podemos deve enfatizar novamente que apenas um repositório deve ser definido para cada raiz de agregação, conforme mostrado na Figura 9-17. Para atingir a meta da raiz agregada para manter a consistência transacional entre todos os objetos de agregação, você nunca deve criar um repositório para cada tabela no banco de dados.

![](./media/image18.png)

**Figura 9-17**. A relação entre repositórios, agregações e tabelas de banco de dados

### <a name="enforcing-one-aggregate-root-per-repository"></a>Aplicando uma raiz de agregação por repositório

É importante para implementar o design do repositório de forma que ele aplica a regra que apenas as raízes de agregação devem ter repositórios. Você pode criar um tipo genérico ou base de repositório que restringe o tipo de entidades que ele funciona com para garantir que eles têm a interface de marcador IAggregateRoot.

Assim, cada classe de repositório implementada na camada de infraestrutura implementa seu próprio contrato ou interface, conforme mostrado no código a seguir:

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class OrderRepository : IOrderRepository
    {
```

Cada interface do repositório específico implementa a interface do IRepository genérica:

```csharp
public interface IOrderRepository : IRepository<Order>
{
    Order Add(Order order);
    // ...
}
```

No entanto, uma maneira melhor de ter o código de impor a convenção de que cada repositório deve estar relacionado a uma única agregação seria implementar um tipo de repositório genérico é explícita que você está usando um repositório para o destino de uma agregação específica. Isso pode ser feito facilmente com a implementação desse genérico na interface base IRepository, como no código a seguir:

```csharp
  public interface IRepository<T> where T : IAggregateRoot
```

### <a name="the-repository-pattern-makes-it-easier-to-test-your-application-logic"></a>O padrão de repositório torna mais fácil de testar a lógica do aplicativo

O padrão de repositório permite que você teste seu aplicativo com testes de unidade. Lembre-se de que testes de unidade apenas testem seu código, não na infraestrutura, portanto as abstrações de repositório facilitam alcançar essa meta.

Como observado em uma seção anterior, é recomendável que você defina e coloque as interfaces de repositório na camada de modelo de domínio para a camada de aplicativo (por exemplo, o microsserviço API da Web) não depende diretamente a camada de infraestrutura em que as classes de repositório real foi implementado. Fazer isso e usando a injeção de dependência nos controladores de sua API da Web, você pode implementar repositórios fictícios que retornam dados falsos em vez de dados do banco de dados. Se a abordagem desacoplado permite que você crie e testes de unidade de execução que podem testar apenas a lógica do seu aplicativo sem a necessidade de conectividade com o banco de dados.

Conexões com bancos de dados podem falhar e, mais importante, que executam centenas de testes em relação a um banco de dados é inválido por dois motivos. Primeiro, pode levar muito tempo devido ao grande número de testes. Segundo, os registros do banco de dados podem alterar e afetar os resultados de seus testes, para que eles não podem ser consistentes. No banco de dados de teste não é uma unidade de testes, mas uma integração de teste. Você deve ter muitos testes de unidade em execução rápida, mas menos integração testes nos bancos de dados.

Em termos de separação de preocupações para testes de unidade, sua lógica opera em entidades de domínio na memória. Ele pressupõe que a classe de repositório foi entregue aqueles. Depois que a lógica modifica as entidades de domínio, ele pressupõe que a classe de repositório será armazená-los corretamente. O ponto importante aqui é criar testes de unidade em relação a seu modelo de domínio e a lógica do domínio. Raízes agregadas são os limites de consistência principal no DDD.

### <a name="the-difference-between-the-repository-pattern-and-the-legacy-data-access-class-dal-class-pattern"></a>A diferença entre o padrão de repositório e o padrão de classe (classe DAL) de acesso a dados herdado

Um objeto de acesso de dados diretamente executa operações de acesso e persistência de dados em relação ao armazenamento. Marcas de repositório de dados com as operações que você deseja executar na memória de uma unidade de objeto de trabalho (como EF ao usar o DbContext), mas essas atualizações não serão executados imediatamente.

Uma unidade de trabalho é conhecida como uma única transação que envolve vários inserir, atualizar ou excluir operações. Em termos simples, isso significa que, para uma ação do usuário específico (por exemplo, o registro em um site), o insert, update e delete transações são tratadas em uma única transação. Isso é mais eficiente do que o tratamento de várias transações de banco de dados de uma maneira chattier.

Essas várias operações de persistência serão executadas mais tarde em uma única ação quando o código da camada de aplicativo comandos a ele. A decisão sobre como aplicar as alterações na memória para o armazenamento de banco de dados real geralmente se baseia o [padrão de unidade de trabalho](http://martinfowler.com/eaaCatalog/unitOfWork.html). EF, o padrão de unidade de trabalho é implementado como o DBContext.

Em muitos casos, esse padrão ou uma maneira de aplicar operações contra o armazenamento pode aumentar o desempenho do aplicativo e reduzir a possibilidade de inconsistências. Além disso, ele reduz transação bloqueando nas tabelas do banco de dados, porque todas as operações pretendidas confirmadas como parte de uma transação. Isso é mais eficiente em comparação com a execução de muitas operações isoladas no banco de dados. Portanto, o ORM selecionado poderá otimizar a execução no banco de dados agrupando várias ações de atualização de dentro da mesma transação, em vez de execuções de muitas transações pequenas e separado.

### <a name="repositories-should-not-be-mandatory"></a>Repositórios não devem ser obrigatórios

Os repositórios personalizados são úteis para motivos citados anteriormente e que é a abordagem para o pedido microsserviço em eShopOnContainers. No entanto, não é um padrão essencial para implementar um design de DDD ou até mesmo em geral de desenvolvimento no .NET.

Por exemplo, Jimmy Bogard, ao fornecer feedback direto para este guia, diz o seguinte:

Isso provavelmente será meu comentário maior. Realmente não tenho um ventilador de repositórios, principalmente porque eles ocultem detalhes importantes do mecanismo de persistência subjacente. É por que posso ir para MediatR para comandos, muito. Posso usar toda a capacidade da camada de persistência e enviar por push a todas as esse comportamento de domínio raízes agregadas. Geralmente não quiser simule Meus repositórios – preciso ter se essa integração com teste com a situação real. Vai CQRS significava que não temos realmente a necessidade de repositórios mais.

Encontramos repositórios útil, mas podemos confirmar que não são essenciais para sua DDD, de forma que a agregação padrão e o modelo de domínio avançado. Portanto, use o padrão de repositório ou não, como você pode ver se ajustar.

#### <a name="additional-resources"></a>Recursos adicionais

##### <a name="the-repository-pattern"></a>O padrão de repositório

-   **Edward Hieatt e Rob me. Padrão de repositório. ** 
     [ *http://martinfowler.com/eaaCatalog/repository.html*](http://martinfowler.com/eaaCatalog/repository.html)

-   **O padrão de repositório**
    [*https://msdn.microsoft.com/en-us/library/ff649690.aspx*](https://msdn.microsoft.com/en-us/library/ff649690.aspx)

-   **Repositório padrão: Uma persistência abstração de dados**
    [*http://deviq.com/repository-pattern/*](http://deviq.com/repository-pattern/)

-   **Eric Evans. Design controlado por domínio: Lidar com a complexidade do Centro de Software.** (Livro; inclui uma discussão sobre o padrão de repositório) [ *https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/*](https://www.amazon.com/Domain-Driven-Design-Tackling-Complexity-Software/dp/0321125215/)

##### <a name="unit-of-work-pattern"></a>Unidade de padrão de trabalho

-   **Martin Fowler. Unidade de padrão de trabalho. ** 
     [ *http://martinfowler.com/eaaCatalog/unitOfWork.html*](http://martinfowler.com/eaaCatalog/unitOfWork.html)

<!-- -->

-   **Implementando o repositório e a unidade de trabalho padrões em um aplicativo ASP.NET MVC**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/ Implementing-the-Repository-and-Unit-of-Work-Patterns-in-an-ASP-NET-MVC-Application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)


>[!div class="step-by-step"]
[Anterior] (domínio-eventos-design-implementation.md) [Avançar] (infrastructure-persistence-layer-implemenation-entity-framework-core.md)
