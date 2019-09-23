---
title: Migrar um serviço de solicitação-resposta do WCF para gRPC-gRPC para desenvolvedores do WCF
description: Saiba como migrar um serviço de solicitação-resposta simples do WCF para o gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: ac9eecf66a7ac37a1df9714e6383f7eaebae4781
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184305"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a><span data-ttu-id="61c91-103">Migrar um serviço de solicitação-resposta WCF para um RPC unário gRPC</span><span class="sxs-lookup"><span data-stu-id="61c91-103">Migrate a WCF request-reply service to a gRPC unary RPC</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="61c91-104">Esta seção aborda como migrar um serviço de solicitação-resposta básico no WCF para um serviço RPC unário no ASP.NET Core gRPC.</span><span class="sxs-lookup"><span data-stu-id="61c91-104">This section covers how to migrate a basic request-reply service in WCF to a unary RPC service in ASP.NET Core gRPC.</span></span> <span data-ttu-id="61c91-105">Esses serviços são os tipos de serviço mais simples no Windows Communication Foundation (WCF) e no gRPC, portanto, é um ótimo lugar para começar.</span><span class="sxs-lookup"><span data-stu-id="61c91-105">These services are the simplest service types in both Windows Communication Foundation (WCF) and gRPC, so it's an excellent place to start.</span></span> <span data-ttu-id="61c91-106">Depois de migrar o serviço, você aprenderá a gerar uma biblioteca de cliente do `.proto` mesmo arquivo para consumir o serviço de um aplicativo cliente .net.</span><span class="sxs-lookup"><span data-stu-id="61c91-106">After migrating the service, you'll learn how to generate a client library from the same `.proto` file to consume the service from a .NET client application.</span></span>

## <a name="the-wcf-solution"></a><span data-ttu-id="61c91-107">A solução WCF</span><span class="sxs-lookup"><span data-stu-id="61c91-107">The WCF solution</span></span>

<span data-ttu-id="61c91-108">A [solução PortfoliosSample](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) inclui um serviço de portfólio simples de solicitação-resposta para baixar um único portfólio ou todos os portfólios de um determinado Trader.</span><span class="sxs-lookup"><span data-stu-id="61c91-108">The [PortfoliosSample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) includes a simple Request-Reply Portfolio service to download a single portfolio, or all portfolios for a given Trader.</span></span> <span data-ttu-id="61c91-109">O serviço é definido na interface `IPortfolioService` com um `ServiceContract` atributo:</span><span class="sxs-lookup"><span data-stu-id="61c91-109">The service is defined in the interface `IPortfolioService` with a `ServiceContract` attribute:</span></span>

```csharp
[ServiceContract]
public interface IPortfolioService
{
    [OperationContract]
    Task<Portfolio> Get(Guid traderId, int portfolioId);

    [OperationContract]
    Task<List<Portfolio>> GetAll(Guid traderId);
}
```

<span data-ttu-id="61c91-110">O `Portfolio` modelo é uma classe C# simples marcada com [DataContract](xref:System.Runtime.Serialization.DataContractAttribute), incluindo uma lista de `PortfolioItem` objetos.</span><span class="sxs-lookup"><span data-stu-id="61c91-110">The `Portfolio` model is a simple C# class marked with [DataContract](xref:System.Runtime.Serialization.DataContractAttribute), including a list of `PortfolioItem` objects.</span></span> <span data-ttu-id="61c91-111">Esses modelos são definidos no `TraderSys.PortfolioData` projeto, juntamente com uma classe de repositório que representa uma abstração de acesso a dados.</span><span class="sxs-lookup"><span data-stu-id="61c91-111">These models are defined in the `TraderSys.PortfolioData` project, along with a repository class representing a data access abstraction.</span></span>

```csharp
[DataContract]
public class Portfolio
{
    [DataMember]
    public int Id { get; set; }

    [DataMember]
    public Guid TraderId { get; set; }

    [DataMember]
    public List<PortfolioItem> Items { get; set; }
}

[DataContract]
public class PortfolioItem
{
    [DataMember]
    public int Id { get; set; }

    [DataMember]
    public int ShareId { get; set; }

    [DataMember]
    public int Holding { get; set; }

    [DataMember]
    public decimal Cost { get; set; }
}
```

<span data-ttu-id="61c91-112">A `ServiceContract` implementação usa uma classe `DataContract` de repositório fornecida por meio de injeção de dependência que retorna instâncias dos tipos.</span><span class="sxs-lookup"><span data-stu-id="61c91-112">The `ServiceContract` implementation uses a repository class provided via dependency injection that returns instances of the `DataContract` types.</span></span>

```csharp
public class PortfolioService : IPortfolioService
{
    private readonly IPortfolioRepository _repository;

    public PortfolioService(IPortfolioRepository repository)
    {
        _repository = repository;
    }

    public async Task<Portfolio> Get(Guid traderId, int portfolioId)
    {
        return await _repository.GetAsync(traderId, portfolioId);
    }

    public async Task<List<Portfolio>> GetAll(Guid traderId)
    {
        return await _repository.GetAllAsync(traderId);
    }
}
```

## <a name="the-portfoliosproto-file"></a><span data-ttu-id="61c91-113">O arquivo portfolios. proto</span><span class="sxs-lookup"><span data-stu-id="61c91-113">The portfolios.proto file</span></span>

<span data-ttu-id="61c91-114">Se você seguiu as instruções na seção anterior, deve ter um projeto gRPC com um `portfolios.proto` arquivo parecido com este.</span><span class="sxs-lookup"><span data-stu-id="61c91-114">If you followed the instructions in the previous section, you should have a gRPC project with a `portfolios.proto` file that looks like this.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

<span data-ttu-id="61c91-115">A primeira etapa é migrar as `DataContract` classes para seus equivalentes Protobuf.</span><span class="sxs-lookup"><span data-stu-id="61c91-115">The first step is to migrate the `DataContract` classes to their Protobuf equivalents.</span></span>

## <a name="convert-the-datacontracts-to-grpc-messages"></a><span data-ttu-id="61c91-116">Converter os DataContracts em mensagens gRPC</span><span class="sxs-lookup"><span data-stu-id="61c91-116">Convert the DataContracts to gRPC messages</span></span>

<span data-ttu-id="61c91-117">A `PortfolioItem` classe será convertida primeiro em uma mensagem Protobuf, pois a `Portfolio` classe depende dela.</span><span class="sxs-lookup"><span data-stu-id="61c91-117">The `PortfolioItem` class will be converted to a Protobuf message first, as the `Portfolio` class depends on it.</span></span> <span data-ttu-id="61c91-118">A classe é muito simples e três das propriedades são mapeadas diretamente para os tipos de dados gRPC.</span><span class="sxs-lookup"><span data-stu-id="61c91-118">The class is very simple, and three of the properties map directly to gRPC data types.</span></span> <span data-ttu-id="61c91-119">A `Cost` Propriedade, que representa o preço pago pelos compartilhamentos na compra, `decimal` é um campo, e gRPC `float` só `double` dá suporte a ou para números reais, que não são adequados para a moeda.</span><span class="sxs-lookup"><span data-stu-id="61c91-119">The `Cost` property, representing the price paid for the shares at purchase, is a `decimal` field, and gRPC only supports `float` or `double` for real numbers, which aren't suitable for currency.</span></span> <span data-ttu-id="61c91-120">Como os preços de compartilhamento variam em um mínimo de uma centésimo, o custo pode ser expresso `int32` como uma das centavos.</span><span class="sxs-lookup"><span data-stu-id="61c91-120">Since share prices vary by a minimum of one cent, the cost can be expressed as an `int32` of cents.</span></span>

> [!NOTE]
> <span data-ttu-id="61c91-121">Lembre-se `camelCase` de usar para nomes de `.proto` campo em seu C# arquivo; o gerador de código `PascalCase` os converterá em para você e os usuários de outras linguagens lhe agradecerão por respeitar seus diferentes padrões de codificação.</span><span class="sxs-lookup"><span data-stu-id="61c91-121">Remember to use `camelCase` for field names in your `.proto` file; the C# code generator will convert them to `PascalCase` for you, and users of other languages will thank you for respecting their different coding standards.</span></span>

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 shareId = 2;
    int32 holding = 3;
    int32 costCents = 4;
}
```

<span data-ttu-id="61c91-122">A `Portfolio` classe é um pouco mais complicada.</span><span class="sxs-lookup"><span data-stu-id="61c91-122">The `Portfolio` class is a little more complicated.</span></span> <span data-ttu-id="61c91-123">No código WCF, o desenvolvedor usou um `Guid` para a `TraderId` Propriedade e contém um `List<PortfolioItem>`.</span><span class="sxs-lookup"><span data-stu-id="61c91-123">In the WCF code, the developer used a `Guid` for the `TraderId` property, and contains a `List<PortfolioItem>`.</span></span> <span data-ttu-id="61c91-124">No Protobuf, que não tem um tipo de primeira `UUID` classe, você deve usar um `string` para o `traderId` campo e analisá-lo em seu próprio código.</span><span class="sxs-lookup"><span data-stu-id="61c91-124">In Protobuf, which doesn't have a first-class `UUID` type, you should use a `string` for the `traderId` field and parse it in your own code.</span></span> <span data-ttu-id="61c91-125">Para a lista de itens, use a `repeated` palavra-chave no campo.</span><span class="sxs-lookup"><span data-stu-id="61c91-125">For the list of items, use the `repeated` keyword on the field.</span></span>

```protobuf
message Portfolio {
    int32 id = 1;
    string traderId = 2;
    repeated PortfolioItem items = 3;
}
```

<span data-ttu-id="61c91-126">Agora temos nossas mensagens de dados, podemos declarar os pontos de extremidade de RPC do serviço.</span><span class="sxs-lookup"><span data-stu-id="61c91-126">Now we have our data messages, we can declare the service RPC endpoints.</span></span>

## <a name="convert-the-servicecontract-to-a-grpc-service"></a><span data-ttu-id="61c91-127">Converter o ServiceContract em um serviço gRPC</span><span class="sxs-lookup"><span data-stu-id="61c91-127">Convert the ServiceContract to a gRPC service</span></span>

<span data-ttu-id="61c91-128">O método `Get` WCF usa dois parâmetros: `Guid traderId` e `int portfolioId`.</span><span class="sxs-lookup"><span data-stu-id="61c91-128">The WCF `Get` method takes two parameters: `Guid traderId` and `int portfolioId`.</span></span> <span data-ttu-id="61c91-129">os métodos de serviço gRPC podem pegar apenas um único parâmetro, portanto, uma mensagem deve ser criada para conter os dois valores.</span><span class="sxs-lookup"><span data-stu-id="61c91-129">gRPC service methods can only take a single parameter, so a message must be created to hold the two values.</span></span> <span data-ttu-id="61c91-130">É uma prática comum nomear esses objetos de solicitação com o mesmo nome que o método e o `Request`sufixo.</span><span class="sxs-lookup"><span data-stu-id="61c91-130">It's common practice to name these request objects with the same name as the method and the suffix `Request`.</span></span> <span data-ttu-id="61c91-131">Novamente, `string` o está sendo usado para `traderId` o campo em `Guid`vez de.</span><span class="sxs-lookup"><span data-stu-id="61c91-131">Again, `string` is being used for the `traderId` field instead of `Guid`.</span></span>

<span data-ttu-id="61c91-132">O serviço pode simplesmente retornar uma `Portfolio` mensagem diretamente, mas novamente, isso poderia afetar a compatibilidade com versões anteriores no futuro.</span><span class="sxs-lookup"><span data-stu-id="61c91-132">The service could just return a `Portfolio` message directly, but again, this could impact backward compatibility in the future.</span></span> <span data-ttu-id="61c91-133">É uma prática `Request` recomendada definir mensagens e `Response` separadas para cada método em um serviço, mesmo se muitos deles forem os mesmos no momento, portanto, declare uma `GetResponse` mensagem com um único `Portfolio` campo.</span><span class="sxs-lookup"><span data-stu-id="61c91-133">It's a good practice to define separate `Request` and `Response` messages for every method in a service, even if many of them are the same right now, so declare a `GetResponse` message with a single `Portfolio` field.</span></span>

<span data-ttu-id="61c91-134">O exemplo a seguir mostra a declaração do método de serviço gRPC usando `GetRequest` a mensagem:</span><span class="sxs-lookup"><span data-stu-id="61c91-134">The following example shows the declaration of the gRPC service method using the `GetRequest` message:</span></span>

```protobuf
message GetRequest {
    string traderId = 1;
    int32 portfolioId = 2;
}

message GetResponse {
    Portfolio portfolio = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (GetResponse);
}
```

<span data-ttu-id="61c91-135">O método `GetAll` WCF usa apenas um único parâmetro, `traderId`, portanto, pode parecer que ele pode ser `string` especificado como o tipo de parâmetro, mas gRPC requer um tipo de mensagem definido.</span><span class="sxs-lookup"><span data-stu-id="61c91-135">The WCF `GetAll` method only takes a single parameter, `traderId`, so it might seem that one could specify `string` as the parameter type, but gRPC requires a defined message type.</span></span> <span data-ttu-id="61c91-136">Esse requisito ajuda a impor a prática de usar mensagens personalizadas para todas as entradas e saídas, para compatibilidade com versões anteriores futuras.</span><span class="sxs-lookup"><span data-stu-id="61c91-136">This requirement helps to enforce the practice of using custom messages for all inputs and outputs, for future backward compatibility.</span></span>

<span data-ttu-id="61c91-137">O método WCF também retornou `List<Portfolio>`um, mas, pelo mesmo motivo, ele não permite tipos de parâmetro simples, `repeated Portfolio` gRPC não permitirá como um tipo de retorno.</span><span class="sxs-lookup"><span data-stu-id="61c91-137">The WCF method also returned a `List<Portfolio>`, but for the same reason it doesn't allow simple parameter types, gRPC won't allow `repeated Portfolio` as a return type.</span></span> <span data-ttu-id="61c91-138">Em vez disso, `GetAllResponse` crie um tipo para encapsular a lista.</span><span class="sxs-lookup"><span data-stu-id="61c91-138">Instead, create a `GetAllResponse` type to wrap the list.</span></span>

> [!WARNING]
> <span data-ttu-id="61c91-139">Você pode estar tentado a criar uma `PortfolioList` mensagem ou algo semelhante e usá-la em vários métodos de serviço, mas deve resistir a essa tentação.</span><span class="sxs-lookup"><span data-stu-id="61c91-139">You may be tempted to create a `PortfolioList` message or similar and use it across multiple service methods, but you should resist this temptation.</span></span> <span data-ttu-id="61c91-140">É impossível saber como os vários métodos em um serviço podem evoluir no futuro, portanto, mantenha suas mensagens específicas e separadas de forma limpa.</span><span class="sxs-lookup"><span data-stu-id="61c91-140">It's impossible to know how the various methods on a service may evolve in the future, so keep their messages specific and cleanly separated.</span></span>

```protobuf
message GetAllRequest {
    string traderId = 1;
}

message PortfolioList {
    repeated Portfolio portfolios = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (Portfolio);
    rpc GetAll(GetAllRequest) returns (GetAllResponse);
}
```

<span data-ttu-id="61c91-141">Se você salvar seu projeto com essas alterações, o destino da compilação gRPC será executado em segundo plano e gerará todos os tipos de mensagem Protobuf e uma classe base que você pode herdar para implementar o serviço.</span><span class="sxs-lookup"><span data-stu-id="61c91-141">If you save your project with these changes, the gRPC build target will run in the background and generate all the Protobuf message types and a base class you can inherit to implement the service.</span></span>

<span data-ttu-id="61c91-142">Abra a `Services/GreeterService.cs` classe e exclua o código de exemplo.</span><span class="sxs-lookup"><span data-stu-id="61c91-142">Open up the `Services/GreeterService.cs` class and delete the example code.</span></span> <span data-ttu-id="61c91-143">Agora você pode adicionar a implementação do serviço de portfólio.</span><span class="sxs-lookup"><span data-stu-id="61c91-143">Now you can add the Portfolio service implementation.</span></span> <span data-ttu-id="61c91-144">A classe base gerada estará no `Protos` namespace e será gerada como uma classe aninhada.</span><span class="sxs-lookup"><span data-stu-id="61c91-144">The generated base class will be in the `Protos` namespace and is generated as a nested class.</span></span> <span data-ttu-id="61c91-145">gRPC cria uma classe estática com o mesmo nome que o serviço no `.proto` arquivo e, em seguida, uma classe base com o sufixo `Base` dentro dessa classe estática, portanto, o identificador completo para o tipo `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`base é.</span><span class="sxs-lookup"><span data-stu-id="61c91-145">gRPC creates a static class with the same name as the service in the `.proto` file, and then a base class with the suffix `Base` inside that static class, so the full identifier for the base type is `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`.</span></span>

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

<span data-ttu-id="61c91-146">A classe base declara `virtual` métodos para `Get` e `GetAll` que podem ser substituídos para implementar o serviço.</span><span class="sxs-lookup"><span data-stu-id="61c91-146">The base class declares `virtual` methods for `Get` and `GetAll` that can be overridden to implement the service.</span></span> <span data-ttu-id="61c91-147">Os métodos são `virtual` em vez `abstract` de que, se você não implementá-los, o serviço poderá retornar `Unimplemented` um código de status gRPC explícito, assim como `NotImplementedException` você pode C# lançar um código regular.</span><span class="sxs-lookup"><span data-stu-id="61c91-147">The methods are `virtual` rather than `abstract` so that if you don't implement them, the service can return an explicit gRPC `Unimplemented` status code, much like you might throw a `NotImplementedException` in regular C# code.</span></span>

<span data-ttu-id="61c91-148">A assinatura para todos os métodos de serviço unário gRPC no ASP.NET Core é consistente.</span><span class="sxs-lookup"><span data-stu-id="61c91-148">The signature for all gRPC unary service methods in ASP.NET Core is consistent.</span></span> <span data-ttu-id="61c91-149">Há dois parâmetros: o primeiro é o tipo de mensagem declarado no `.proto` arquivo e o segundo é um `ServerCallContext` `HttpContext` que funciona de forma semelhante ao de ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="61c91-149">There are two parameters: the first is the message type declared in the `.proto` file, and the second is a `ServerCallContext` that works similarly to the `HttpContext` from ASP.NET Core.</span></span> <span data-ttu-id="61c91-150">Na verdade, há um método de extensão chamado `GetHttpContext` `ServerCallContext` na classe que você pode usar para obter o subjacente `HttpContext`, embora você não precise usá-lo com frequência.</span><span class="sxs-lookup"><span data-stu-id="61c91-150">In fact, there's an extension method called `GetHttpContext` on the `ServerCallContext` class that you can use to get the underlying `HttpContext`, although you shouldn't need to use it often.</span></span> <span data-ttu-id="61c91-151">Vamos examinar `ServerCallContext` mais adiante neste capítulo e também no capítulo que aborda a autenticação.</span><span class="sxs-lookup"><span data-stu-id="61c91-151">We'll take a look at `ServerCallContext` later in this chapter, and also in the chapter that discusses authentication.</span></span>

<span data-ttu-id="61c91-152">O tipo de retorno do método é `Task<T>` um `T` em que é o tipo de mensagem de resposta.</span><span class="sxs-lookup"><span data-stu-id="61c91-152">The method's return type is a `Task<T>` where `T` is the response message type.</span></span> <span data-ttu-id="61c91-153">Todos os métodos de serviço gRPC são assíncronos.</span><span class="sxs-lookup"><span data-stu-id="61c91-153">All gRPC service methods are asynchronous.</span></span>

## <a name="migrate-the-portfoliodata-library-to-net-core"></a><span data-ttu-id="61c91-154">Migrar a biblioteca PortfolioData para o .NET Core</span><span class="sxs-lookup"><span data-stu-id="61c91-154">Migrate the PortfolioData library to .NET Core</span></span>

<span data-ttu-id="61c91-155">Neste ponto, o projeto precisa do repositório de portfólio e dos modelos contidos na `TraderSys.PortfolioData` biblioteca de classes na solução do WCF.</span><span class="sxs-lookup"><span data-stu-id="61c91-155">At this point, the project needs the Portfolio repository and models contained in the `TraderSys.PortfolioData` class library in the WCF solution.</span></span> <span data-ttu-id="61c91-156">A maneira mais fácil de trazê-los é criar uma nova biblioteca de classes usando a caixa de diálogo **novo projeto** do Visual Studio com o modelo *biblioteca de classes (.net Standard)* ou na linha de comando usando o CLI do .NET Core, executando os seguintes comandos do diretório que contém o `TraderSys.sln` arquivo.</span><span class="sxs-lookup"><span data-stu-id="61c91-156">The easiest way to bring them across is to create a new class library using either the Visual Studio **New project** dialog with the *Class Library (.NET Standard)* template, or from the command line using the .NET Core CLI, running the following commands from the directory containing the `TraderSys.sln` file.</span></span>

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

<span data-ttu-id="61c91-157">Depois que a biblioteca tiver sido criada e adicionada à solução, exclua o `Class1.cs` arquivo gerado e copie os arquivos da biblioteca da solução WCF para a pasta da nova biblioteca de classes, mantendo a estrutura de pastas.</span><span class="sxs-lookup"><span data-stu-id="61c91-157">Once the library has been created and added to the solution, delete the generated `Class1.cs` file and copy the files from the WCF solution's library into the new class library's folder, keeping the folder structure.</span></span>

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

<span data-ttu-id="61c91-158">Os arquivos de projeto do .net modernos `.cs` incluem automaticamente todos os arquivos no ou em seu próprio diretório, portanto, não é necessário adicioná-los explicitamente ao projeto.</span><span class="sxs-lookup"><span data-stu-id="61c91-158">Modern .NET project files automatically include any `.cs` files in or under their own directory, so there's no need to explicitly add them to the project.</span></span> <span data-ttu-id="61c91-159">A única etapa `DataContract` restante é remover os atributos e `DataMember` das `Portfolio` classes e para `PortfolioItem` que eles sejam classes simples e C# antigas.</span><span class="sxs-lookup"><span data-stu-id="61c91-159">The only step remaining is to remove the `DataContract` and `DataMember` attributes from the `Portfolio` and `PortfolioItem` classes so they're plain old C# classes.</span></span>

```csharp
public class Portfolio
{
    public int Id { get; set; }
    public Guid TraderId { get; set; }
    public List<PortfolioItem> Items { get; set; }
}

public class PortfolioItem
{
    public int Id { get; set; }
    public int ShareId { get; set; }
    public int Holding { get; set; }
    public decimal Cost { get; set; }
}
```

## <a name="use-aspnet-core-dependency-injection"></a><span data-ttu-id="61c91-160">Usar ASP.NET Core injeção de dependência</span><span class="sxs-lookup"><span data-stu-id="61c91-160">Use ASP.NET Core dependency injection</span></span>

<span data-ttu-id="61c91-161">Agora você pode adicionar uma referência a essa biblioteca para o projeto de aplicativo gRPC e consumir `PortfolioRepository` a classe usando a injeção de dependência na implementação do serviço gRPC.</span><span class="sxs-lookup"><span data-stu-id="61c91-161">Now you can add a reference to this library to the gRPC application project and consume the `PortfolioRepository` class using dependency injection in the gRPC service implementation.</span></span> <span data-ttu-id="61c91-162">No aplicativo WCF, a injeção de dependência foi fornecida pelo contêiner Autofac IoC.</span><span class="sxs-lookup"><span data-stu-id="61c91-162">In the WCF application, dependency injection was provided by the Autofac IoC container.</span></span> <span data-ttu-id="61c91-163">ASP.NET Core tem injeção de dependência inclusas em; o repositório pode ser registrado no `ConfigureServices` método `Startup` na classe.</span><span class="sxs-lookup"><span data-stu-id="61c91-163">ASP.NET Core has dependency injection baked in; the repository can be registered in the `ConfigureServices` method in the `Startup` class.</span></span>

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Register the repository class as a scoped service (instance per request)
        services.AddScoped<IPortfolioRepository, PortfolioRepository>();

        services.AddGrpc();
    }

    // ...
}
```

<span data-ttu-id="61c91-164">A `IPortfolioRepository` implementação agora pode ser especificada como um parâmetro `PortfolioService` de Construtor na classe, da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="61c91-164">The `IPortfolioRepository` implementation can now be specified as a constructor parameter in the `PortfolioService` class, as follows:</span></span>

```csharp
public class PortfolioService : Protos.Portfolios.PortfoliosBase
{
    private readonly IPortfolioRepository _repository;

    public PortfolioService(IPortfolioRepository repository)
    {
        _repository = repository;
    }
}
```

## <a name="implement-the-grpc-service"></a><span data-ttu-id="61c91-165">Implementar o serviço gRPC</span><span class="sxs-lookup"><span data-stu-id="61c91-165">Implement the gRPC service</span></span>

<span data-ttu-id="61c91-166">Agora que você declarou suas mensagens e seu serviço no `portfolios.proto` arquivo, precisará implementar os métodos de serviço `PortfolioService` na classe que herda da classe gerada `Portfolios.PortfoliosBase` pelo gRPC.</span><span class="sxs-lookup"><span data-stu-id="61c91-166">Now that you've declared your messages and your service in the `portfolios.proto` file, you have to implement the service methods in the `PortfolioService` class that inherits from the gRPC-generated `Portfolios.PortfoliosBase` class.</span></span> <span data-ttu-id="61c91-167">Os métodos são declarados como `virtual` na classe base.</span><span class="sxs-lookup"><span data-stu-id="61c91-167">The methods are declared as `virtual` in the base class.</span></span> <span data-ttu-id="61c91-168">Se você não substituí-los, eles retornarão um código de status gRPC "não implementado" por padrão.</span><span class="sxs-lookup"><span data-stu-id="61c91-168">If you don't override them, they'll return a gRPC "Not Implemented" status code by default.</span></span>

<span data-ttu-id="61c91-169">Comece implementando o `Get` método.</span><span class="sxs-lookup"><span data-stu-id="61c91-169">Start by implementing the `Get` method.</span></span> <span data-ttu-id="61c91-170">A substituição padrão é semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="61c91-170">The default override looks like the following example:</span></span>

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

<span data-ttu-id="61c91-171">O primeiro problema é `request.TraderId` uma cadeia de caracteres, e o serviço requer um. `Guid`</span><span class="sxs-lookup"><span data-stu-id="61c91-171">The first issue is that `request.TraderId` is a string, and the service requires a `Guid`.</span></span> <span data-ttu-id="61c91-172">Embora o formato esperado para a cadeia de caracteres seja `UUID`a, o código precisa lidar com a possibilidade de um chamador ter enviado um valor inválido e responder adequadamente.</span><span class="sxs-lookup"><span data-stu-id="61c91-172">Even though the expected format for the string is a `UUID`, the code has to deal with the possibility that a caller has sent an invalid value and respond appropriately.</span></span> <span data-ttu-id="61c91-173">O serviço pode responder com erros lançando um `RpcException`e usar o código de `InvalidArgument` status padrão para expressar o problema.</span><span class="sxs-lookup"><span data-stu-id="61c91-173">The service can respond with errors by throwing an `RpcException`, and use the standard `InvalidArgument` status code to express the problem.</span></span>

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    return base.Get(request, context);
}
```

<span data-ttu-id="61c91-174">Uma vez que há um `Guid` valor adequado `traderId`para, o repositório pode ser usado para recuperar o portfólio e retorná-lo para o cliente.</span><span class="sxs-lookup"><span data-stu-id="61c91-174">Once there's a proper `Guid` value for `traderId`, the repository can be used to retrieve the Portfolio and return it to the client.</span></span>

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a><span data-ttu-id="61c91-175">Mapear modelos internos para mensagens gRPC</span><span class="sxs-lookup"><span data-stu-id="61c91-175">Map internal models to gRPC messages</span></span>

<span data-ttu-id="61c91-176">O código anterior não funciona realmente porque o repositório está retornando seu próprio modelo `Portfolio`poco, mas gRPC precisa *de sua* própria `Portfolio`mensagem Protobuf.</span><span class="sxs-lookup"><span data-stu-id="61c91-176">The previous code doesn't actually work because the repository is returning its own POCO model `Portfolio`, but gRPC needs *its* own Protobuf message `Portfolio`.</span></span> <span data-ttu-id="61c91-177">Assim como o mapeamento de tipos de Entity Framework para tipos de transferência de dados, a melhor solução é fornecer conversão entre os dois.</span><span class="sxs-lookup"><span data-stu-id="61c91-177">Much like mapping Entity Framework types to data transfer types, the best solution is to provide conversion between the two.</span></span> <span data-ttu-id="61c91-178">Um bom lugar para colocar o código para isso é na classe gerada pelo Protobuf, que é declarada como `partial` uma classe para que possa ser estendida.</span><span class="sxs-lookup"><span data-stu-id="61c91-178">A good place to put the code for this is in the Protobuf-generated class, which is declared as a `partial` class so it can be extended.</span></span>

```csharp
namespace TraderSys.Portfolios.Protos
{
    public partial class PortfolioItem
    {
        public static PortfolioItem FromRepositoryModel(PortfolioData.Models.PortfolioItem source)
        {
            if (source is null) return null;

            return new PortfolioItem
            {
                Id = source.Id,
                ShareId = source.ShareId,
                Holding = source.Holding,
                CostCents = (int)(source.Cost * 100)
            };
        }
    }

    public partial class Portfolio
    {
        public static Portfolio FromRepositoryModel(PortfolioData.Models.Portfolio source)
        {
            if (source is null) return null;

            var target = new Portfolio
            {
                Id = source.Id,
                TraderId = source.TraderId.ToString(),
            };

            target.Items.AddRange(source.Items.Select(PortfolioItem.FromRepositoryModel));

            return target;
        }
    }
}
```

> [!NOTE]
> <span data-ttu-id="61c91-179">Você pode usar uma biblioteca como [o AutoMapper](https://automapper.org/) para lidar com essa conversão de classes de modelo internas para tipos Protobuf, contanto que configure as conversões de tipo de nível `string` inferior como ou `decimal` / `Guid` /e o mapeamento de lista. `double`</span><span class="sxs-lookup"><span data-stu-id="61c91-179">You could use a library like [AutoMapper](https://automapper.org/) to handle this conversion from internal model classes to Protobuf types, as long as you configure the lower-level type conversions like `string`/`Guid` or `decimal`/`double` and the list mapping.</span></span>

<span data-ttu-id="61c91-180">Com o código de conversão em vigor, `Get` a implementação do método pode ser concluída.</span><span class="sxs-lookup"><span data-stu-id="61c91-180">With the conversion code in place, the `Get` method implementation can be completed.</span></span>

```csharp
public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    var portfolio = await _repository.GetAsync(traderId, request.PortfolioId);

    return new GetResponse
    {
        Portfolio = Portfolio.FromRepositoryModel(portfolio)
    };
}

```

<span data-ttu-id="61c91-181">A implementação do `GetAll` método é semelhante.</span><span class="sxs-lookup"><span data-stu-id="61c91-181">The implementation of the `GetAll` method is similar.</span></span> <span data-ttu-id="61c91-182">Observe que os `repeated` campos em mensagens Protobuf são gerados como `readonly` Propriedades do tipo `RepeatedField<T>`, portanto, você precisa adicionar itens a eles usando o `AddRange` método, como no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="61c91-182">Note that the `repeated` fields on Protobuf messages are generated as `readonly` properties of type `RepeatedField<T>`, so you have to add items to them using the `AddRange` method, like in the following example:</span></span>

```csharp
public override async Task<GetAllResponse> GetAll(GetAllRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    var portfolios = await _repository.GetAllAsync(traderId);

    var response = new GetAllResponse();
    response.Portfolios.AddRange(portfolios.Select(Portfolio.FromRepositoryModel));

    return response;
}
```

<span data-ttu-id="61c91-183">Tendo migrado com êxito o serviço de solicitação-resposta do WCF para gRPC, vamos examinar a criação de um cliente para ele `.proto` a partir do arquivo.</span><span class="sxs-lookup"><span data-stu-id="61c91-183">Having successfully migrated the WCF request-reply service to gRPC, let's look at creating a client for it from the `.proto` file.</span></span>

## <a name="generate-client-code"></a><span data-ttu-id="61c91-184">Gerar código de cliente</span><span class="sxs-lookup"><span data-stu-id="61c91-184">Generate client code</span></span>

<span data-ttu-id="61c91-185">Crie um .NET Standard biblioteca de classes na mesma solução para conter o cliente.</span><span class="sxs-lookup"><span data-stu-id="61c91-185">Create a .NET Standard class library in the same solution to contain the client.</span></span> <span data-ttu-id="61c91-186">Isso é basicamente um exemplo de criação de código de cliente, mas você pode empacotar uma biblioteca desse tipo usando o NuGet e distribuí-la em um repositório interno para que outras equipes do .NET consumam.</span><span class="sxs-lookup"><span data-stu-id="61c91-186">This is primarily an example of creating client code, but you could package such a library using NuGet and distribute it on an internal repository for other .NET teams to consume.</span></span> <span data-ttu-id="61c91-187">Vá em frente e adicione uma nova biblioteca de classes `TraderSys.Portfolios.Client` .net Standard chamada à solução e exclua o `Class1.cs` arquivo.</span><span class="sxs-lookup"><span data-stu-id="61c91-187">Go ahead and add a new .NET Standard Class Library called `TraderSys.Portfolios.Client` to the solution and delete the `Class1.cs` file.</span></span>

> [!CAUTION]
> <span data-ttu-id="61c91-188">O pacote NuGet do [.net. Client do Grpc](https://www.nuget.org/packages/Grpc.Net.Client) requer o .net Core 3,0 (ou outro tempo de execução compatível com 2,1 .net Standard).</span><span class="sxs-lookup"><span data-stu-id="61c91-188">The [Grpc.Net.Client](https://www.nuget.org/packages/Grpc.Net.Client) NuGet package requires .NET Core 3.0 (or another .NET Standard 2.1-compliant runtime).</span></span> <span data-ttu-id="61c91-189">As versões anteriores do .NET Framework e do .NET Core são compatíveis com o pacote NuGet [Grpc. Core](https://www.nuget.org/packages/Grpc.Core) .</span><span class="sxs-lookup"><span data-stu-id="61c91-189">Earlier versions of .NET Framework and .NET Core are supported by the [Grpc.Core](https://www.nuget.org/packages/Grpc.Core) NuGet package.</span></span>

<span data-ttu-id="61c91-190">No Visual Studio 2019, você pode adicionar referências a serviços gRPCs de forma semelhante à maneira como você adicionaria referências de serviço a projetos WCF em versões anteriores do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="61c91-190">In Visual Studio 2019, you can add references to gRPC services similar to the way you'd add Service References to WCF projects in earlier versions of Visual Studio.</span></span> <span data-ttu-id="61c91-191">Referências de serviço e serviços conectados são todos gerenciados na mesma interface do usuário agora, que você pode acessar clicando com o botão direito do `TraderSys.Portfolios.Client` mouse no nó **dependências** no projeto no Gerenciador de soluções e selecionando **Adicionar serviço conectado**.</span><span class="sxs-lookup"><span data-stu-id="61c91-191">Service References and Connected Services are all managed under the same UI now, which you can access by right-clicking the **Dependencies** node in the `TraderSys.Portfolios.Client` project in Solution Explorer and selecting **Add Connected Service**.</span></span> <span data-ttu-id="61c91-192">Na janela de ferramentas exibida, selecione a seção **referências de serviço** e clique em **Adicionar nova referência de serviço gRPC**.</span><span class="sxs-lookup"><span data-stu-id="61c91-192">In the tool window that appears, select the **Service References** section and click **Add new gRPC service reference**.</span></span>

![A interface do usuário dos serviços conectados no Visual Studio 2019](media/migrate-request-reply/add-connected-service.png)

<span data-ttu-id="61c91-194">Navegue até o `portfolios.proto` arquivo `TraderSys.Portfolios` no projeto, deixe o **tipo de classe a ser gerado** como **cliente**e clique em **OK**.</span><span class="sxs-lookup"><span data-stu-id="61c91-194">Browse to the `portfolios.proto` file in the `TraderSys.Portfolios` project, leave the **type of class to be generated** as **Client**, and click **OK**.</span></span>

![A caixa de diálogo Adicionar nova referência de serviço gRPC no Visual Studio 2019](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> <span data-ttu-id="61c91-196">Observe que essa caixa de diálogo também fornece um campo URL.</span><span class="sxs-lookup"><span data-stu-id="61c91-196">Notice that this dialog also provides a URL field.</span></span> <span data-ttu-id="61c91-197">Se sua organização mantém um diretório de arquivos acessível pela `.proto` Web, você pode criar clientes apenas definindo esse endereço de URL.</span><span class="sxs-lookup"><span data-stu-id="61c91-197">If your organization maintains a web-accessible directory of `.proto` files, you can create clients just by setting this URL address.</span></span>

<span data-ttu-id="61c91-198">Ao usar o recurso **Adicionar serviço conectado** do Visual Studio, `portfolios.proto` o arquivo é adicionado ao projeto de biblioteca de classes como um *arquivo vinculado*, em vez de copiado, portanto, as alterações no arquivo no projeto de serviço serão aplicadas automaticamente no projeto de cliente.</span><span class="sxs-lookup"><span data-stu-id="61c91-198">When using the Visual Studio **Add Connected Service** feature, the `portfolios.proto` file is added to the Class Library project as a *linked file*, rather than copied, so changes to the file in the service project will automatically be applied in the client project.</span></span> <span data-ttu-id="61c91-199">O `<Protobuf>` elemento`csproj` no arquivo tem a seguinte aparência:</span><span class="sxs-lookup"><span data-stu-id="61c91-199">The `<Protobuf>` element in the `csproj` file looks like this:</span></span>

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

### <a name="use-the-portfolios-service-from-a-client-application"></a><span data-ttu-id="61c91-200">Usar o serviço de portfólios de um aplicativo cliente</span><span class="sxs-lookup"><span data-stu-id="61c91-200">Use the Portfolios service from a client application</span></span>

<span data-ttu-id="61c91-201">O código a seguir é um breve exemplo do uso do cliente gerado em um aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="61c91-201">The following code is a brief example of using the generated client in a console application.</span></span> <span data-ttu-id="61c91-202">Uma exploração mais detalhada do código do cliente gRPC está no final deste capítulo.</span><span class="sxs-lookup"><span data-stu-id="61c91-202">A more detailed exploration of the gRPC client code is at the end of this chapter.</span></span>

```csharp
public class Program
{
    public async Task Main(string[] args)
    {
        GetResponse response;

        using (var channel = GrpcChannel.ForAddress("https://localhost:5001"))
        {
            var client = new Protos.Portfolios.PortfoliosClient(channel);

            response = await client.GetAsync(new GetRequest
            {
                TraderId = args[0],
                PortfolioId = int.Parse(args[1])
            });
        }

        foreach (var item in response.Portfolio.Items)
        {
            Console.WriteLine($"Holding {item.Holding} of Share ID {item.ShareId}.");
        }
    }
}
```

<span data-ttu-id="61c91-203">Agora, você migrou um aplicativo WCF básico para um serviço ASP.NET Core gRPC e criou um cliente para consumir o serviço de um aplicativo .NET.</span><span class="sxs-lookup"><span data-stu-id="61c91-203">Now, you've migrated a basic WCF application to an ASP.NET Core gRPC service and created a client to consume the service from a .NET application.</span></span> <span data-ttu-id="61c91-204">A próxima seção abordará os serviços "duplex" mais envolvidos.</span><span class="sxs-lookup"><span data-stu-id="61c91-204">The next section will cover the more involved "duplex" services.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="61c91-205">[Anterior](create-project.md)
>[Próximo](migrate-duplex-services.md)</span><span class="sxs-lookup"><span data-stu-id="61c91-205">[Previous](create-project.md)
[Next](migrate-duplex-services.md)</span></span>
