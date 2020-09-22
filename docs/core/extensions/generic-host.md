---
title: Host Genérico .NET
author: IEvangelist
description: Saiba mais sobre o host genérico do .NET, que é responsável pela inicialização do aplicativo e pelo gerenciamento do tempo de vida.
ms.author: dapine
ms.date: 09/18/2020
ms.openlocfilehash: c1b22b4490dc54d462482976d1c2e512f812c9a9
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875849"
---
# <a name="net-generic-host"></a><span data-ttu-id="97609-103">Host Genérico .NET</span><span class="sxs-lookup"><span data-stu-id="97609-103">.NET Generic Host</span></span>

<span data-ttu-id="97609-104">Os modelos de serviço de trabalho criam um host genérico .NET, <xref:Microsoft.Extensions.Hosting.HostBuilder> .</span><span class="sxs-lookup"><span data-stu-id="97609-104">The Worker Service templates create a .NET Generic Host, <xref:Microsoft.Extensions.Hosting.HostBuilder>.</span></span> <span data-ttu-id="97609-105">O host genérico pode ser usado com outros tipos de aplicativos .NET, como aplicativos de console.</span><span class="sxs-lookup"><span data-stu-id="97609-105">The Generic Host can be used with other types of .NET applications, such as Console apps.</span></span>

<span data-ttu-id="97609-106">Um *host* é um objeto que encapsula os recursos de um aplicativo, tais como:</span><span class="sxs-lookup"><span data-stu-id="97609-106">A *host* is an object that encapsulates an app's resources, such as:</span></span>

- <span data-ttu-id="97609-107">DI (injeção de dependência)</span><span class="sxs-lookup"><span data-stu-id="97609-107">Dependency injection (DI)</span></span>
- <span data-ttu-id="97609-108">Registrando em log</span><span class="sxs-lookup"><span data-stu-id="97609-108">Logging</span></span>
- <span data-ttu-id="97609-109">Configuração</span><span class="sxs-lookup"><span data-stu-id="97609-109">Configuration</span></span>
- <span data-ttu-id="97609-110">Implementações de `IHostedService`</span><span class="sxs-lookup"><span data-stu-id="97609-110">`IHostedService` implementations</span></span>

<span data-ttu-id="97609-111">Quando um host é iniciado, ele chama <xref:Microsoft.Extensions.Hosting.IHostedService.StartAsync%2A?displayProperty=nameWithType> cada implementação de <xref:Microsoft.Extensions.Hosting.IHostedService> registrado na coleção de serviços hospedados do contêiner de serviço.</span><span class="sxs-lookup"><span data-stu-id="97609-111">When a host starts, it calls <xref:Microsoft.Extensions.Hosting.IHostedService.StartAsync%2A?displayProperty=nameWithType> on each implementation of <xref:Microsoft.Extensions.Hosting.IHostedService> registered in the service container's collection of hosted services.</span></span> <span data-ttu-id="97609-112">Em um aplicativo de serviço de trabalho, todas as `IHostedService` implementações que contêm <xref:Microsoft.Extensions.Hosting.BackgroundService> instâncias têm seus <xref:Microsoft.Extensions.Hosting.BackgroundService.ExecuteAsync%2A?displayProperty=nameWithType> métodos chamados.</span><span class="sxs-lookup"><span data-stu-id="97609-112">In a worker service app, all `IHostedService` implementations that contain <xref:Microsoft.Extensions.Hosting.BackgroundService> instances have their <xref:Microsoft.Extensions.Hosting.BackgroundService.ExecuteAsync%2A?displayProperty=nameWithType> methods called.</span></span>

<span data-ttu-id="97609-113">O principal motivo para incluir todos os recursos interdependentes do aplicativo em um objeto é o gerenciamento de tempo de vida: controle sobre a inicialização do aplicativo e desligamento normal.</span><span class="sxs-lookup"><span data-stu-id="97609-113">The main reason for including all of the app's interdependent resources in one object is lifetime management: control over app startup and graceful shutdown.</span></span> <span data-ttu-id="97609-114">Isso é obtido com o pacote NuGet [Microsoft. Extensions. Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) .</span><span class="sxs-lookup"><span data-stu-id="97609-114">This is achieved with the [Microsoft.Extensions.Hosting](https://www.nuget.org/packages/Microsoft.Extensions.Hosting) NuGet package.</span></span>

## <a name="set-up-a-host"></a><span data-ttu-id="97609-115">Configurar um host</span><span class="sxs-lookup"><span data-stu-id="97609-115">Set up a host</span></span>

<span data-ttu-id="97609-116">O host normalmente é configurado, compilado e executado pelo código na classe `Program`.</span><span class="sxs-lookup"><span data-stu-id="97609-116">The host is typically configured, built, and run by code in the `Program` class.</span></span> <span data-ttu-id="97609-117">O método `Main`:</span><span class="sxs-lookup"><span data-stu-id="97609-117">The `Main` method:</span></span>

- <span data-ttu-id="97609-118">Chama um método <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder> para criar e configurar um objeto construtor.</span><span class="sxs-lookup"><span data-stu-id="97609-118">Calls a <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder> method to create and configure a builder object.</span></span>
- <span data-ttu-id="97609-119">Chamadas <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> para criar uma <xref:Microsoft.Extensions.Hosting.IHost> instância.</span><span class="sxs-lookup"><span data-stu-id="97609-119">Calls <xref:Microsoft.Extensions.Hosting.IHostBuilder.Build> to create an <xref:Microsoft.Extensions.Hosting.IHost> instance.</span></span>
- <span data-ttu-id="97609-120">Chamadas <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.Run%2A> ou <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.RunAsync%2A> método no objeto de host.</span><span class="sxs-lookup"><span data-stu-id="97609-120">Calls <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.Run%2A> or <xref:Microsoft.Extensions.Hosting.HostingAbstractionsHostExtensions.RunAsync%2A> method on the host object.</span></span>

<span data-ttu-id="97609-121">Os modelos de serviço do .NET Worker geram o seguinte código para criar um host genérico:</span><span class="sxs-lookup"><span data-stu-id="97609-121">The .NET Worker Service templates generate the following code to create a Generic Host:</span></span>

```csharp
public class Program
{
    public static void Main(string[] args)
    {
        CreateHostBuilder(args).Build().Run();
    }

    public static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureServices((hostContext, services) =>
            {
                services.AddHostedService<Worker>();
            });
}
```

## <a name="default-builder-settings"></a><span data-ttu-id="97609-122">Configurações do construtor padrão</span><span class="sxs-lookup"><span data-stu-id="97609-122">Default builder settings</span></span>

<span data-ttu-id="97609-123">O método <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A>:</span><span class="sxs-lookup"><span data-stu-id="97609-123">The <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A> method:</span></span>

- <span data-ttu-id="97609-124">Define a raiz do conteúdo como o caminho retornado por <xref:System.IO.Directory.GetCurrentDirectory>.</span><span class="sxs-lookup"><span data-stu-id="97609-124">Sets the content root to the path returned by <xref:System.IO.Directory.GetCurrentDirectory>.</span></span>
- <span data-ttu-id="97609-125">Carrega a [configuração do host](#host-configuration) de:</span><span class="sxs-lookup"><span data-stu-id="97609-125">Loads [host configuration](#host-configuration) from:</span></span>
  - <span data-ttu-id="97609-126">Variáveis de ambiente prefixadas com `DOTNET_` .</span><span class="sxs-lookup"><span data-stu-id="97609-126">Environment variables prefixed with `DOTNET_`.</span></span>
  - <span data-ttu-id="97609-127">Argumentos de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="97609-127">Command-line arguments.</span></span>
- <span data-ttu-id="97609-128">Carrega a configuração do aplicativo de:</span><span class="sxs-lookup"><span data-stu-id="97609-128">Loads app configuration from:</span></span>
  - <span data-ttu-id="97609-129">*appsettings.jsem*.</span><span class="sxs-lookup"><span data-stu-id="97609-129">*appsettings.json*.</span></span>
  - <span data-ttu-id="97609-130">*appsettings.{Environment}.json*.</span><span class="sxs-lookup"><span data-stu-id="97609-130">*appsettings.{Environment}.json*.</span></span>
  - <span data-ttu-id="97609-131">Gerenciador de Segredo quando o aplicativo é executado no ambiente `Development`.</span><span class="sxs-lookup"><span data-stu-id="97609-131">Secret Manager when the app runs in the `Development` environment.</span></span>
  - <span data-ttu-id="97609-132">Variáveis de ambiente.</span><span class="sxs-lookup"><span data-stu-id="97609-132">Environment variables.</span></span>
  - <span data-ttu-id="97609-133">Argumentos de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="97609-133">Command-line arguments.</span></span>
- <span data-ttu-id="97609-134">Adiciona os seguintes provedores de registro em log:</span><span class="sxs-lookup"><span data-stu-id="97609-134">Adds the following logging providers:</span></span>
  - <span data-ttu-id="97609-135">Console</span><span class="sxs-lookup"><span data-stu-id="97609-135">Console</span></span>
  - <span data-ttu-id="97609-136">Depurar</span><span class="sxs-lookup"><span data-stu-id="97609-136">Debug</span></span>
  - <span data-ttu-id="97609-137">EventSource</span><span class="sxs-lookup"><span data-stu-id="97609-137">EventSource</span></span>
  - <span data-ttu-id="97609-138">EventLog (somente quando em execução no Windows)</span><span class="sxs-lookup"><span data-stu-id="97609-138">EventLog (only when running on Windows)</span></span>
- <span data-ttu-id="97609-139">Habilita validação de escopo e [validação de dependência](xref:Microsoft.Extensions.DependencyInjection.ServiceProviderOptions.ValidateOnBuild) quando o ambiente é `Development` .</span><span class="sxs-lookup"><span data-stu-id="97609-139">Enables scope validation and [dependency validation](xref:Microsoft.Extensions.DependencyInjection.ServiceProviderOptions.ValidateOnBuild) when the environment is `Development`.</span></span>

<span data-ttu-id="97609-140">O `ConfigureServices` método expõe a capacidade de adicionar serviços à <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection?displayProperty=nameWithType> instância.</span><span class="sxs-lookup"><span data-stu-id="97609-140">The `ConfigureServices` method exposes the ability to add services to the <xref:Microsoft.Extensions.DependencyInjection.IServiceCollection?displayProperty=nameWithType> instance.</span></span> <span data-ttu-id="97609-141">Posteriormente, esses serviços podem ser disponibilizados da injeção de dependência.</span><span class="sxs-lookup"><span data-stu-id="97609-141">Later, these services can be made available from dependency injection.</span></span>

## <a name="framework-provided-services"></a><span data-ttu-id="97609-142">Serviços fornecidos pela estrutura</span><span class="sxs-lookup"><span data-stu-id="97609-142">Framework-provided services</span></span>

<span data-ttu-id="97609-143">Os seguintes serviços são registrados automaticamente:</span><span class="sxs-lookup"><span data-stu-id="97609-143">The following services are registered automatically:</span></span>

- [<span data-ttu-id="97609-144">IHostApplicationLifetime</span><span class="sxs-lookup"><span data-stu-id="97609-144">IHostApplicationLifetime</span></span>](#ihostapplicationlifetime)
- [<span data-ttu-id="97609-145">IHostLifetime</span><span class="sxs-lookup"><span data-stu-id="97609-145">IHostLifetime</span></span>](#ihostlifetime)
- [<span data-ttu-id="97609-146">IHostEnvironment</span><span class="sxs-lookup"><span data-stu-id="97609-146">IHostEnvironment</span></span>](#ihostenvironment)

## <a name="ihostapplicationlifetime"></a><span data-ttu-id="97609-147">IHostApplicationLifetime</span><span class="sxs-lookup"><span data-stu-id="97609-147">IHostApplicationLifetime</span></span>

<span data-ttu-id="97609-148">Injetar o <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime> serviço em qualquer classe para lidar com tarefas de desligamento de inicialização e de fechamento normal.</span><span class="sxs-lookup"><span data-stu-id="97609-148">Inject the <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime> service into any class to handle post-startup and graceful shutdown tasks.</span></span> <span data-ttu-id="97609-149">Três propriedades na interface são tokens de cancelamento usados para registrar métodos de manipulador de eventos de inicialização e desligamento do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="97609-149">Three properties on the interface are cancellation tokens used to register app start and app stop event handler methods.</span></span> <span data-ttu-id="97609-150">A interface também inclui um método <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication>.</span><span class="sxs-lookup"><span data-stu-id="97609-150">The interface also includes a <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication> method.</span></span>

<span data-ttu-id="97609-151">O exemplo a seguir é uma `IHostedService` implementação que registra `IHostApplicationLifetime` eventos:</span><span class="sxs-lookup"><span data-stu-id="97609-151">The following example is an `IHostedService` implementation that registers `IHostApplicationLifetime` events:</span></span>

:::code language="csharp" source="snippets/configuration/app-lifetime/ExampleHostedService.cs" highlight="18-20":::

<span data-ttu-id="97609-152">O modelo de serviço de trabalho pode ser modificado para adicionar a `ExampleHostedService` implementação:</span><span class="sxs-lookup"><span data-stu-id="97609-152">The Worker Service template could be modified to add the `ExampleHostedService` implementation:</span></span>

:::code language="csharp" source="snippets/configuration/app-lifetime/Program.cs" range="1-16,36" highlight="15":::

<span data-ttu-id="97609-153">O aplicativo gravaria a seguinte saída de exemplo:</span><span class="sxs-lookup"><span data-stu-id="97609-153">The application would write the following sample output:</span></span>

:::code language="csharp" source="snippets/configuration/app-lifetime/Program.cs" range="17-35":::

## <a name="ihostlifetime"></a><span data-ttu-id="97609-154">IHostLifetime</span><span class="sxs-lookup"><span data-stu-id="97609-154">IHostLifetime</span></span>

<span data-ttu-id="97609-155">A implementação <xref:Microsoft.Extensions.Hosting.IHostLifetime> controla quando o host é iniciado e quando ele é interrompido.</span><span class="sxs-lookup"><span data-stu-id="97609-155">The <xref:Microsoft.Extensions.Hosting.IHostLifetime> implementation controls when the host starts and when it stops.</span></span> <span data-ttu-id="97609-156">A última implementação registrada é usada.</span><span class="sxs-lookup"><span data-stu-id="97609-156">The last implementation registered is used.</span></span>

<span data-ttu-id="97609-157">`Microsoft.Extensions.Hosting.Internal.ConsoleLifetime` é a implementação `IHostLifetime` padrão.</span><span class="sxs-lookup"><span data-stu-id="97609-157">`Microsoft.Extensions.Hosting.Internal.ConsoleLifetime` is the default `IHostLifetime` implementation.</span></span> <span data-ttu-id="97609-158">`ConsoleLifetime`:</span><span class="sxs-lookup"><span data-stu-id="97609-158">`ConsoleLifetime`:</span></span>

- <span data-ttu-id="97609-159">Escuta <kbd>Ctrl</kbd> + <kbd>C</kbd>, [SIGINT](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGINT)ou [SIGTERM](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGTERM) e chama <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication%2A> para iniciar o processo de desligamento.</span><span class="sxs-lookup"><span data-stu-id="97609-159">Listens for <kbd>Ctrl</kbd>+<kbd>C</kbd>, [SIGINT](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGINT), or [SIGTERM](https://en.wikipedia.org/wiki/Signal_(IPC)#SIGTERM) and calls <xref:Microsoft.Extensions.Hosting.IHostApplicationLifetime.StopApplication%2A> to start the shutdown process.</span></span>
- <span data-ttu-id="97609-160">Desbloqueia extensões como `RunAsync` e `WaitForShutdownAsync` .</span><span class="sxs-lookup"><span data-stu-id="97609-160">Unblocks extensions such as `RunAsync` and `WaitForShutdownAsync`.</span></span>

## <a name="ihostenvironment"></a><span data-ttu-id="97609-161">IHostEnvironment</span><span class="sxs-lookup"><span data-stu-id="97609-161">IHostEnvironment</span></span>

<span data-ttu-id="97609-162">Insira o <xref:Microsoft.Extensions.Hosting.IHostEnvironment> serviço em uma classe para obter informações sobre as seguintes configurações:</span><span class="sxs-lookup"><span data-stu-id="97609-162">Inject the <xref:Microsoft.Extensions.Hosting.IHostEnvironment> service into a class to get information about the following settings:</span></span>

- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ApplicationName?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ContentRootFileProvider?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.ContentRootPath?displayProperty=nameWithType>
- <xref:Microsoft.Extensions.Hosting.IHostEnvironment.EnvironmentName?displayProperty=nameWithType>

## <a name="host-configuration"></a><span data-ttu-id="97609-163">Configuração do host</span><span class="sxs-lookup"><span data-stu-id="97609-163">Host configuration</span></span>

<span data-ttu-id="97609-164">A configuração do host é usada para as propriedades da implementação <xref:Microsoft.Extensions.Hosting.IHostEnvironment>.</span><span class="sxs-lookup"><span data-stu-id="97609-164">Host configuration is used for the properties of the <xref:Microsoft.Extensions.Hosting.IHostEnvironment> implementation.</span></span>

<span data-ttu-id="97609-165">A configuração do host está disponível por meio de [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration) dentro de <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A>.</span><span class="sxs-lookup"><span data-stu-id="97609-165">Host configuration is available from [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration) inside <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A>.</span></span> <span data-ttu-id="97609-166">Após `ConfigureAppConfiguration`, `HostBuilderContext.Configuration` é substituído com a configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="97609-166">After `ConfigureAppConfiguration`, `HostBuilderContext.Configuration` is replaced with the app config.</span></span>

<span data-ttu-id="97609-167">Para adicionar a configuração do host, chame <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureHostConfiguration%2A> em `IHostBuilder`.</span><span class="sxs-lookup"><span data-stu-id="97609-167">To add host configuration, call <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureHostConfiguration%2A> on `IHostBuilder`.</span></span> <span data-ttu-id="97609-168">`ConfigureHostConfiguration` pode ser chamado várias vezes com resultados aditivos.</span><span class="sxs-lookup"><span data-stu-id="97609-168">`ConfigureHostConfiguration` can be called multiple times with additive results.</span></span> <span data-ttu-id="97609-169">O host usa a opção que define um valor por último em uma chave determinada.</span><span class="sxs-lookup"><span data-stu-id="97609-169">The host uses whichever option sets a value last on a given key.</span></span>

<span data-ttu-id="97609-170">O exemplo a seguir cria a configuração de host:</span><span class="sxs-lookup"><span data-stu-id="97609-170">The following example creates host configuration:</span></span>

:::code language="csharp" source="snippets/configuration/console-host/Program.cs" highlight="13-19":::

## <a name="app-configuration"></a><span data-ttu-id="97609-171">Configuração do aplicativo</span><span class="sxs-lookup"><span data-stu-id="97609-171">App configuration</span></span>

<span data-ttu-id="97609-172">A configuração de aplicativo é criada chamando <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> em `IHostBuilder`.</span><span class="sxs-lookup"><span data-stu-id="97609-172">App configuration is created by calling <xref:Microsoft.Extensions.Hosting.HostBuilder.ConfigureAppConfiguration%2A> on `IHostBuilder`.</span></span> <span data-ttu-id="97609-173">`ConfigureAppConfiguration` pode ser chamado várias vezes com resultados aditivos.</span><span class="sxs-lookup"><span data-stu-id="97609-173">`ConfigureAppConfiguration` can be called multiple times with additive results.</span></span> <span data-ttu-id="97609-174">O aplicativo usa a opção que define um valor por último em uma chave determinada.</span><span class="sxs-lookup"><span data-stu-id="97609-174">The app uses whichever option sets a value last on a given key.</span></span>

<span data-ttu-id="97609-175">A configuração criada pelo `ConfigureAppConfiguration` está disponível em [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration%2A) para operações subsequentes e como um serviço da DI.</span><span class="sxs-lookup"><span data-stu-id="97609-175">The configuration created by `ConfigureAppConfiguration` is available at [HostBuilderContext.Configuration](xref:Microsoft.Extensions.Hosting.HostBuilderContext.Configuration%2A) for subsequent operations and as a service from DI.</span></span> <span data-ttu-id="97609-176">A configuração do host também é adicionada à configuração do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="97609-176">The host configuration is also added to the app configuration.</span></span>

<span data-ttu-id="97609-177">Para obter mais informações, consulte [Configuration in .net](configuration.md).</span><span class="sxs-lookup"><span data-stu-id="97609-177">For more information, see [Configuration in .NET](configuration.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="97609-178">Confira também</span><span class="sxs-lookup"><span data-stu-id="97609-178">See also</span></span>

- [<span data-ttu-id="97609-179">Configuração no .NET</span><span class="sxs-lookup"><span data-stu-id="97609-179">Configuration in .NET</span></span>](configuration.md)
- [<span data-ttu-id="97609-180">Host da Web do ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="97609-180">ASP.NET Core Web Host</span></span>](/aspnet/core/fundamentals/host/web-host)
