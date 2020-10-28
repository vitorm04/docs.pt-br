---
title: Usar injeção de dependência no .NET
description: Saiba como usar a injeção de dependência em seus aplicativos .NET.
author: IEvangelist
ms.author: dapine
ms.date: 09/23/2020
ms.topic: tutorial
no-loc:
- ':::no-loc(Transient):::'
- ':::no-loc(Scoped):::'
- ':::no-loc(Singleton):::'
- ':::no-loc(Example):::'
ms.openlocfilehash: 589e15736c07b465fda308b04c91384a2502755c
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888581"
---
# <a name="tutorial-use-dependency-injection-in-net"></a><span data-ttu-id="5fe6c-103">Tutorial: usar injeção de dependência no .NET</span><span class="sxs-lookup"><span data-stu-id="5fe6c-103">Tutorial: Use dependency injection in .NET</span></span>

<span data-ttu-id="5fe6c-104">Este tutorial mostra como usar [injeção de dependência (di) no .net](dependency-injection.md).</span><span class="sxs-lookup"><span data-stu-id="5fe6c-104">This tutorial shows how to use [dependency injection (DI) in .NET](dependency-injection.md).</span></span> <span data-ttu-id="5fe6c-105">Com *o Microsoft Extensions* , di é um cidadão de primeira classe onde os serviços são adicionados e configurados em um <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection> .</span><span class="sxs-lookup"><span data-stu-id="5fe6c-105">With *Microsoft Extensions* , DI is a first-class citizen where services are added and configured in an <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection>.</span></span> <span data-ttu-id="5fe6c-106">A <xref:Microsoft.Extensions.Hosting.IHost> interface expõe a <xref:System.IServiceProvider> instância, que atua como um contêiner de todos os serviços registrados.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-106">The <xref:Microsoft.Extensions.Hosting.IHost> interface exposes the <xref:System.IServiceProvider> instance, which acts as a container of all the registered services.</span></span>

<span data-ttu-id="5fe6c-107">Neste tutorial, você aprenderá como:</span><span class="sxs-lookup"><span data-stu-id="5fe6c-107">In this tutorial, you learn how to:</span></span>

> [!div class="checklist"]
>
> - <span data-ttu-id="5fe6c-108">Criar um aplicativo de console .NET que usa injeção de dependência</span><span class="sxs-lookup"><span data-stu-id="5fe6c-108">Create a .NET console app that uses dependency injection</span></span>
> - <span data-ttu-id="5fe6c-109">Criar e configurar um [host genérico](generic-host.md)</span><span class="sxs-lookup"><span data-stu-id="5fe6c-109">Build and configure a [Generic Host](generic-host.md)</span></span>
> - <span data-ttu-id="5fe6c-110">Escrever várias interfaces e implementações correspondentes</span><span class="sxs-lookup"><span data-stu-id="5fe6c-110">Write several interfaces and corresponding implementations</span></span>
> - <span data-ttu-id="5fe6c-111">Usar o tempo de vida do serviço e o escopo para DI</span><span class="sxs-lookup"><span data-stu-id="5fe6c-111">Use service lifetime and scoping for DI</span></span>

## <a name="prerequisites"></a><span data-ttu-id="5fe6c-112">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="5fe6c-112">Prerequisites</span></span>

- <span data-ttu-id="5fe6c-113">[SDK do .NET Core 3,1](https://dotnet.microsoft.com/download/dotnet-core) ou posterior.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-113">[.NET Core 3.1 SDK](https://dotnet.microsoft.com/download/dotnet-core) or later.</span></span>
- <span data-ttu-id="5fe6c-114">Familiaridade com a criação de novos aplicativos .NET e a instalação de pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-114">Familiarity with creating new .NET applications and installing NuGet packages.</span></span>

## <a name="create-a-new-console-application"></a><span data-ttu-id="5fe6c-115">Criar um novo aplicativo de console</span><span class="sxs-lookup"><span data-stu-id="5fe6c-115">Create a new console application</span></span>

<span data-ttu-id="5fe6c-116">Usando o comando [dotnet New](../tools/dotnet-new.md) ou um assistente de novo projeto do IDE, crie um novo aplicativo de console .NET chamado **ConsoleDI. :::no-loc(Example):::** .</span><span class="sxs-lookup"><span data-stu-id="5fe6c-116">Using either the [dotnet new](../tools/dotnet-new.md) command or an IDE new project wizard, create a new .NET console application named **ConsoleDI.:::no-loc(Example):::** .</span></span> <span data-ttu-id="5fe6c-117">Adicione o pacote NuGet [Microsoft. Extensions. Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) ao projeto.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-117">Add the [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet package to the project.</span></span>

## <a name="add-interfaces"></a><span data-ttu-id="5fe6c-118">Adicionar interfaces</span><span class="sxs-lookup"><span data-stu-id="5fe6c-118">Add interfaces</span></span>

<span data-ttu-id="5fe6c-119">Adicione as seguintes interfaces ao diretório raiz do projeto:</span><span class="sxs-lookup"><span data-stu-id="5fe6c-119">Add the following interfaces to the project root directory:</span></span>

<span data-ttu-id="5fe6c-120">*IOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="5fe6c-120">*IOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/IOperation.cs":::

<span data-ttu-id="5fe6c-121">A `IOperation` interface define uma única `OperationId` propriedade.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-121">The `IOperation` interface defines a single `OperationId` property.</span></span>

<span data-ttu-id="5fe6c-122">*Eu :::no-loc(Transient)::: Operation.cs*</span><span class="sxs-lookup"><span data-stu-id="5fe6c-122">*I:::no-loc(Transient):::Operation.cs*</span></span>

<span data-ttu-id="5fe6c-123">::: linguagem de código = "CSharp" origem = "trechos/configuração/console-di/I :::no-loc(Transient)::: Operation.cs":::</span><span class="sxs-lookup"><span data-stu-id="5fe6c-123">:::code language="csharp" source="snippets/configuration/console-di/I:::no-loc(Transient):::Operation.cs":::</span></span>

<span data-ttu-id="5fe6c-124">*Eu :::no-loc(Scoped)::: Operation.cs*</span><span class="sxs-lookup"><span data-stu-id="5fe6c-124">*I:::no-loc(Scoped):::Operation.cs*</span></span>

<span data-ttu-id="5fe6c-125">::: linguagem de código = "CSharp" origem = "trechos/configuração/console-di/I :::no-loc(Scoped)::: Operation.cs":::</span><span class="sxs-lookup"><span data-stu-id="5fe6c-125">:::code language="csharp" source="snippets/configuration/console-di/I:::no-loc(Scoped):::Operation.cs":::</span></span>

<span data-ttu-id="5fe6c-126">*Eu :::no-loc(Singleton)::: Operation.cs*</span><span class="sxs-lookup"><span data-stu-id="5fe6c-126">*I:::no-loc(Singleton):::Operation.cs*</span></span>

<span data-ttu-id="5fe6c-127">::: linguagem de código = "CSharp" origem = "trechos/configuração/console-di/I :::no-loc(Singleton)::: Operation.cs":::</span><span class="sxs-lookup"><span data-stu-id="5fe6c-127">:::code language="csharp" source="snippets/configuration/console-di/I:::no-loc(Singleton):::Operation.cs":::</span></span>

<span data-ttu-id="5fe6c-128">Todas as subinterfaces de `IOperation` nome do seu tempo de vida de serviço pretendido.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-128">All of the subinterfaces of `IOperation` name their intended service lifetime.</span></span> <span data-ttu-id="5fe6c-129">Por exemplo, " :::no-loc(Transient)::: " ou " :::no-loc(Singleton)::: ".</span><span class="sxs-lookup"><span data-stu-id="5fe6c-129">For example, ":::no-loc(Transient):::" or ":::no-loc(Singleton):::".</span></span>

## <a name="add-default-implementation"></a><span data-ttu-id="5fe6c-130">Adicionar implementação padrão</span><span class="sxs-lookup"><span data-stu-id="5fe6c-130">Add default implementation</span></span>

<span data-ttu-id="5fe6c-131">Adicione a seguinte implementação padrão para as várias operações:</span><span class="sxs-lookup"><span data-stu-id="5fe6c-131">Add the following default implementation for the various operations:</span></span>

<span data-ttu-id="5fe6c-132">*DefaultOperation.cs*</span><span class="sxs-lookup"><span data-stu-id="5fe6c-132">*DefaultOperation.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/DefaultOperation.cs":::

<span data-ttu-id="5fe6c-133">O `DefaultOperation` implementa todas as interfaces do marcador nomeado e inicializa a `OperationId` propriedade para os últimos quatro caracteres de um novo GUID (identificador global exclusivo).</span><span class="sxs-lookup"><span data-stu-id="5fe6c-133">The `DefaultOperation` implements all of the named marker interfaces and initializes the `OperationId` property to the last four characters of a new globally unique identifier (GUID).</span></span>

## <a name="add-service-that-requires-di"></a><span data-ttu-id="5fe6c-134">Adicionar serviço que requer DI</span><span class="sxs-lookup"><span data-stu-id="5fe6c-134">Add service that requires DI</span></span>

<span data-ttu-id="5fe6c-135">Adicione o seguinte objeto de agente de operação, que atua como um serviço para o aplicativo de console:</span><span class="sxs-lookup"><span data-stu-id="5fe6c-135">Add the following operation logger object, which acts as a service to the console app:</span></span>

<span data-ttu-id="5fe6c-136">*OperationLogger.cs*</span><span class="sxs-lookup"><span data-stu-id="5fe6c-136">*OperationLogger.cs*</span></span>

:::code language="csharp" source="snippets/configuration/console-di/OperationLogger.cs":::

<span data-ttu-id="5fe6c-137">O `OperationLogger` define um construtor que requer cada uma das interfaces de marcador mencionadas anteriormente, ou seja,, `I:::no-loc(Transient):::Operation` `I:::no-loc(Scoped):::Operation` e `I:::no-loc(Singleton):::Operation` .</span><span class="sxs-lookup"><span data-stu-id="5fe6c-137">The `OperationLogger` defines a constructor that requires each of the aforementioned marker interfaces, that is; `I:::no-loc(Transient):::Operation`, `I:::no-loc(Scoped):::Operation`, and `I:::no-loc(Singleton):::Operation`.</span></span> <span data-ttu-id="5fe6c-138">O objeto expõe um único método que permite ao consumidor registrar as operações com um determinado `scope` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-138">The object exposes a single method that allows the consumer to log the operations with a given `scope` parameter.</span></span> <span data-ttu-id="5fe6c-139">Quando invocado, o `LogOperations` método registra o identificador exclusivo de cada operação com a cadeia de caracteres e a mensagem do escopo.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-139">When invoked, the `LogOperations` method logs each operation's unique identifier with the scope string and message.</span></span>

## <a name="register-services-for-di"></a><span data-ttu-id="5fe6c-140">Registrar serviços para DI</span><span class="sxs-lookup"><span data-stu-id="5fe6c-140">Register services for DI</span></span>

<span data-ttu-id="5fe6c-141">Atualize *Program.cs* com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="5fe6c-141">Update *Program.cs* with the following code:</span></span>

:::code language="csharp" source="snippets/configuration/console-di/Program.cs" range="1-18,35-60" highlight="22-26":::

<span data-ttu-id="5fe6c-142">O aplicativo:</span><span class="sxs-lookup"><span data-stu-id="5fe6c-142">The app:</span></span>

- <span data-ttu-id="5fe6c-143">Cria uma <xref:Microsoft.Extensions.Hosting.IHostBuilder> instância com as [configurações padrão do fichário](generic-host.md#default-builder-settings).</span><span class="sxs-lookup"><span data-stu-id="5fe6c-143">Creates an <xref:Microsoft.Extensions.Hosting.IHostBuilder> instance with the [default binder settings](generic-host.md#default-builder-settings).</span></span>
- <span data-ttu-id="5fe6c-144">Configura os serviços e os adiciona com o tempo de vida do serviço correspondente.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-144">Configures services and adds them with their corresponding service lifetime.</span></span>
- <span data-ttu-id="5fe6c-145">Chama <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> e atribui uma instância do <xref:Microsoft.Extensions.Hosting.IHost> .</span><span class="sxs-lookup"><span data-stu-id="5fe6c-145">Calls <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> and assigns an instance of <xref:Microsoft.Extensions.Hosting.IHost>.</span></span>
- <span data-ttu-id="5fe6c-146">Chamadas `ExemplifyScoping` , passando no <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="5fe6c-146">Calls `ExemplifyScoping`, passing in the <xref:Microsoft.Extensions.Hosting.IHost.Services?displayProperty=nameWithType>.</span></span>

## <a name="conclusion"></a><span data-ttu-id="5fe6c-147">Conclusão</span><span class="sxs-lookup"><span data-stu-id="5fe6c-147">Conclusion</span></span>

<span data-ttu-id="5fe6c-148">O aplicativo exibe uma saída semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="5fe6c-148">The app displays output similar to the following example:</span></span>

```console
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): I:::no-loc(Transient):::Operation [ 80f4...Always different        ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): I:::no-loc(Scoped):::Operation    [ c878...Changes only with scope ]
Scope 1-Call 1 .GetRequiredService<OperationLogger>(): I:::no-loc(Singleton):::Operation [ 1586...Always the same         ]
...
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): I:::no-loc(Transient):::Operation [ f3c0...Always different        ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): I:::no-loc(Scoped):::Operation    [ c878...Changes only with scope ]
Scope 1-Call 2 .GetRequiredService<OperationLogger>(): I:::no-loc(Singleton):::Operation [ 1586...Always the same         ]

Scope 2-Call 1 .GetRequiredService<OperationLogger>(): I:::no-loc(Transient):::Operation [ f9af...Always different        ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): I:::no-loc(Scoped):::Operation    [ 2bd0...Changes only with scope ]
Scope 2-Call 1 .GetRequiredService<OperationLogger>(): I:::no-loc(Singleton):::Operation [ 1586...Always the same         ]
...
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): I:::no-loc(Transient):::Operation [ fa65...Always different        ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): I:::no-loc(Scoped):::Operation    [ 2bd0...Changes only with scope ]
Scope 2-Call 2 .GetRequiredService<OperationLogger>(): I:::no-loc(Singleton):::Operation [ 1586...Always the same         ]
```

<span data-ttu-id="5fe6c-149">Na saída do aplicativo, você pode ver que:</span><span class="sxs-lookup"><span data-stu-id="5fe6c-149">From the app output, you can see that:</span></span>

- <span data-ttu-id="5fe6c-150">:::no-loc(Transient)::: as operações são sempre diferentes, uma nova instância é criada com cada recuperação do serviço.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-150">:::no-loc(Transient)::: operations are always different, a new instance is created with every retrieval of the service.</span></span>
- <span data-ttu-id="5fe6c-151">:::no-loc(Scoped)::: as operações são alteradas somente com um novo escopo, mas são a mesma instância dentro de um escopo.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-151">:::no-loc(Scoped)::: operations change only with a new scope, but are the same instance within a scope.</span></span>
- <span data-ttu-id="5fe6c-152">:::no-loc(Singleton)::: as operações são sempre as mesmas, uma nova instância é criada apenas uma vez.</span><span class="sxs-lookup"><span data-stu-id="5fe6c-152">:::no-loc(Singleton)::: operations are always the same, a new instance is only created once.</span></span>

## <a name="see-also"></a><span data-ttu-id="5fe6c-153">Veja também</span><span class="sxs-lookup"><span data-stu-id="5fe6c-153">See also</span></span>

* [<span data-ttu-id="5fe6c-154">Diretrizes de injeção de dependência</span><span class="sxs-lookup"><span data-stu-id="5fe6c-154">Dependency injection guidelines</span></span>](dependency-injection-guidelines.md)
* [<span data-ttu-id="5fe6c-155">Injeção de dependência no ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5fe6c-155">Dependency injection in ASP.NET Core</span></span>](/aspnet/core/fundamentals/dependency-injection)
