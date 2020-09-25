---
title: Usar injeção de dependência no .NET
description: Saiba como usar a injeção de dependência em seus aplicativos .NET.
author: IEvangelist
ms.author: dapine
ms.date: 09/23/2020
ms.topic: tutorial
ms.openlocfilehash: f2298cb0be6d555a7636903dc251f022a6a62a43
ms.sourcegitcommit: c04535ad05e374fb269fcfc6509217755fbc0d54
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2020
ms.locfileid: "91247879"
---
# <a name="tutorial-use-dependency-injection-in-net"></a><span data-ttu-id="7c827-103">Tutorial: usar injeção de dependência no .NET</span><span class="sxs-lookup"><span data-stu-id="7c827-103">Tutorial: Use dependency injection in .NET</span></span>

<span data-ttu-id="7c827-104">Este tutorial mostra como usar [injeção de dependência (di) no .net](dependency-injection.md).</span><span class="sxs-lookup"><span data-stu-id="7c827-104">This tutorial shows how to use [dependency injection (DI) in .NET](dependency-injection.md).</span></span> <span data-ttu-id="7c827-105">Com *o Microsoft Extensions*, di é um cidadão de primeira classe onde os serviços são adicionados e configurados em um <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> .</span><span class="sxs-lookup"><span data-stu-id="7c827-105">With *Microsoft Extensions*, DI is a first-class citizen where services are added and configured in an <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="7c827-106">A <xref:Microsoft.Extensions.Hosting.IHost> interface expõe a <xref:System.IServiceProvider> instância, que atua como um contêiner de todos os serviços registrados.</span><span class="sxs-lookup"><span data-stu-id="7c827-106">The <xref:Microsoft.Extensions.Hosting.IHost> interface exposes the <xref:System.IServiceProvider> instance, which acts as a container of all the registered services.</span></span>

<span data-ttu-id="7c827-107">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="7c827-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="7c827-108">Criar um aplicativo de console .NET que usa injeção de dependência</span><span class="sxs-lookup"><span data-stu-id="7c827-108">Create a .NET console app that uses dependency injection</span></span>
> - <span data-ttu-id="7c827-109">Criar e configurar um [host genérico](generic-host.md)</span><span class="sxs-lookup"><span data-stu-id="7c827-109">Build and configure a [Generic Host](generic-host.md)</span></span>
> - <span data-ttu-id="7c827-110">Escrever várias interfaces e implementações correspondentes</span><span class="sxs-lookup"><span data-stu-id="7c827-110">Write several interfaces and corresponding implementations</span></span>
> - <span data-ttu-id="7c827-111">Usar o tempo de vida do serviço e o escopo para DI</span><span class="sxs-lookup"><span data-stu-id="7c827-111">Use service lifetime and scoping for DI</span></span>

## <a name="prerequisites"></a><span data-ttu-id="7c827-112">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="7c827-112">Prerequisites</span></span>

- <span data-ttu-id="7c827-113">[SDK do .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core) ou uma versão posterior.</span><span class="sxs-lookup"><span data-stu-id="7c827-113">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="7c827-114">Um ambiente de desenvolvimento integrado (IDE), [Visual Studio, Visual Studio Code ou Visual Studio para Mac](https://visualstudio.microsoft.com) são opções válidas.</span><span class="sxs-lookup"><span data-stu-id="7c827-114">An Integrated Development Environment (IDE), [Visual Studio, Visual Studio Code, or Visual Studio for Mac](https://visualstudio.microsoft.com) are all valid choices.</span></span>
- <span data-ttu-id="7c827-115">Familiaridade com a criação de novos aplicativos .NET e a instalação de pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="7c827-115">Familiarity with creating new .NET applications and installing NuGet packages.</span></span>

## <a name="create-a-new-console-application"></a><span data-ttu-id="7c827-116">Criar um novo aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="7c827-116">Create a new console application</span></span>

<span data-ttu-id="7c827-117">Usando o comando [dotnet New](../tools/dotnet-new.md) ou um assistente de novo projeto do IDE, crie um novo aplicativo de console .NET chamado **ConsoleDI. example**.</span><span class="sxs-lookup"><span data-stu-id="7c827-117">Using either the [dotnet new](../tools/dotnet-new.md) command or an IDE new project wizard, create a new .NET console application named **ConsoleDI.Example**.</span></span> <span data-ttu-id="7c827-118">Adicione o pacote NuGet [Microsoft. Extensions. Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) ao projeto.</span><span class="sxs-lookup"><span data-stu-id="7c827-118">Add the [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet package to the project.</span></span>

## <a name="add-interfaces"></a><span data-ttu-id="7c827-119">Adicionar interfaces</span><span class="sxs-lookup"><span data-stu-id="7c827-119">Add interfaces</span></span>

<span data-ttu-id="7c827-120">Adicione as seguintes interfaces ao diretório raiz do projeto:</span><span class="sxs-lookup"><span data-stu-id="7c827-120">Add the following interfaces to the project root directory:</span></span>

<span data-ttu-id="7c827-121">*IOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="7c827-121">*IOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/IOperation.cs":::

<span data-ttu-id="7c827-122">A `IOperation` interface define uma única `OperationId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="7c827-122">The `IOperation` interface defines a single `OperationId` property.</span></span>

<span data-ttu-id="7c827-123">*ITransientOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="7c827-123">*ITransientOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/ITransientOperation.cs":::

<span data-ttu-id="7c827-124">*IScopedOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="7c827-124">*IScopedOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/IScopedOperation.cs":::

<span data-ttu-id="7c827-125">*ISingletonOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="7c827-125">*ISingletonOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/ISingletonOperation.cs":::

<span data-ttu-id="7c827-126">Todas as subinterfaces de `IOperation` nome do seu tempo de vida de serviço pretendido.</span><span class="sxs-lookup"><span data-stu-id="7c827-126">All of the subinterfaces of `IOperation` name their intended service lifetime.</span></span> <span data-ttu-id="7c827-127">Por exemplo, "transitório" ou "singleton".</span><span class="sxs-lookup"><span data-stu-id="7c827-127">For example, "Transient" or "Singleton".</span></span>

## <a name="add-default-implementation"></a><span data-ttu-id="7c827-128">Adicionar implementação padrão</span><span class="sxs-lookup"><span data-stu-id="7c827-128">Add default implementation</span></span>

<span data-ttu-id="7c827-129">Adicione a seguinte implementação padrão para as várias operações:</span><span class="sxs-lookup"><span data-stu-id="7c827-129">Add the following default implementation for the various operations:</span></span>

<span data-ttu-id="7c827-130">*DefaultOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="7c827-130">*DefaultOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/DefaultOperation.cs":::

<span data-ttu-id="7c827-131">O `DefaultOperation` implementa todas as interfaces nomeadas/de marcador e inicializa a `OperationId` propriedade para os últimos quatro caracteres de um novo GUID (identificador global exclusivo).</span><span class="sxs-lookup"><span data-stu-id="7c827-131">The `DefaultOperation` implements all of the named/marker interfaces and initializes the `OperationId` property to the last four characters of a new globally unique identifier (GUID).</span></span>

## <a name="add-service-that-requires-di"></a><span data-ttu-id="7c827-132">Adicionar serviço que requer DI</span><span class="sxs-lookup"><span data-stu-id="7c827-132">Add service that requires DI</span></span>

<span data-ttu-id="7c827-133">Adicione o seguinte objeto de agente de operação, que atua como um serviço para o aplicativo de console:</span><span class="sxs-lookup"><span data-stu-id="7c827-133">Add the following operation logger object, which acts as a service to your console application:</span></span>

<span data-ttu-id="7c827-134">*OperationLogger.cs*</span><span class="sxs-lookup"><span data-stu-id="7c827-134">*OperationLogger.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/OperationLogger.cs":::

<span data-ttu-id="7c827-135">O `OperationLogger` define um construtor que requer cada uma das interfaces de marcador mencionadas anteriormente, ou seja,, `ITransientOperation` `IScopedOperation` e `ISingletonOperation` .</span><span class="sxs-lookup"><span data-stu-id="7c827-135">The `OperationLogger` defines a constructor that requires each of the aforementioned marker interfaces, that is; `ITransientOperation`, `IScopedOperation`, and `ISingletonOperation`.</span></span> <span data-ttu-id="7c827-136">O objeto expõe um único método que permite ao consumidor registrar as operações com um determinado `scope` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7c827-136">The object exposes a single method that allows the consumer to log the operations with a given `scope` parameter.</span></span> <span data-ttu-id="7c827-137">Quando invocado, o `LogOperations` método registrará em log o identificador exclusivo de cada operação com a cadeia de caracteres e a mensagem do escopo.</span><span class="sxs-lookup"><span data-stu-id="7c827-137">When invoked, the `LogOperations` method will log each operation's unique identifier with the scope string and message.</span></span>

## <a name="register-services-for-di"></a><span data-ttu-id="7c827-138">Registrar serviços para DI</span><span class="sxs-lookup"><span data-stu-id="7c827-138">Register services for DI</span></span>

<span data-ttu-id="7c827-139">Por fim, atualize o arquivo *Program.cs* para corresponder ao seguinte:</span><span class="sxs-lookup"><span data-stu-id="7c827-139">Finally, update the *Program.cs* file to match following:</span></span>

:::code language="csharp" source="snippets/configuration/console-di/Program.cs" range="1-18,35-60" highlight="22-26":::

<span data-ttu-id="7c827-140">O aplicativo:</span><span class="sxs-lookup"><span data-stu-id="7c827-140">The application:</span></span>

- <span data-ttu-id="7c827-141">Cria uma <xref:Microsoft.Extensions.Hosting.IHostBuilder> instância com as [configurações padrão do fichário](generic-host.md#default-builder-settings).</span><span class="sxs-lookup"><span data-stu-id="7c827-141">Creates an <xref:Microsoft.Extensions.Hosting.IHostBuilder> instance with the [default binder settings](generic-host.md#default-builder-settings).</span></span>
- <span data-ttu-id="7c827-142">Configura os serviços e os adiciona com o tempo de vida do serviço correspondente.</span><span class="sxs-lookup"><span data-stu-id="7c827-142">Configures services and adds them with their corresponding service lifetime.</span></span>
- <span data-ttu-id="7c827-143">Chama <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> e atribui uma instância do <xref:Microsoft.Extensions.Hosting.IHost> .</span><span class="sxs-lookup"><span data-stu-id="7c827-143">Calls <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> and assigns an instance of <xref:Microsoft.Extensions.Hosting.IHost>.</span></span>
- <span data-ttu-id="7c827-144">Chamadas `ExemplifyScoping` , passando no <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7c827-144">Calls `ExemplifyScoping`, passing in the <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType>.</span></span>

## <a name="conclusion"></a><span data-ttu-id="7c827-145">Conclusão</span><span class="sxs-lookup"><span data-stu-id="7c827-145">Conclusion</span></span>

<span data-ttu-id="7c827-146">O aplicativo produz uma saída semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="7c827-146">The application produces output similar to the following example:</span></span>

```console
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): ITransientOperation [ 80f4...Always different        ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): IScopedOperation    [ c878...Changes only with scope ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
...
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): ITransientOperation [ f3c0...Always different        ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): IScopedOperation    [ c878...Changes only with scope ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]

Scope 2-Call 1 .GetRequiredService<OperationLogger>(): ITransientOperation [ f9af...Always different        ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): IScopedOperation    [ 2bd0...Changes only with scope ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
...
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): ITransientOperation [ fa65...Always different        ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): IScopedOperation    [ 2bd0...Changes only with scope ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): ISingletonOperation [ 1586...Always the same         ]
```

<span data-ttu-id="7c827-147">Na saída do aplicativo, você pode ver que:</span><span class="sxs-lookup"><span data-stu-id="7c827-147">From the application output, you can see that:</span></span>

- <span data-ttu-id="7c827-148">As operações transitórias são sempre diferentes, o que significa que uma nova instância é criada com cada recuperação do serviço.</span><span class="sxs-lookup"><span data-stu-id="7c827-148">Transient operations are always different, meaning a new instance is created with every retrieval of the service.</span></span>
- <span data-ttu-id="7c827-149">As operações com escopo são alteradas somente com um novo escopo, mas são a mesma instância dentro de um escopo.</span><span class="sxs-lookup"><span data-stu-id="7c827-149">Scoped operations change only with a new scope, but are the same instance within a scope.</span></span>
- <span data-ttu-id="7c827-150">As operações singleton são sempre as mesmas, o que significa que uma nova instância é criada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="7c827-150">Singleton operations are always the same, meaning a new instance is only created once.</span></span>

## <a name="next-steps"></a><span data-ttu-id="7c827-151">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="7c827-151">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="7c827-152">Diretrizes de injeção de dependência</span><span class="sxs-lookup"><span data-stu-id="7c827-152">Dependency injection guidelines</span></span>](dependency-injection-guidelines.md)
