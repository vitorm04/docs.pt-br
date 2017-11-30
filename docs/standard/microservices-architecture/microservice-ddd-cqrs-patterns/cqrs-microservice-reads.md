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
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="6a171-104">Implementando leituras/consultas em um microsserviço CQRS</span><span class="sxs-lookup"><span data-stu-id="6a171-104">Implementing reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="6a171-105">Para leituras/consultas, o ordenação microsserviço do aplicativo de referência eShopOnContainers implementa as consultas independentemente do modelo DDD e área transacional.</span><span class="sxs-lookup"><span data-stu-id="6a171-105">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="6a171-106">Isso foi feito principalmente porque as exigências para consultas e transações são totalmente diferentes.</span><span class="sxs-lookup"><span data-stu-id="6a171-106">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="6a171-107">Gravações executar transações que devem ser compatíveis com a lógica do domínio.</span><span class="sxs-lookup"><span data-stu-id="6a171-107">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="6a171-108">Consultas, por outro lado, são idempotentes e podem ser separadas das regras de domínio.</span><span class="sxs-lookup"><span data-stu-id="6a171-108">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="6a171-109">A abordagem é simple, conforme mostrado na Figura 9-3.</span><span class="sxs-lookup"><span data-stu-id="6a171-109">The approach is simple, as shown in Figure 9-3.</span></span> <span data-ttu-id="6a171-110">A interface de API é implementada pelos controladores de API da Web usando qualquer infraestrutura (por exemplo, um micro ORM como Dapper) e retornando ViewModels dinâmico dependendo das necessidades dos aplicativos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="6a171-110">The API interface is implemented by the Web API controllers using any infrastructure (such as a micro ORM like Dapper) and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![](./media/image3.png)

<span data-ttu-id="6a171-111">**Figura 9-3**.</span><span class="sxs-lookup"><span data-stu-id="6a171-111">**Figure 9-3**.</span></span> <span data-ttu-id="6a171-112">A abordagem mais simples para consultas em um microsserviço CQRS</span><span class="sxs-lookup"><span data-stu-id="6a171-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="6a171-113">Essa é a abordagem mais simples possível para consultas.</span><span class="sxs-lookup"><span data-stu-id="6a171-113">This is the simplest possible approach for queries.</span></span> <span data-ttu-id="6a171-114">As definições de consulta o banco de dados de consulta e retornam um ViewModel dinâmico criado dinamicamente para cada consulta.</span><span class="sxs-lookup"><span data-stu-id="6a171-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="6a171-115">Como as consultas são idempotentes, eles não alterará os dados não importa quantas vezes você executar uma consulta.</span><span class="sxs-lookup"><span data-stu-id="6a171-115">Since the queries are idempotent, they will not change the data no matter how many times you run a query.</span></span> <span data-ttu-id="6a171-116">Portanto, você não precisa ser restrita por qualquer padrão DDD usada no lado do transacional, como agregações e outros padrões, e por consultas são separadas da área de trabalho transacional.</span><span class="sxs-lookup"><span data-stu-id="6a171-116">Therefore, you do not need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="6a171-117">Você simplesmente consulta o banco de dados para os dados que precisa de interface do usuário e retorna um ViewModel dinâmico que não precisam ser estaticamente definidos em qualquer lugar (nenhuma classe ViewModels) exceto nas próprias instruções SQL.</span><span class="sxs-lookup"><span data-stu-id="6a171-117">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="6a171-118">Como essa é uma abordagem simples, o código necessário para o lado de consultas (como o código usando um micro ORM como [Dapper](https://github.com/StackExchange/Dapper)) podem ser implementadas [dentro do mesmo projeto de API da Web](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span><span class="sxs-lookup"><span data-stu-id="6a171-118">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="6a171-119">Figura 9-4 mostra isso.</span><span class="sxs-lookup"><span data-stu-id="6a171-119">Figure 9-4 shows this.</span></span> <span data-ttu-id="6a171-120">As consultas são definidas no **Ordering.API** microsserviço projeto dentro da solução eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="6a171-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![](./media/image4.png)

<span data-ttu-id="6a171-121">**Figura 9-4**.</span><span class="sxs-lookup"><span data-stu-id="6a171-121">**Figure 9-4**.</span></span> <span data-ttu-id="6a171-122">Consultas de microsserviço ordenação em eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="6a171-122">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="6a171-123">Usando ViewModels feito especificamente para aplicativos cliente, independentemente de restrições do modelo de domínio</span><span class="sxs-lookup"><span data-stu-id="6a171-123">Using ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="6a171-124">Como as consultas são executadas para obter os dados necessários para os aplicativos cliente, o tipo retornado pode ser feito especificamente para os clientes, com base nos dados retornados por consultas.</span><span class="sxs-lookup"><span data-stu-id="6a171-124">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="6a171-125">Esses modelos ou dados transferidos DTOs (objetos), são chamados de ViewModels.</span><span class="sxs-lookup"><span data-stu-id="6a171-125">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="6a171-126">Os dados retornados (ViewModel) podem ser o resultado da associação de dados de várias entidades ou tabelas no banco de dados, ou mesmo em várias agregações definidas no modelo de domínio para a área de trabalho transacional.</span><span class="sxs-lookup"><span data-stu-id="6a171-126">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="6a171-127">Nesse caso, porque você está criando consultas independente do modelo de domínio, os limites de agregações e as restrições são ignoradas completamente e você é livre para qualquer tabela e coluna, que talvez seja necessário de consulta.</span><span class="sxs-lookup"><span data-stu-id="6a171-127">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you are free to query any table and column you might need.</span></span> <span data-ttu-id="6a171-128">Essa abordagem fornece grande flexibilidade e a produtividade para os desenvolvedores a criar ou atualizar as consultas.</span><span class="sxs-lookup"><span data-stu-id="6a171-128">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="6a171-129">ViewModels podem ser definidos nas classes de tipos estáticos.</span><span class="sxs-lookup"><span data-stu-id="6a171-129">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="6a171-130">Ou eles podem ser criados dinamicamente com base nas consultas executadas (como é implementado no ordenação microsserviço), que é muito ágil para desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="6a171-130">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="6a171-131">Usando Dapper como um ORM micro para executar consultas</span><span class="sxs-lookup"><span data-stu-id="6a171-131">Using Dapper as a micro ORM to perform queries</span></span> 

<span data-ttu-id="6a171-132">Você pode usar qualquer micro ORM, Entity Framework Core ou até mesmo ADO.NET simples para a consulta.</span><span class="sxs-lookup"><span data-stu-id="6a171-132">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="6a171-133">O aplicativo de exemplo, selecionamos Dapper para o classificação microsserviço em eShopOnContainers como um bom exemplo de um ORM micro popular.</span><span class="sxs-lookup"><span data-stu-id="6a171-133">In the sample application, we selected Dapper for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="6a171-134">Consultas SQL simples pode ser executada com desempenho ótimo, porque é uma estrutura muito leve.</span><span class="sxs-lookup"><span data-stu-id="6a171-134">It can run plain SQL queries with great performance, because it is a very light framework.</span></span> <span data-ttu-id="6a171-135">Usando Dapper, você pode escrever uma consulta SQL que pode acessar e unir várias tabelas.</span><span class="sxs-lookup"><span data-stu-id="6a171-135">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="6a171-136">Dapper é um projeto de código-fonte aberto (criado pelo Sam Saffron original) e faz parte dos blocos de construção usado em [estouro de pilha](https://stackoverflow.com/).</span><span class="sxs-lookup"><span data-stu-id="6a171-136">Dapper is an open source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="6a171-137">Para usar Dapper, basta instalá-lo por meio de [pacote Dapper NuGet](https://www.nuget.org/packages/Dapper), conforme mostrado na figura a seguir.</span><span class="sxs-lookup"><span data-stu-id="6a171-137">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure.</span></span>

![](./media/image5.png)

<span data-ttu-id="6a171-138">Você também precisará adicionar um uso instrução para que seu código tenha acesso aos métodos de extensão Dapper.</span><span class="sxs-lookup"><span data-stu-id="6a171-138">You will also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="6a171-139">Quando você usa Dapper em seu código, usar diretamente a classe SqlClient disponível no namespace do SqlClient.</span><span class="sxs-lookup"><span data-stu-id="6a171-139">When you use Dapper in your code, you directly use the SqlClient class available in the System.Data.SqlClient namespace.</span></span> <span data-ttu-id="6a171-140">Por meio do método QueryAsync e outros métodos de extensão que estendem a classe SqlClient, você pode simplesmente executar consultas de maneira simples e de alto desempenho.</span><span class="sxs-lookup"><span data-stu-id="6a171-140">Through the QueryAsync method and other extension methods which extend the SqlClient class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-and-static-viewmodels"></a><span data-ttu-id="6a171-141">ViewModels dinâmico e estático</span><span class="sxs-lookup"><span data-stu-id="6a171-141">Dynamic and static ViewModels</span></span>

<span data-ttu-id="6a171-142">Conforme mostrado no código a seguir de microsserviço a ordenação, a maioria dos ViewModels retornados por consultas é implementada como *dinâmico*.</span><span class="sxs-lookup"><span data-stu-id="6a171-142">As shown in the following code from the ordering microservice, most of the ViewModels returned by the queries are implemented as *dynamic*.</span></span> <span data-ttu-id="6a171-143">Isso significa que o subconjunto de atributos a serem retornados é baseado na própria consulta.</span><span class="sxs-lookup"><span data-stu-id="6a171-143">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="6a171-144">Se você adicionar uma nova coluna na consulta ou uma junção, que dados são adicionados dinamicamente ao ViewModel retornado.</span><span class="sxs-lookup"><span data-stu-id="6a171-144">If you add a new column to the query or join, that data is dynamically added to the returned ViewModel.</span></span> <span data-ttu-id="6a171-145">Essa abordagem reduz a necessidade de modificar consultas em resposta a atualizações para o modelo de dados subjacente, tornando essa abordagem de design mais flexíveis e tolerante a falhas de alterações futuras.</span><span class="sxs-lookup"><span data-stu-id="6a171-145">This approach reduces the need to modify queries in response to updates to the underlying data model, making this design approach more flexible and tolerant of future changes.</span></span>

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

<span data-ttu-id="6a171-146">O ponto importante é que ao usar um tipo dinâmico, a coleção retornada de dados será ser montada dinamicamente como ViewModel.</span><span class="sxs-lookup"><span data-stu-id="6a171-146">The important point is that by using a dynamic type, the returned collection of data will be dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="6a171-147">Para a maioria das consultas, você não precisa Predefinir uma classe DTO ou ViewModel, o que torna a codificação-las simples e produtiva.</span><span class="sxs-lookup"><span data-stu-id="6a171-147">For most queries, you do not need to predefine a DTO or ViewModel class, which makes coding them straightforward and productive.</span></span> <span data-ttu-id="6a171-148">No entanto, você pode predefinir ViewModels (como DTOs predefinidos) se quiser ter ViewModels com uma definição mais restrita como contratos.</span><span class="sxs-lookup"><span data-stu-id="6a171-148">However, you can predefine ViewModels (like predefined DTOs) if you want to have ViewModels with a more restricted definition as contracts.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="6a171-149">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="6a171-149">Additional resources</span></span>

-   <span data-ttu-id="6a171-150">**Dapper**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span><span class="sxs-lookup"><span data-stu-id="6a171-150">**Dapper**
[*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span></span>

-   <span data-ttu-id="6a171-151">**Julie Lerman. Pontos de dados - Dapper, Entity Framework e aplicativos híbridos (artigo do MSDN Mag.)**</span><span class="sxs-lookup"><span data-stu-id="6a171-151">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN Mag. article)**</span></span>

    <span data-ttu-id="6a171-152">*https://msdn.microsoft.com/en-US/Magazine/mt703432.aspx*</span><span class="sxs-lookup"><span data-stu-id="6a171-152">*https://msdn.microsoft.com/en-us/magazine/mt703432.aspx*</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="6a171-153">[Anterior] (eshoponcontainers-cqrs-ddd-microservice.md) [Avançar] (ddd-orientado-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="6a171-153">[Previous] (eshoponcontainers-cqrs-ddd-microservice.md) [Next] (ddd-oriented-microservice.md)</span></span>
