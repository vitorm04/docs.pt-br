---
title: Novidades do .NET Core 2.2
description: Conheça os novos recursos do .NET Core 2.2.
dev_langs:
- csharp
- vb
ms.date: 12/04/2018
ms.openlocfilehash: 917b51e0cf36cca45135fda4a084eb2bca62e835
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73100689"
---
# <a name="whats-new-in-net-core-22"></a><span data-ttu-id="7e29c-103">Novidades do .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="7e29c-103">What's new in .NET Core 2.2</span></span>

<span data-ttu-id="7e29c-104">O .NET Core 2.2 inclui aprimoramentos na implantação do aplicativo, na manipulação de eventos para serviços de tempo de execução, na autenticação de Bancos de Dados SQL do Azure, no desempenho do compilador JIT e na injeção de código antes da execução do método `Main`.</span><span class="sxs-lookup"><span data-stu-id="7e29c-104">.NET Core 2.2 includes enhancements in application deployment, event handling for runtime services, authentication to Azure SQL databases, JIT compiler performance, and code injection prior to the execution of the `Main` method.</span></span>

## <a name="new-deployment-mode"></a><span data-ttu-id="7e29c-105">Novo modo de implantação</span><span class="sxs-lookup"><span data-stu-id="7e29c-105">New deployment mode</span></span>

<span data-ttu-id="7e29c-106">A partir do .NET Core 2.2, você pode implantar [executáveis dependentes da estrutura](../deploying/index.md#framework-dependent-executables-fde), que são arquivos **.exe** em vez de arquivos **.dll**.</span><span class="sxs-lookup"><span data-stu-id="7e29c-106">Starting with .NET Core 2.2, you can deploy [framework-dependent executables](../deploying/index.md#framework-dependent-executables-fde), which are **.exe** files instead of **.dll** files.</span></span> <span data-ttu-id="7e29c-107">Com uma funcionalidade semelhante às implantações dependentes de estrutura, os FDEs (executáveis dependentes de estrutura) ainda contam com a presença de uma versão compartilhada de todo o sistema do .NET Core para executar.</span><span class="sxs-lookup"><span data-stu-id="7e29c-107">Functionally similar to framework-dependent deployments, framework-dependent executables (FDE) still rely on the presence of a shared system-wide version of .NET Core to run.</span></span> <span data-ttu-id="7e29c-108">Seu aplicativo contém apenas seu código e quaisquer dependências de terceiros.</span><span class="sxs-lookup"><span data-stu-id="7e29c-108">Your app contains only your code and any third-party dependencies.</span></span> <span data-ttu-id="7e29c-109">Ao contrário de implantações dependentes de estrutura, os FDEs são específicos da plataforma.</span><span class="sxs-lookup"><span data-stu-id="7e29c-109">Unlike framework-dependent deployments, FDEs are platform-specific.</span></span>

<span data-ttu-id="7e29c-110">Esse novo modo de implantação tem a vantagem distinta da criar um executável em vez de uma biblioteca, o que significa que você pode executar seu aplicativo diretamente, sem invocar `dotnet` primeiro.</span><span class="sxs-lookup"><span data-stu-id="7e29c-110">This new deployment mode has the distinct advantage of building an executable instead of a library, which means you can run your app directly without invoking `dotnet` first.</span></span>

## <a name="core"></a><span data-ttu-id="7e29c-111">Núcleo</span><span class="sxs-lookup"><span data-stu-id="7e29c-111">Core</span></span>

<span data-ttu-id="7e29c-112">**Manipulação de eventos nos serviços de tempo de execução**</span><span class="sxs-lookup"><span data-stu-id="7e29c-112">**Handling events in runtime services**</span></span>

<span data-ttu-id="7e29c-113">Muitas vezes, convém monitorar o uso dos serviços de runtime do seu aplicativo, como o GC, o JIT e o ThreadPool, para entender como eles afetam seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7e29c-113">You may often want to monitor your application's use of runtime services, such as the GC, JIT, and ThreadPool, to understand how they impact your application.</span></span><span data-ttu-id="7e29c-114"> Em sistemas Windows, isso é comumente feito monitorando os eventos ETW do processo atual.</span><span class="sxs-lookup"><span data-stu-id="7e29c-114"> On Windows systems, this is commonly done by monitoring the ETW events of the current process.</span></span><span data-ttu-id="7e29c-115"> Embora isso continue funcionando bem, nem sempre é possível usar o ETW se você estiver executando em um ambiente de baixo privilégio ou no Linux ou no macOS.</span><span class="sxs-lookup"><span data-stu-id="7e29c-115"> While this continues to work well, it's not always possible to use ETW if you're running in a low-privilege environment or on Linux or macOS.</span></span> 

<span data-ttu-id="7e29c-116">A partir do .NET Core 2.2, os eventos de CoreCLR podem ser consumidos usando a classe <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="7e29c-116">Starting with .NET Core 2.2, CoreCLR events can now be consumed using the <xref:System.Diagnostics.Tracing.EventListener?displayProperty=nameWithType> class.</span></span> <span data-ttu-id="7e29c-117">Esses eventos descrevem o comportamento desses serviços de runtime como GC, JIT, ThreadPool e interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="7e29c-117">These events describe the behavior of such runtime services as GC, JIT, ThreadPool, and interop.</span></span> <span data-ttu-id="7e29c-118">Esses são os mesmos eventos são expostos como parte do provedor ETW CoreCLR.</span><span class="sxs-lookup"><span data-stu-id="7e29c-118">These are the same events that are exposed as part of the CoreCLR ETW provider.</span></span><span data-ttu-id="7e29c-119">  Isso permite que os aplicativos consumam esses eventos ou usem um mecanismo de transporte para enviá-los a um serviço de agregação de telemetria.</span><span class="sxs-lookup"><span data-stu-id="7e29c-119">  This allows for applications to consume these events or use a transport mechanism to send them to a telemetry aggregation service.</span></span> <span data-ttu-id="7e29c-120">Veja como assinar eventos no exemplo de código a seguir:</span><span class="sxs-lookup"><span data-stu-id="7e29c-120">You can see how to subscribe to events in the following code sample:</span></span>

```csharp
internal sealed class SimpleEventListener : EventListener
{
    // Called whenever an EventSource is created.
    protected override void OnEventSourceCreated(EventSource eventSource)
    {
        // Watch for the .NET runtime EventSource and enable all of its events.
        if (eventSource.Name.Equals("Microsoft-Windows-DotNETRuntime"))
        {
            EnableEvents(eventSource, EventLevel.Verbose, (EventKeywords)(-1));
        }
    }

    // Called whenever an event is written.
    protected override void OnEventWritten(EventWrittenEventArgs eventData)
    {
        // Write the contents of the event to the console.
        Console.WriteLine($"ThreadID = {eventData.OSThreadId} ID = {eventData.EventId} Name = {eventData.EventName}");
        for (int i = 0; i < eventData.Payload.Count; i++)
        {
            string payloadString = eventData.Payload[i]?.ToString() ?? string.Empty;
            Console.WriteLine($"\tName = \"{eventData.PayloadNames[i]}\" Value = \"{payloadString}\"");
        }
        Console.WriteLine("\n");
    }
}
```

<span data-ttu-id="7e29c-121">Além disso, o .NET Core 2.2 adiciona as duas propriedades a seguir à classe <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> para fornecer informações adicionais sobre eventos ETW:</span><span class="sxs-lookup"><span data-stu-id="7e29c-121">In addition, .NET Core 2.2 adds the following two properties to the <xref:System.Diagnostics.Tracing.EventWrittenEventArgs> class to provide additional information about ETW events:</span></span>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.OSThreadId?displayProperty=nameWithType>

- <xref:System.Diagnostics.Tracing.EventWrittenEventArgs.TimeStamp?displayProperty=nameWithType>

## <a name="data"></a><span data-ttu-id="7e29c-122">Dados</span><span class="sxs-lookup"><span data-stu-id="7e29c-122">Data</span></span>

<span data-ttu-id="7e29c-123">**Autenticação do AAD para Bancos de Dados SQL do Azure com a propriedade SqlConnection.AccessToken**</span><span class="sxs-lookup"><span data-stu-id="7e29c-123">**AAD authentication to Azure SQL databases with the SqlConnection.AccessToken property**</span></span>

<span data-ttu-id="7e29c-124">A partir do .NET Core 2.2, um token de acesso emitido pelo Azure Active Directory pode ser usado para autenticar em um Banco de Dados SQL do Azure.</span><span class="sxs-lookup"><span data-stu-id="7e29c-124">Starting with .NET Core 2.2, an access token issued by Azure Active Directory can be used to authenticate to an Azure SQL database.</span></span> <span data-ttu-id="7e29c-125">Para dar suporte a tokens de acesso, a propriedade <xref:System.Data.SqlClient.SqlConnection.AccessToken> foi adicionada à classe <xref:System.Data.SqlClient.SqlConnection>.</span><span class="sxs-lookup"><span data-stu-id="7e29c-125">To support access tokens, the <xref:System.Data.SqlClient.SqlConnection.AccessToken> property has been added to the <xref:System.Data.SqlClient.SqlConnection> class.</span></span> <span data-ttu-id="7e29c-126">Para aproveitar a autenticação do AAD, baixe a versão 4.6 do pacote NuGet System.Data.SqlClient.</span><span class="sxs-lookup"><span data-stu-id="7e29c-126">To take advantage of AAD authentication, download version 4.6 of the System.Data.SqlClient NuGet package.</span></span> <span data-ttu-id="7e29c-127">Para usar o recurso, obtenha o valor do token de acesso usando a [Biblioteca de Autenticação do Active Directory para .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) contida no pacote NuGet [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/).</span><span class="sxs-lookup"><span data-stu-id="7e29c-127">In order to use the feature, you can obtain the access token value using the [Active Directory Authentication Library for .NET](https://github.com/AzureAD/azure-activedirectory-library-for-dotnet) contained in the [`Microsoft.IdentityModel.Clients.ActiveDirectory`](https://www.nuget.org/packages/Microsoft.IdentityModel.Clients.ActiveDirectory/) NuGet package.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="7e29c-128">Melhorias do compilador JIT</span><span class="sxs-lookup"><span data-stu-id="7e29c-128">JIT compiler improvements</span></span>

<span data-ttu-id="7e29c-129">**A compilação em camadas permanece um recurso ativado mediante consentimento**</span><span class="sxs-lookup"><span data-stu-id="7e29c-129">**Tiered compilation remains an opt-in feature**</span></span>

<span data-ttu-id="7e29c-130">No .NET Core 2.1, o compilador JIT implementou uma nova tecnologia compiladora, a *compilação hierárquica*, como um recurso ativado mediante consentimento.</span><span class="sxs-lookup"><span data-stu-id="7e29c-130">In .NET Core 2.1, the JIT compiler implemented a new compiler technology, *tiered compilation*, as an opt-in feature.</span></span> <span data-ttu-id="7e29c-131">O objetivo da compilação em camadas é melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="7e29c-131">The goal of tiered compilation is improved performance.</span></span> <span data-ttu-id="7e29c-132">Uma das tarefas importantes executadas pelo compilador JIT é otimizar a execução de código.</span><span class="sxs-lookup"><span data-stu-id="7e29c-132">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="7e29c-133">No entanto, para caminhos de código pouco usados, o compilador pode gastar mais tempo otimizando o código do que o runtime gasta executando código não otimizado.</span><span class="sxs-lookup"><span data-stu-id="7e29c-133">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends executing unoptimized code.</span></span> <span data-ttu-id="7e29c-134">A compilação em camadas introduz dois estágios na compilação JIT:</span><span class="sxs-lookup"><span data-stu-id="7e29c-134">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="7e29c-135">Uma **primeira camada**, que gera código o mais rápido possível.</span><span class="sxs-lookup"><span data-stu-id="7e29c-135">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="7e29c-136">Uma **segunda camada**, que gera código otimizado para os métodos executados com frequência.</span><span class="sxs-lookup"><span data-stu-id="7e29c-136">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="7e29c-137">A segunda camada de compilação é executada em paralelo para melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="7e29c-137">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="7e29c-138">Para saber mais sobre melhoria de desempenho que pode resultar da compilação em camadas, consulte [Anúncio do .NET Core 2.2 Versão prévia 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span><span class="sxs-lookup"><span data-stu-id="7e29c-138">For information on the performance improvement that can result from tiered compilation, see [Announcing .NET Core 2.2 Preview 2](https://devblogs.microsoft.com/dotnet/announcing-net-core-2-2-preview-2/).</span></span>

<span data-ttu-id="7e29c-139">No .NET Core 2.2 Versão prévia 2, a compilação em camadas está habilitada por padrão.</span><span class="sxs-lookup"><span data-stu-id="7e29c-139">In .NET Core 2.2 Preview 2, tiered compilation was enabled by default.</span></span> <span data-ttu-id="7e29c-140">No entanto, decidimos que ainda não estamos prontos para habilitar a compilação em camadas por padrão.</span><span class="sxs-lookup"><span data-stu-id="7e29c-140">However, we've decided that we are still not ready to enable tiered compilation by default.</span></span> <span data-ttu-id="7e29c-141">Portanto, no .NET Core 2.2, a compilação em camadas continua a ser um recurso ativado mediante consentimento.</span><span class="sxs-lookup"><span data-stu-id="7e29c-141">So in .NET Core 2.2, tiered compilation continues to be an opt-in feature.</span></span> <span data-ttu-id="7e29c-142">Para saber mais sobre o consentimento com a compilação em camadas, confira [Aprimoramentos do compilador Jit](dotnet-core-2-1.md#jit-compiler-improvements) em [O que há de novo no .NET Core 2.1](dotnet-core-2-1.md).</span><span class="sxs-lookup"><span data-stu-id="7e29c-142">For information on opting in to tiered compilation, see [Jit compiler improvements](dotnet-core-2-1.md#jit-compiler-improvements) in [What's new in .NET Core 2.1](dotnet-core-2-1.md).</span></span>

## <a name="runtime"></a><span data-ttu-id="7e29c-143">Runtime</span><span class="sxs-lookup"><span data-stu-id="7e29c-143">Runtime</span></span>

<span data-ttu-id="7e29c-144">**Injeção de código antes de executar o método Main**</span><span class="sxs-lookup"><span data-stu-id="7e29c-144">**Injecting code prior to executing the Main method**</span></span>

<span data-ttu-id="7e29c-145">A partir do .NET Core 2.2, você pode usar um gancho de inicialização para injetar código antes da execução do método Main de um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7e29c-145">Starting with .NET Core 2.2, you can use a startup hook to inject code prior to running an application's Main method.</span></span> <span data-ttu-id="7e29c-146">Ganchos de inicialização tornam possível para um host personalizar o comportamento de aplicativos após eles terem sido implantados, sem a necessidade de recompilar ou alterar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="7e29c-146">Startup hooks make it possible for a host to customize the behavior of applications after they have been deployed without needing to recompile or change the application.</span></span>

<span data-ttu-id="7e29c-147">Esperamos que os provedores de hospedagem definam a configuração e a política personalizadas, incluindo configurações que possivelmente influenciam o comportamento de carregamento do ponto de entrada principal, como o comportamento <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> .</span><span class="sxs-lookup"><span data-stu-id="7e29c-147">We expect hosting providers to define custom configuration and policy, including settings that potentially influence the load behavior of the main entry point, such as the <xref:System.Runtime.Loader.AssemblyLoadContext?displayProperty=nameWithType> behavior.</span></span> <span data-ttu-id="7e29c-148">O gancho pode ser usado para configurar a injeção de rastreamento ou de telemetria, para configurar os retornos de chamada para tratamento ou para definir outro comportamento dependente do ambiente.</span><span class="sxs-lookup"><span data-stu-id="7e29c-148">The hook can be used to set up tracing or telemetry injection, to set up callbacks for handling, or to define other environment-dependent behavior.</span></span> <span data-ttu-id="7e29c-149">O gancho é separado do ponto de entrada, para que o código do usuário não precise ser modificado.</span><span class="sxs-lookup"><span data-stu-id="7e29c-149">The hook is separate from the entry point, so that user code doesn't need to be modified.</span></span>

<span data-ttu-id="7e29c-150">Confira [Gancho de inicialização do host](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) para saber mais.</span><span class="sxs-lookup"><span data-stu-id="7e29c-150">See [Host startup hook](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/host-startup-hook.md) for more information.</span></span>

## <a name="see-also"></a><span data-ttu-id="7e29c-151">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e29c-151">See also</span></span>

- [<span data-ttu-id="7e29c-152">Novidades do .NET Core</span><span class="sxs-lookup"><span data-stu-id="7e29c-152">What's new in .NET Core</span></span>](index.md)
- [<span data-ttu-id="7e29c-153">Novidades do ASP.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="7e29c-153">What's new in ASP.NET Core 2.2</span></span>](/aspnet/core/release-notes/aspnetcore-2.2)
- [<span data-ttu-id="7e29c-154">Novos recursos no EF Core 2.2</span><span class="sxs-lookup"><span data-stu-id="7e29c-154">New features in EF Core 2.2</span></span>](/ef/core/what-is-new/ef-core-2.2)
