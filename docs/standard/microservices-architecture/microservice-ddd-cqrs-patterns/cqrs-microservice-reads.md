---
title: "Implementando leituras/consultas em um microsserviço CQRS"
description: "Arquitetura de microsserviços .NET para aplicativos .NET em contêineres | Implementando leituras/consultas em um microsserviço CQRS"
keywords: "Docker, Microsserviços, ASP.NET, Contêiner"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/02/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ca9bcefb317d2b3c7c225b773918ca4a2484cb8f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="2d557-104">Implementando leituras/consultas em um microsserviço CQRS</span><span class="sxs-lookup"><span data-stu-id="2d557-104">Implementing reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="2d557-105">Para leituras/consultas, o microsserviço de ordenação do aplicativo de referência eShopOnContainers implementa as consultas independentemente do modelo DDD e da área transacional.</span><span class="sxs-lookup"><span data-stu-id="2d557-105">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="2d557-106">Isso foi feito principalmente porque as exigências para consultas e transações são totalmente diferentes.</span><span class="sxs-lookup"><span data-stu-id="2d557-106">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="2d557-107">Grava transações de execução que devem estar em conformidade com a lógica do domínio.</span><span class="sxs-lookup"><span data-stu-id="2d557-107">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="2d557-108">Consultas, por outro lado, são idempotentes e podem ser separadas das regras de domínio.</span><span class="sxs-lookup"><span data-stu-id="2d557-108">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="2d557-109">A abordagem é simples, conforme mostra a Figura 9-3.</span><span class="sxs-lookup"><span data-stu-id="2d557-109">The approach is simple, as shown in Figure 9-3.</span></span> <span data-ttu-id="2d557-110">A interface de API é implementada pelos controladores de API da Web usando qualquer infraestrutura, como um micro ORM (Mapeador Relacional de Objeto) como Dapper e retornando ViewModels dinâmicos dependendo das necessidades dos aplicativos de interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="2d557-110">The API interface is implemented by the Web API controllers using any infrastructure, such as a micro Object Relational Mapper (ORM) like Dapper, and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![](./media/image3.png)

<span data-ttu-id="2d557-111">**Figura 9-3**.</span><span class="sxs-lookup"><span data-stu-id="2d557-111">**Figure 9-3**.</span></span> <span data-ttu-id="2d557-112">A abordagem mais simples para consultas em um microsserviço CQRS</span><span class="sxs-lookup"><span data-stu-id="2d557-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="2d557-113">Essa é a abordagem mais simples possível para consultas.</span><span class="sxs-lookup"><span data-stu-id="2d557-113">This is the simplest possible approach for queries.</span></span> <span data-ttu-id="2d557-114">As definições de consulta consultam o banco de dados e retornam um ViewModel dinâmico criado dinamicamente para cada consulta.</span><span class="sxs-lookup"><span data-stu-id="2d557-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="2d557-115">Uma vez que as consultas são idempotentes, elas não alteram os dados, não importa quantas vezes você execute uma consulta.</span><span class="sxs-lookup"><span data-stu-id="2d557-115">Since the queries are idempotent, they won't change the data no matter how many times you run a query.</span></span> <span data-ttu-id="2d557-116">Portanto, você não precisa estar restrito por nenhum padrão DDD usado no lado do transacional, como agregações e outros padrões, e é por isso que as consultas são separadas da área de trabalho transacional.</span><span class="sxs-lookup"><span data-stu-id="2d557-116">Therefore, you don't need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="2d557-117">Você simplesmente consulta o banco de dados para os dados de que a interface do usuário precisa e retorna um ViewModel dinâmico que não precisa ser estaticamente definido em nenhum lugar (nenhuma classe para os ViewModels), exceto nas próprias instruções SQL.</span><span class="sxs-lookup"><span data-stu-id="2d557-117">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="2d557-118">Como essa é uma abordagem simples, o código necessário para o lado de consultas (como o código usando um micro ORM como [Dapper](https://github.com/StackExchange/Dapper)) pode ser implementado [dentro do mesmo projeto de API da Web](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span><span class="sxs-lookup"><span data-stu-id="2d557-118">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="2d557-119">A Figura 9-4 mostra isso.</span><span class="sxs-lookup"><span data-stu-id="2d557-119">Figure 9-4 shows this.</span></span> <span data-ttu-id="2d557-120">As consultas são definidas no projeto de microsserviço **Ordering.API** dentro da solução eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="2d557-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![](./media/image4.png)

<span data-ttu-id="2d557-121">**Figura 9-4**.</span><span class="sxs-lookup"><span data-stu-id="2d557-121">**Figure 9-4**.</span></span> <span data-ttu-id="2d557-122">Consultas no microsserviço de Ordenação em eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="2d557-122">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="2d557-123">Usando ViewModels feitos especificamente para aplicativos cliente, independentemente de restrições do modelo de domínio</span><span class="sxs-lookup"><span data-stu-id="2d557-123">Using ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="2d557-124">Uma vez que as consultas são executadas para obter os dados necessários para os aplicativos cliente, o tipo retornado pode ser feito especificamente para os clientes com base nos dados retornados pelas consultas.</span><span class="sxs-lookup"><span data-stu-id="2d557-124">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="2d557-125">Esses modelos ou DTOs (Objetos de Transferência de Dados) são chamados de ViewModels.</span><span class="sxs-lookup"><span data-stu-id="2d557-125">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="2d557-126">Os dados retornados (ViewModel) podem ser o resultado da associação de dados de várias entidades ou tabelas no banco de dados, ou mesmo entre várias agregações definidas no modelo de domínio para a área transacional.</span><span class="sxs-lookup"><span data-stu-id="2d557-126">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="2d557-127">Nesse caso, porque você está criando consultas independentes do modelo de domínio, os limites de agregações e as restrições são completamente ignorados e você é livre para consultar qualquer tabela e coluna de que possa precisar.</span><span class="sxs-lookup"><span data-stu-id="2d557-127">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you're free to query any table and column you might need.</span></span> <span data-ttu-id="2d557-128">Essa abordagem fornece grande flexibilidade e produtividade para os desenvolvedores criarem ou atualizarem as consultas.</span><span class="sxs-lookup"><span data-stu-id="2d557-128">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="2d557-129">Os ViewModels podem ser tipos estáticos definidos nas classes.</span><span class="sxs-lookup"><span data-stu-id="2d557-129">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="2d557-130">Ou eles podem ser criados dinamicamente com base nas consultas executadas (conforme implementado no microsserviço de ordenação), que é muito ágil para desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="2d557-130">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="2d557-131">Usando o Dapper como um micro ORM para executar consultas</span><span class="sxs-lookup"><span data-stu-id="2d557-131">Using Dapper as a micro ORM to perform queries</span></span>

<span data-ttu-id="2d557-132">Você pode usar qualquer micro ORM, Entity Framework Core ou até mesmo ADO.NET simples para a consulta.</span><span class="sxs-lookup"><span data-stu-id="2d557-132">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="2d557-133">O aplicativo de exemplo, o Dapper foi selecionado para o microsserviço de ordenação em eShopOnContainers como um bom exemplo de um micro ORM popular.</span><span class="sxs-lookup"><span data-stu-id="2d557-133">In the sample application, Dapper was selected for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="2d557-134">Ele pode executar consultas SQL simples com alto desempenho, pois é uma estrutura muito leve.</span><span class="sxs-lookup"><span data-stu-id="2d557-134">It can run plain SQL queries with great performance, because it's a very light framework.</span></span> <span data-ttu-id="2d557-135">Usando o Dapper, você pode escrever uma consulta SQL que pode acessar e unir várias tabelas.</span><span class="sxs-lookup"><span data-stu-id="2d557-135">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="2d557-136">O Dapper é um projeto de software livre (original criado por Sam Saffron) e faz parte dos blocos de construção usado no [Stack Overflow](https://stackoverflow.com/).</span><span class="sxs-lookup"><span data-stu-id="2d557-136">Dapper is an open-source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="2d557-137">Para usar o Dapper, basta instalá-lo por meio do [pacote Dapper NuGet](https://www.nuget.org/packages/Dapper), conforme mostra a figura a seguir:</span><span class="sxs-lookup"><span data-stu-id="2d557-137">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure:</span></span>

![](./media/image4.1.png)

<span data-ttu-id="2d557-138">Você também precisa adicionar uma instrução de uso para que seu código tenha acesso aos métodos de extensão Dapper.</span><span class="sxs-lookup"><span data-stu-id="2d557-138">You also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="2d557-139">Quando você usa o Dapper em seu código, usa diretamente a classe <xref:System.Data.SqlClient.SqlConnection> disponível no namespace <xref:System.Data.SqlClient>.</span><span class="sxs-lookup"><span data-stu-id="2d557-139">When you use Dapper in your code, you directly use the <xref:System.Data.SqlClient.SqlConnection> class available in the <xref:System.Data.SqlClient> namespace.</span></span> <span data-ttu-id="2d557-140">Por meio do método QueryAsync e outros métodos de extensão que estendem a classe <xref:System.Data.SqlClient.SqlConnection>, você pode simplesmente executar consultas de maneira simples e de alto desempenho.</span><span class="sxs-lookup"><span data-stu-id="2d557-140">Through the QueryAsync method and other extension methods that extend the <xref:System.Data.SqlClient.SqlConnection> class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-versus-static-viewmodels"></a><span data-ttu-id="2d557-141">ViewModels dinâmicos versus estáticos</span><span class="sxs-lookup"><span data-stu-id="2d557-141">Dynamic versus static ViewModels</span></span>

<span data-ttu-id="2d557-142">Ao retornar ViewModels do lado do servidor para aplicativos cliente, você pode pensar sobre esses ViewModels como DTOs que podem ser diferentes para as entidades de domínio internas do seu modelo de entidade porque a os ViewModels contêm os dados da maneira como o aplicativo cliente precisa.</span><span class="sxs-lookup"><span data-stu-id="2d557-142">When returning ViewModels from the server-side to client apps, you can think about those ViewModels as DTOs that can be different to the internal domain entities of your entity model because the ViewModels hold the data the way the client app needs.</span></span> <span data-ttu-id="2d557-143">Portanto, em muitos casos, você pode agregar dados provenientes de várias entidades de domínio e compor os ViewModels exatamente de acordo com a maneira como o aplicativo cliente precisa daqueles dados.</span><span class="sxs-lookup"><span data-stu-id="2d557-143">Therefore, in many cases, you can aggregate data coming from multiple domain entities and compose the ViewModels precisely according to how the client app needs that data.</span></span>

<span data-ttu-id="2d557-144">Esses ViewModels ou DTOs podem ser definidos explicitamente (como classes de proprietário de dados) como a classe [OrderSummary](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Queries/OrderViewModel.cs) mostrada um trecho de código posterior, ou você pode retornar apenas ViewModels dinâmicos ou DTOs dinâmicos simplesmente com base em atributos retornados pelas suas consultas, como um tipo `dynamic`.</span><span class="sxs-lookup"><span data-stu-id="2d557-144">Those ViewModels or DTOs can be defined explicitly (as data holder classes) like the [OrderSummary](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Queries/OrderViewModel.cs) class shown in a later code snippet, or you could just return dynamic ViewModels or dynamic DTOs simply based on the attributes returned by your queries, as a `dynamic` type.</span></span>

### <a name="viewmodel-as-dynamic-type"></a><span data-ttu-id="2d557-145">ViewModel como tipo dinâmico</span><span class="sxs-lookup"><span data-stu-id="2d557-145">ViewModel as dynamic type</span></span>

<span data-ttu-id="2d557-146">Conforme mostrado no código a seguir, um ViewModel pode ser diretamente retornado pelas consultas retornando um tipo dinâmico internamente baseado nos atributos retornados por uma consulta.</span><span class="sxs-lookup"><span data-stu-id="2d557-146">As shown in the following code, a ViewModel can be directly returned by the queries by returning a dynamic type that internally is based on the attributes returned by a query.</span></span> <span data-ttu-id="2d557-147">Isso significa que o subconjunto de atributos a serem retornados é baseado na própria consulta.</span><span class="sxs-lookup"><span data-stu-id="2d557-147">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="2d557-148">Portanto, se você adicionar uma nova coluna à consulta ou junção, esses dados serão adicionados dinamicamente ao ViewModel retornado.</span><span class="sxs-lookup"><span data-stu-id="2d557-148">Therefore, if you add a new column to the query or join, that data is dynamically added to the returned ViewModel.</span></span>

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

<span data-ttu-id="2d557-149">O ponto importante é que, ao usar um tipo dinâmico, a coleção de dados retornada é montada dinamicamente como o ViewModel.</span><span class="sxs-lookup"><span data-stu-id="2d557-149">The important point is that by using a dynamic type, the returned collection of data is dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="2d557-150">*Prós:* essa abordagem reduz a necessidade de modificar classes estáticas de ViewModel sempre que você atualizar a frase SQL de uma consulta, tornando essa abordagem de design muito ágil ao codificar, simples e rápida de evoluir conforme alterações futuras.</span><span class="sxs-lookup"><span data-stu-id="2d557-150">*Pros:* This approach reduces the need to modify static ViewModel classes whenever you update the SQL sentence of a query, making this design approach pretty agile when coding, straightforward, and quick to evolve in regard to future changes.</span></span>

<span data-ttu-id="2d557-151">*Contras:* no longo prazo, tipos dinâmicos podem afetar negativamente a clareza e o impacto da compatibilidade de um serviço com aplicativos cliente.</span><span class="sxs-lookup"><span data-stu-id="2d557-151">*Cons:* In the long term, dynamic types can impact negatively the clarity and impact the compatibility of a service with client apps.</span></span> <span data-ttu-id="2d557-152">Além disso, o software middleware como Swagger não poderá fornecer o mesmo nível de documentação em tipos retornados ao usar tipos dinâmicos.</span><span class="sxs-lookup"><span data-stu-id="2d557-152">In addition, middleware software like Swagger cannot provide the same level of documentation on returned types if using dynamic types.</span></span>

### <a name="viewmodel-as-predefined-dto-classes"></a><span data-ttu-id="2d557-153">ViewModel como classes DTO predefinidas</span><span class="sxs-lookup"><span data-stu-id="2d557-153">ViewModel as predefined DTO classes</span></span>

<span data-ttu-id="2d557-154">*Prós:* ter classes ViewModel estáticas predefinidas, como "contratos" com base em classes DTO explícitas, é definitivamente melhor para APIs públicas, mas também para microsserviços de longo prazo, mesmo que sejam usados apenas pelo mesmo aplicativo.</span><span class="sxs-lookup"><span data-stu-id="2d557-154">*Pros:* Having static predefined ViewModel classes, like "contracts" based on explicit DTO classes, is definitely better for public APIs but also for long term microservices, even if they are only used by the same application.</span></span>

<span data-ttu-id="2d557-155">Se você quiser especificar os tipos de resposta para o Swagger, precisará usar as classes DTO explícitas como o tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="2d557-155">If you want to specify response types for swagger, you need to use explicit DTO classes as the return type.</span></span> <span data-ttu-id="2d557-156">Portanto, classes DTO predefinidas permitem que você ofereça informações mais sofisticadas do Swagger.</span><span class="sxs-lookup"><span data-stu-id="2d557-156">Therefore, predefined DTO classes allow you to offer richer information from Swagger.</span></span> <span data-ttu-id="2d557-157">Isso melhora a documentação da API e a compatibilidade ao consumir uma API.</span><span class="sxs-lookup"><span data-stu-id="2d557-157">That improves the API documentation and compatibility when consuming an API.</span></span>

<span data-ttu-id="2d557-158">*Contras:* conforme mencionado anteriormente, ao atualizar o código, serão necessárias mais algumas etapas para atualizar as classes DTO.</span><span class="sxs-lookup"><span data-stu-id="2d557-158">*Cons:* As mentioned earlier, when updating the code, it takes some more steps to update the DTO classes.</span></span>

<span data-ttu-id="2d557-159">*Dica com base em nossa experiência:* nas consultas implementadas no microsserviço de Ordenação em eShopOnContainers, começamos a desenvolver usando ViewModels dinâmico, pois ele era muito simples e mais ágil nos primeiros estágios de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="2d557-159">*Tip based on our experience:* In the queries implemented at the Ordering microservice in eShopOnContainers, we started developing by using dynamic ViewModels as it was very straightforward and agile on the early development stages.</span></span> <span data-ttu-id="2d557-160">No entanto, quando o desenvolvimento foi estabilizado, escolhemos refatorar as APIs e usar DTOs estáticos ou predefinidos para ViewModels, pois fica mais claro para os consumidores do microsserviço conhecer os tipos de DTO explícitos, usados como "contratos".</span><span class="sxs-lookup"><span data-stu-id="2d557-160">But, once the development was stabilized, we chose to refactor the APIs and use static or pre-defined DTOs for the ViewModels, because it is clearer for the microservice’s consumers to know explicit DTO types, used as "contracts".</span></span>

<span data-ttu-id="2d557-161">No exemplo a seguir, você pode ver como a consulta está retornando dados usando uma classe DTO ViewModel explícita: a classe OrderSummary.</span><span class="sxs-lookup"><span data-stu-id="2d557-161">In the following example, you can see how the query is returning data by using an explicit ViewModel DTO class: the OrderSummary class.</span></span>

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
  public async Task<IEnumerable<OrderSummary>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            var result = await connection.QueryAsync<dynamic>(
                  @"SELECT o.[Id] as ordernumber, 
                  o.[OrderDate] as [date],os.[Name] as [status], 
                  SUM(oi.units*oi.unitprice) as total
                  FROM [ordering].[Orders] o
                  LEFT JOIN[ordering].[orderitems] oi ON  o.Id = oi.orderid 
                  LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
                  GROUP BY o.[Id], o.[OrderDate], os.[Name]
                  ORDER BY o.[Id]");
        }
    } 
}
```

#### <a name="describing-response-types-of-web-apis"></a><span data-ttu-id="2d557-162">Descrevendo os tipos de resposta de APIs da Web</span><span class="sxs-lookup"><span data-stu-id="2d557-162">Describing response types of Web APIs</span></span>

<span data-ttu-id="2d557-163">Os desenvolvedores que consomem APIs e microsserviços Web estão mais preocupados com o que é retornado, especificamente, tipos de resposta e códigos de erro (se não padrão).</span><span class="sxs-lookup"><span data-stu-id="2d557-163">Developers consuming web APIs and microservices are most concerned with what is returned — specifically response types and error codes (if not standard).</span></span> <span data-ttu-id="2d557-164">Eles são manipulados nos comentários XML e anotações de dados.</span><span class="sxs-lookup"><span data-stu-id="2d557-164">These are handled in the XML comments and data annotations.</span></span>

<span data-ttu-id="2d557-165">Sem a documentação adequada na interface do usuário do Swagger, o consumidor não tem conhecimento de quais tipos estão sendo retornados ou quais códigos HTTP podem ser retornados.</span><span class="sxs-lookup"><span data-stu-id="2d557-165">Without proper documentation in the Swagger UI, the consumer lacks knowledge of what types are being returned or what HTTP codes can be returned.</span></span> <span data-ttu-id="2d557-166">Esse problema é corrigido adicionando o <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, portanto, o Swagger pode gerar informações mais avançadas sobre o modelo e os valores de retorno de API, conforme mostra o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="2d557-166">That problem is fixed by adding the <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, so Swagger can generate richer information about the API return model and values, as shown in the following code:</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class OrdersController : Controller
    {
       //Additional code...
       [Route("")]
       [HttpGet]
       [ProducesResponseType(typeof(IEnumerable<OrderSummary>),
                             (int)HttpStatusCode.OK)]
       public async Task<IActionResult> GetOrders()
       {
           var orderTask = _orderQueries.GetOrdersAsync();
           var orders = await orderTask;
           return Ok(orders);
        }
    }
}
```

<span data-ttu-id="2d557-167">No entanto, o atributo `ProducesResponseType` não pode usar dinâmica como um tipo, mas requer o uso de tipos explícitos, como o `OrderSummary` ViewModel DTO, mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="2d557-167">However, the `ProducesResponseType` attribute cannot use dynamic as a type but requires to use explicit types, like the `OrderSummary` ViewModel DTO, shown in the following example:</span></span>

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

<span data-ttu-id="2d557-168">Essa é outra razão pela qual tipos retornados explícitos são melhores que tipos dinâmicos no longo prazo.</span><span class="sxs-lookup"><span data-stu-id="2d557-168">This is another reason why explicit returned types are better than dynamic types, in the long term.</span></span>
<span data-ttu-id="2d557-169">Ao usar o atributo `ProducesResponseType`, você também pode especificar qual é o resultado esperado no que diz respeito a possíveis erros/códigos HTTP, como 200, 400, etc.</span><span class="sxs-lookup"><span data-stu-id="2d557-169">When using the `ProducesResponseType` attribute, you can also specify what is the expected outcome in regards possible HTTP errors/codes, like 200,400, etc.</span></span>

<span data-ttu-id="2d557-170">Na imagem a seguir, você pode ver como a interface do usuário Swagger mostra as informações de ResponseType.</span><span class="sxs-lookup"><span data-stu-id="2d557-170">In the following image, you can see how Swagger UI shows the ResponseType information.</span></span>

![](./media/image5.png)

<span data-ttu-id="2d557-171">**Figura 9-5**.</span><span class="sxs-lookup"><span data-stu-id="2d557-171">**Figure 9-5**.</span></span> <span data-ttu-id="2d557-172">Interface do usuário do Swagger mostrando os tipos de resposta e possíveis códigos de status HTTP de uma API da Web</span><span class="sxs-lookup"><span data-stu-id="2d557-172">Swagger UI showing response types and possible HTTP status codes from a Web API</span></span>

<span data-ttu-id="2d557-173">Você pode ver na imagem acima alguns valores de exemplo com base nos tipos ViewModel mais os possíveis códigos de status HTTP que podem ser retornados.</span><span class="sxs-lookup"><span data-stu-id="2d557-173">You can see in the image above some example values based on the ViewModel types plus the possible HTTP status codes that can be returned.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="2d557-174">Recursos adicionais</span><span class="sxs-lookup"><span data-stu-id="2d557-174">Additional resources</span></span>

-   <span data-ttu-id="2d557-175">**Dapper**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span><span class="sxs-lookup"><span data-stu-id="2d557-175">**Dapper**
[*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span></span>

-   <span data-ttu-id="2d557-176">**Julie Lerman. Pontos de dados – Dapper, Entity Framework e aplicativos híbridos (artigo do MSDN Mag.)**</span><span class="sxs-lookup"><span data-stu-id="2d557-176">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN Mag. article)**</span></span>

    <span data-ttu-id="2d557-177">*https://msdn.microsoft.com/magazine/mt703432.aspx*</span><span class="sxs-lookup"><span data-stu-id="2d557-177">*https://msdn.microsoft.com/magazine/mt703432.aspx*</span></span>

-   <span data-ttu-id="2d557-178">**Páginas de ajuda da API Web ASP.NET Core usando o Swagger**</span><span class="sxs-lookup"><span data-stu-id="2d557-178">**ASP.NET Core Web API Help Pages using Swagger**</span></span>

    <span data-ttu-id="2d557-179">*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio*</span><span class="sxs-lookup"><span data-stu-id="2d557-179">*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio*</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="2d557-180">[Anterior] (eshoponcontainers-cqrs-ddd-microservice.md) [Próximo] (ddd-orientado-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="2d557-180">[Previous] (eshoponcontainers-cqrs-ddd-microservice.md) [Next] (ddd-oriented-microservice.md)</span></span>
