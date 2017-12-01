---
title: "Implementando leituras/consultas em um microsserviço CQRS"
description: "Arquitetura de Microservices .NET para aplicativos .NET em contêineres | Implementando leituras/consultas em um microsserviço CQRS"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: e017aaaa701d8033110be8d6244d3e1120fc4fd9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a>Implementando leituras/consultas em um microsserviço CQRS

Para leituras/consultas, o ordenação microsserviço do aplicativo de referência eShopOnContainers implementa as consultas independentemente do modelo DDD e área transacional. Isso foi feito principalmente porque as exigências para consultas e transações são totalmente diferentes. Gravações executar transações que devem ser compatíveis com a lógica do domínio. Consultas, por outro lado, são idempotentes e podem ser separadas das regras de domínio.

A abordagem é simple, conforme mostrado na Figura 9-3. A interface de API é implementada pelos controladores de API da Web usando qualquer infraestrutura (por exemplo, um micro ORM como Dapper) e retornando ViewModels dinâmico dependendo das necessidades dos aplicativos de interface do usuário.

![](./media/image3.png)

**Figura 9-3**. A abordagem mais simples para consultas em um microsserviço CQRS

Essa é a abordagem mais simples possível para consultas. As definições de consulta o banco de dados de consulta e retornam um ViewModel dinâmico criado dinamicamente para cada consulta. Como as consultas são idempotentes, eles não alterará os dados não importa quantas vezes você executar uma consulta. Portanto, você não precisa ser restrita por qualquer padrão DDD usada no lado do transacional, como agregações e outros padrões, e por consultas são separadas da área de trabalho transacional. Você simplesmente consulta o banco de dados para os dados que precisa de interface do usuário e retorna um ViewModel dinâmico que não precisam ser estaticamente definidos em qualquer lugar (nenhuma classe ViewModels) exceto nas próprias instruções SQL.

Como essa é uma abordagem simples, o código necessário para o lado de consultas (como o código usando um micro ORM como [Dapper](https://github.com/StackExchange/Dapper)) podem ser implementadas [dentro do mesmo projeto de API da Web](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs). Figura 9-4 mostra isso. As consultas são definidas no **Ordering.API** microsserviço projeto dentro da solução eShopOnContainers.

![](./media/image4.png)

**Figura 9-4**. Consultas de microsserviço ordenação em eShopOnContainers

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>Usando ViewModels feito especificamente para aplicativos cliente, independentemente de restrições do modelo de domínio

Como as consultas são executadas para obter os dados necessários para os aplicativos cliente, o tipo retornado pode ser feito especificamente para os clientes, com base nos dados retornados por consultas. Esses modelos ou dados transferidos DTOs (objetos), são chamados de ViewModels.

Os dados retornados (ViewModel) podem ser o resultado da associação de dados de várias entidades ou tabelas no banco de dados, ou mesmo em várias agregações definidas no modelo de domínio para a área de trabalho transacional. Nesse caso, porque você está criando consultas independente do modelo de domínio, os limites de agregações e as restrições são ignoradas completamente e você é livre para qualquer tabela e coluna, que talvez seja necessário de consulta. Essa abordagem fornece grande flexibilidade e a produtividade para os desenvolvedores a criar ou atualizar as consultas.

ViewModels podem ser definidos nas classes de tipos estáticos. Ou eles podem ser criados dinamicamente com base nas consultas executadas (como é implementado no ordenação microsserviço), que é muito ágil para desenvolvedores.

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a>Usando Dapper como um ORM micro para executar consultas 

Você pode usar qualquer micro ORM, Entity Framework Core ou até mesmo ADO.NET simples para a consulta. O aplicativo de exemplo, selecionamos Dapper para o classificação microsserviço em eShopOnContainers como um bom exemplo de um ORM micro popular. Consultas SQL simples pode ser executada com desempenho ótimo, porque é uma estrutura muito leve. Usando Dapper, você pode escrever uma consulta SQL que pode acessar e unir várias tabelas.

Dapper é um projeto de código-fonte aberto (criado pelo Sam Saffron original) e faz parte dos blocos de construção usado em [estouro de pilha](https://stackoverflow.com/). Para usar Dapper, basta instalá-lo por meio de [pacote Dapper NuGet](https://www.nuget.org/packages/Dapper), conforme mostrado na figura a seguir.

![](./media/image5.png)

Você também precisará adicionar um uso instrução para que seu código tenha acesso aos métodos de extensão Dapper.

Quando você usa Dapper em seu código, usar diretamente a classe SqlClient disponível no namespace do SqlClient. Por meio do método QueryAsync e outros métodos de extensão que estendem a classe SqlClient, você pode simplesmente executar consultas de maneira simples e de alto desempenho.

## <a name="dynamic-and-static-viewmodels"></a>ViewModels dinâmico e estático

Conforme mostrado no código a seguir de microsserviço a ordenação, a maioria dos ViewModels retornados por consultas é implementada como *dinâmico*. Isso significa que o subconjunto de atributos a serem retornados é baseado na própria consulta. Se você adicionar uma nova coluna na consulta ou uma junção, que dados são adicionados dinamicamente ao ViewModel retornado. Essa abordagem reduz a necessidade de modificar consultas em resposta a atualizações para o modelo de dados subjacente, tornando essa abordagem de design mais flexíveis e tolerante a falhas de alterações futuras.

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
    public async Task<IEnumerable<dynamic>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            return await connection.QueryAsync<dynamic>(
@"SELECT o.[Id] as ordernumber,
o.[OrderDate] as [date],os.[Name] as [status],
SUM(oi.units*oi.unitprice) as total
FROM [ordering].[Orders] o
LEFT JOIN[ordering].[orderitems] oi ON o.Id = oi.orderid
LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
GROUP BY o.[Id], o.[OrderDate], os.[Name]");
        }
  }
}
```

O ponto importante é que ao usar um tipo dinâmico, a coleção retornada de dados será ser montada dinamicamente como ViewModel.

Para a maioria das consultas, você não precisa Predefinir uma classe DTO ou ViewModel, o que torna a codificação-las simples e produtiva. No entanto, você pode predefinir ViewModels (como DTOs predefinidos) se quiser ter ViewModels com uma definição mais restrita como contratos.

#### <a name="additional-resources"></a>Recursos adicionais

-   **Dapper**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)

-   **Julie Lerman. Pontos de dados - Dapper, Entity Framework e aplicativos híbridos (artigo do MSDN Mag.)**

    *https://msdn.microsoft.com/en-US/Magazine/mt703432.aspx*


>[!div class="step-by-step"]
[Anterior] (eshoponcontainers-cqrs-ddd-microservice.md) [Avançar] (ddd-orientado-microservice.md)
