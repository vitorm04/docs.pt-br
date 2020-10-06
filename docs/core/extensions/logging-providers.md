---
title: Provedores de log no .NET
description: Saiba como a API do provedor de log é usada em aplicativos .NET.
author: IEvangelist
ms.author: dapine
ms.date: 09/25/2020
ms.openlocfilehash: 96a5ece10068e39c991e67a36f22e725d6380af5
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91755883"
---
# <a name="logging-providers-in-net"></a><span data-ttu-id="33ce8-103">Provedores de log no .NET</span><span class="sxs-lookup"><span data-stu-id="33ce8-103">Logging providers in .NET</span></span>

<span data-ttu-id="33ce8-104">Os provedores de log mantêm logs, exceto para o `Console` provedor, que exibe apenas os logs como saída padrão.</span><span class="sxs-lookup"><span data-stu-id="33ce8-104">Logging providers persist logs, except for the `Console` provider, which only displays logs as standard output.</span></span> <span data-ttu-id="33ce8-105">Por exemplo, o provedor do Aplicativo Azure insights armazena logs no Aplicativo Azure insights.</span><span class="sxs-lookup"><span data-stu-id="33ce8-105">For example, the Azure Application Insights provider stores logs in Azure Application Insights.</span></span> <span data-ttu-id="33ce8-106">Vários provedores podem ser habilitados.</span><span class="sxs-lookup"><span data-stu-id="33ce8-106">Multiple providers can be enabled.</span></span>

<span data-ttu-id="33ce8-107">Os modelos de aplicativo do .NET Worker padrão:</span><span class="sxs-lookup"><span data-stu-id="33ce8-107">The default .NET Worker app templates:</span></span>

- <span data-ttu-id="33ce8-108">Use o [host genérico](generic-host.md).</span><span class="sxs-lookup"><span data-stu-id="33ce8-108">Use the [Generic Host](generic-host.md).</span></span>
- <span data-ttu-id="33ce8-109">Chamada <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A> , que adiciona os seguintes provedores de log:</span><span class="sxs-lookup"><span data-stu-id="33ce8-109">Call <xref:Microsoft.Extensions.Hosting.Host.CreateDefaultBuilder%2A>, which adds the following logging providers:</span></span>
  - [<span data-ttu-id="33ce8-110">Console</span><span class="sxs-lookup"><span data-stu-id="33ce8-110">Console</span></span>](#console)
  - [<span data-ttu-id="33ce8-111">Depurar</span><span class="sxs-lookup"><span data-stu-id="33ce8-111">Debug</span></span>](#debug)
  - [<span data-ttu-id="33ce8-112">EventSource</span><span class="sxs-lookup"><span data-stu-id="33ce8-112">EventSource</span></span>](#event-source)
  - <span data-ttu-id="33ce8-113">[EventLog](#windows-eventlog): somente Windows</span><span class="sxs-lookup"><span data-stu-id="33ce8-113">[EventLog](#windows-eventlog): Windows only</span></span>

:::code language="csharp" source="snippets/configuration/console/Program.cs" highlight="12":::

<span data-ttu-id="33ce8-114">O código anterior mostra a `Program` classe criada com os modelos de aplicativo do .net Worker.</span><span class="sxs-lookup"><span data-stu-id="33ce8-114">The preceding code shows the `Program` class created with the .NET Worker app templates.</span></span> <span data-ttu-id="33ce8-115">As várias seções a seguir fornecem exemplos baseados nos modelos de aplicativo do .NET Worker, que usam o host genérico.</span><span class="sxs-lookup"><span data-stu-id="33ce8-115">The next several sections provide samples based on the .NET Worker app templates, which use the Generic Host.</span></span>

<span data-ttu-id="33ce8-116">Para substituir o conjunto padrão de provedores de log adicionados pelo `Host.CreateDefaultBuilder` , chame `ClearProviders` e adicione os provedores de log que você deseja.</span><span class="sxs-lookup"><span data-stu-id="33ce8-116">To override the default set of logging providers added by `Host.CreateDefaultBuilder`, call `ClearProviders` and add the logging providers you want.</span></span> <span data-ttu-id="33ce8-117">Por exemplo, o código a seguir:</span><span class="sxs-lookup"><span data-stu-id="33ce8-117">For example, the following code:</span></span>

- <span data-ttu-id="33ce8-118">Chama <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.ClearProviders%2A> para remover todas as <xref:Microsoft.Extensions.Logging.ILoggerProvider> instâncias do construtor.</span><span class="sxs-lookup"><span data-stu-id="33ce8-118">Calls <xref:Microsoft.Extensions.Logging.LoggingBuilderExtensions.ClearProviders%2A> to remove all the <xref:Microsoft.Extensions.Logging.ILoggerProvider> instances from the builder.</span></span>
- <span data-ttu-id="33ce8-119">Adiciona o provedor de log de [console](#console) .</span><span class="sxs-lookup"><span data-stu-id="33ce8-119">Adds the [Console](#console) logging provider.</span></span>

```csharp
static IHostBuilder CreateHostBuilder(string[] args) =>
    Host.CreateDefaultBuilder(args)
        .ConfigureLogging(logging =>
        {
            logging.ClearProviders();
            logging.AddConsole();
        });
```

<span data-ttu-id="33ce8-120">Para provedores adicionais, consulte:</span><span class="sxs-lookup"><span data-stu-id="33ce8-120">For additional providers, see:</span></span>

- <span data-ttu-id="33ce8-121">[Provedores de log internos](#built-in-logging-providers).</span><span class="sxs-lookup"><span data-stu-id="33ce8-121">[Built-in logging providers](#built-in-logging-providers).</span></span>
- <span data-ttu-id="33ce8-122">[Provedores de log de](#third-party-logging-providers)terceiros.</span><span class="sxs-lookup"><span data-stu-id="33ce8-122">[Third-party logging providers](#third-party-logging-providers).</span></span>

## <a name="configure-a-service-that-depends-on-ilogger"></a><span data-ttu-id="33ce8-123">Configurar um serviço que depende do ILogger</span><span class="sxs-lookup"><span data-stu-id="33ce8-123">Configure a service that depends on ILogger</span></span>

<span data-ttu-id="33ce8-124">Para configurar um serviço que depende do `ILogger<T>` , use a injeção de construtor ou forneça um método de fábrica.</span><span class="sxs-lookup"><span data-stu-id="33ce8-124">To configure a service that depends on `ILogger<T>`, use constructor injection or provide a factory method.</span></span> <span data-ttu-id="33ce8-125">A abordagem do método de fábrica é recomendada somente se não há nenhuma outra opção.</span><span class="sxs-lookup"><span data-stu-id="33ce8-125">The factory method approach is recommended only if there is no other option.</span></span> <span data-ttu-id="33ce8-126">Por exemplo, considere um serviço que precisa de uma `ILogger<T>` instância fornecida por di:</span><span class="sxs-lookup"><span data-stu-id="33ce8-126">For example, consider a service that needs an `ILogger<T>` instance provided by DI:</span></span>

```csharp
.ConfigureServices(services =>
    services.AddSingleton<IExampleService>(container =>
        new DefaultExampleService
        {
            Logger = container.GetRequiredService<ILogger<IExampleService>>()
        }));
```

<span data-ttu-id="33ce8-127">O código anterior é um [Func<IServiceProvider, IExampleService>](/dotnet/api/system.func-2) que é executado pela primeira vez que o contêiner di precisa construir uma instância do `IExampleService` .</span><span class="sxs-lookup"><span data-stu-id="33ce8-127">The preceding code is a [Func<IServiceProvider, IExampleService>](/dotnet/api/system.func-2) that runs the first time the DI container needs to construct an instance of `IExampleService`.</span></span> <span data-ttu-id="33ce8-128">Você pode acessar qualquer um dos serviços registrados dessa maneira.</span><span class="sxs-lookup"><span data-stu-id="33ce8-128">You can access any of the registered services in this way.</span></span>

## <a name="built-in-logging-providers"></a><span data-ttu-id="33ce8-129">Provedores de log internos</span><span class="sxs-lookup"><span data-stu-id="33ce8-129">Built-in logging providers</span></span>

<span data-ttu-id="33ce8-130">As extensões da Microsoft incluem os seguintes provedores de log como parte das bibliotecas de tempo de execução:</span><span class="sxs-lookup"><span data-stu-id="33ce8-130">Microsoft Extensions include the following logging providers as part of the runtime libraries:</span></span>

- [<span data-ttu-id="33ce8-131">Console</span><span class="sxs-lookup"><span data-stu-id="33ce8-131">Console</span></span>](#console)
- [<span data-ttu-id="33ce8-132">Depurar</span><span class="sxs-lookup"><span data-stu-id="33ce8-132">Debug</span></span>](#debug)
- [<span data-ttu-id="33ce8-133">EventSource</span><span class="sxs-lookup"><span data-stu-id="33ce8-133">EventSource</span></span>](#event-source)
- [<span data-ttu-id="33ce8-134">EventLog</span><span class="sxs-lookup"><span data-stu-id="33ce8-134">EventLog</span></span>](#windows-eventlog)

<span data-ttu-id="33ce8-135">Os provedores de log a seguir são fornecidos pela Microsoft, mas não como parte das bibliotecas de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="33ce8-135">The following logging providers are shipped by Microsoft, but not as part of the runtime libraries.</span></span> <span data-ttu-id="33ce8-136">Eles devem ser instalados como pacotes NuGet adicionais.</span><span class="sxs-lookup"><span data-stu-id="33ce8-136">They must be installed as additional NuGet packages.</span></span>

- [<span data-ttu-id="33ce8-137">AzureAppServicesFile e AzureAppServicesBlob</span><span class="sxs-lookup"><span data-stu-id="33ce8-137">AzureAppServicesFile and AzureAppServicesBlob</span></span>](#azure-app-service)
- [<span data-ttu-id="33ce8-138">ApplicationInsights</span><span class="sxs-lookup"><span data-stu-id="33ce8-138">ApplicationInsights</span></span>](#azure-application-insights)

### <a name="console"></a><span data-ttu-id="33ce8-139">Console</span><span class="sxs-lookup"><span data-stu-id="33ce8-139">Console</span></span>

<span data-ttu-id="33ce8-140">O `Console` provedor registra a saída no console.</span><span class="sxs-lookup"><span data-stu-id="33ce8-140">The `Console` provider logs output to the console.</span></span>

### <a name="debug"></a><span data-ttu-id="33ce8-141">Depurar</span><span class="sxs-lookup"><span data-stu-id="33ce8-141">Debug</span></span>

<span data-ttu-id="33ce8-142">O `Debug` provedor grava a saída de log usando a classe [System. Diagnostics. Debug](/dotnet/api/system.diagnostics.debug) .</span><span class="sxs-lookup"><span data-stu-id="33ce8-142">The `Debug` provider writes log output by using the [System.Diagnostics.Debug](/dotnet/api/system.diagnostics.debug) class.</span></span> <span data-ttu-id="33ce8-143">Chamadas para `System.Diagnostics.Debug.WriteLine` gravar no `Debug` provedor.</span><span class="sxs-lookup"><span data-stu-id="33ce8-143">Calls to `System.Diagnostics.Debug.WriteLine` write to the `Debug` provider.</span></span>

<span data-ttu-id="33ce8-144">No Linux, o `Debug` local do log do provedor é dependente de distribuição e pode ser um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="33ce8-144">On Linux, the `Debug` provider log location is distribution-dependent and may be one of the following:</span></span>

- <span data-ttu-id="33ce8-145">*/var/log/message*</span><span class="sxs-lookup"><span data-stu-id="33ce8-145">*/var/log/message*</span></span>
- <span data-ttu-id="33ce8-146">*/var/log/syslog*</span><span class="sxs-lookup"><span data-stu-id="33ce8-146">*/var/log/syslog*</span></span>

### <a name="event-source"></a><span data-ttu-id="33ce8-147">Origem do Evento</span><span class="sxs-lookup"><span data-stu-id="33ce8-147">Event Source</span></span>

<span data-ttu-id="33ce8-148">O `EventSource` provedor grava em uma origem de evento de plataforma cruzada com o nome `Microsoft-Extensions-Logging` .</span><span class="sxs-lookup"><span data-stu-id="33ce8-148">The `EventSource` provider writes to a cross-platform event source with the name `Microsoft-Extensions-Logging`.</span></span> <span data-ttu-id="33ce8-149">No Windows, o provedor usa o [ETW](/windows/win32/etw/event-tracing-portal).</span><span class="sxs-lookup"><span data-stu-id="33ce8-149">On Windows, the provider uses [ETW](/windows/win32/etw/event-tracing-portal).</span></span>

#### <a name="dotnet-trace-tooling"></a><span data-ttu-id="33ce8-150">ferramentas de rastreamento dotnet</span><span class="sxs-lookup"><span data-stu-id="33ce8-150">dotnet trace tooling</span></span>

<span data-ttu-id="33ce8-151">A ferramenta [dotnet-Trace](../diagnostics/dotnet-trace.md) é uma ferramenta global da CLI de plataforma cruzada que habilita a coleta de rastreamentos do .NET Core de um processo em execução.</span><span class="sxs-lookup"><span data-stu-id="33ce8-151">The [dotnet-trace](../diagnostics/dotnet-trace.md) tool is a cross-platform CLI global tool that enables the collection of .NET Core traces of a running process.</span></span> <span data-ttu-id="33ce8-152">A ferramenta coleta <xref:Microsoft.Extensions.Logging.EventSource> dados do provedor usando um <xref:Microsoft.Extensions.Logging.EventSource.LoggingEventSource> .</span><span class="sxs-lookup"><span data-stu-id="33ce8-152">The tool collects <xref:Microsoft.Extensions.Logging.EventSource> provider data using a <xref:Microsoft.Extensions.Logging.EventSource.LoggingEventSource>.</span></span>

<span data-ttu-id="33ce8-153">Consulte [dotnet-Trace](../diagnostics/dotnet-trace.md) para obter instruções de instalação.</span><span class="sxs-lookup"><span data-stu-id="33ce8-153">See [dotnet-trace](../diagnostics/dotnet-trace.md) for installation instructions.</span></span> <span data-ttu-id="33ce8-154">Para obter um tutorial de diagnóstico usando o `dotnet-trace` , consulte [debug High CPU Usage in .NET Core](/../diagnostics/debug-highcpu.md).</span><span class="sxs-lookup"><span data-stu-id="33ce8-154">For a diagnostic tutorial using `dotnet-trace`, see [Debug high CPU usage in .NET Core](/../diagnostics/debug-highcpu.md).</span></span>

### <a name="windows-eventlog"></a><span data-ttu-id="33ce8-155">EventLog do Windows</span><span class="sxs-lookup"><span data-stu-id="33ce8-155">Windows EventLog</span></span>

<span data-ttu-id="33ce8-156">O `EventLog` provedor envia a saída de log para o log de eventos do Windows.</span><span class="sxs-lookup"><span data-stu-id="33ce8-156">The `EventLog` provider sends log output to the Windows Event Log.</span></span> <span data-ttu-id="33ce8-157">Ao contrário dos outros provedores, o `EventLog` provedor ***não*** herda as configurações padrão de não provedor.</span><span class="sxs-lookup"><span data-stu-id="33ce8-157">Unlike the other providers, the `EventLog` provider does ***not*** inherit the default non-provider settings.</span></span> <span data-ttu-id="33ce8-158">Se `EventLog` as configurações de log não forem especificadas, elas serão padronizadas como padrão `LogLevel.Warning` .</span><span class="sxs-lookup"><span data-stu-id="33ce8-158">If `EventLog` log settings aren't specified, they default to `LogLevel.Warning`.</span></span>

<span data-ttu-id="33ce8-159">Para registrar em log eventos inferiores <xref:Microsoft.Extensions.Logging.LogLevel.Warning?displayProperty=nameWithType> a, defina explicitamente o nível de log.</span><span class="sxs-lookup"><span data-stu-id="33ce8-159">To log events lower than <xref:Microsoft.Extensions.Logging.LogLevel.Warning?displayProperty=nameWithType>, explicitly set the log level.</span></span> <span data-ttu-id="33ce8-160">O exemplo a seguir define o nível de log padrão do log de eventos como <xref:Microsoft.Extensions.Logging.LogLevel.Information?displayProperty=nameWithType> :</span><span class="sxs-lookup"><span data-stu-id="33ce8-160">The following example sets the Event Log default log level to <xref:Microsoft.Extensions.Logging.LogLevel.Information?displayProperty=nameWithType>:</span></span>

```json
"Logging": {
  "EventLog": {
    "LogLevel": {
      "Default": "Information"
    }
  }
}
```

<span data-ttu-id="33ce8-161">[Sobrecargas de autoeventlog](xref:Microsoft.Extensions.Logging.EventLoggerFactoryExtensions) podem passar <xref:Microsoft.Extensions.Logging.EventLog.EventLogSettings> .</span><span class="sxs-lookup"><span data-stu-id="33ce8-161">[AddEventLog overloads](xref:Microsoft.Extensions.Logging.EventLoggerFactoryExtensions) can pass in <xref:Microsoft.Extensions.Logging.EventLog.EventLogSettings>.</span></span> <span data-ttu-id="33ce8-162">Se `null` ou não for especificado, as seguintes configurações padrão serão usadas:</span><span class="sxs-lookup"><span data-stu-id="33ce8-162">If `null` or not specified, the following default settings are used:</span></span>

- <span data-ttu-id="33ce8-163">`LogName`: "Aplicativo"</span><span class="sxs-lookup"><span data-stu-id="33ce8-163">`LogName`: "Application"</span></span>
- <span data-ttu-id="33ce8-164">`SourceName`: "Tempo de execução do .NET"</span><span class="sxs-lookup"><span data-stu-id="33ce8-164">`SourceName`: ".NET Runtime"</span></span>
- <span data-ttu-id="33ce8-165">`MachineName`: O nome do computador local é usado.</span><span class="sxs-lookup"><span data-stu-id="33ce8-165">`MachineName`: The local machine name is used.</span></span>

<span data-ttu-id="33ce8-166">O código a seguir altera o `SourceName` do valor padrão de `".NET Runtime"` para `CustomLogs` :</span><span class="sxs-lookup"><span data-stu-id="33ce8-166">The following code changes the `SourceName` from the default value of `".NET Runtime"` to `CustomLogs`:</span></span>

```csharp
public class Program
{
    public static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
                logging.AddEventLog(configuration =>
                    configuration.SourceName = "CustomLogs"));
}
```

### <a name="azure-app-service"></a><span data-ttu-id="33ce8-167">Serviço de aplicativo do Azure</span><span class="sxs-lookup"><span data-stu-id="33ce8-167">Azure App Service</span></span>

<span data-ttu-id="33ce8-168">O pacote de provedor [Microsoft.Extensions.Logging.AzureAppServices](https://www.nuget.org/packages/Microsoft.Extensions.Logging.AzureAppServices) grava logs em arquivos de texto no sistema de arquivos de um aplicativo do Serviço de Aplicativo do Azure e no [armazenamento de blobs](/azure/storage/blobs/storage-quickstart-blobs-dotnet#what-is-blob-storage) em uma conta de Armazenamento do Azure.</span><span class="sxs-lookup"><span data-stu-id="33ce8-168">The [Microsoft.Extensions.Logging.AzureAppServices](https://www.nuget.org/packages/Microsoft.Extensions.Logging.AzureAppServices) provider package writes logs to text files in an Azure App Service app's file system and to [blob storage](/azure/storage/blobs/storage-quickstart-blobs-dotnet#what-is-blob-storage) in an Azure Storage account.</span></span>

<span data-ttu-id="33ce8-169">O pacote do provedor não está incluído nas bibliotecas de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="33ce8-169">The provider package isn't included in the runtime libraries.</span></span> <span data-ttu-id="33ce8-170">Para usar o provedor, adicione o pacote do provedor ao projeto.</span><span class="sxs-lookup"><span data-stu-id="33ce8-170">To use the provider, add the provider package to the project.</span></span>

<span data-ttu-id="33ce8-171">Para definir as configurações do provedor, use <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureFileLoggerOptions> e <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureBlobLoggerOptions>, conforme mostrado no exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="33ce8-171">To configure provider settings, use <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureFileLoggerOptions> and <xref:Microsoft.Extensions.Logging.AzureAppServices.AzureBlobLoggerOptions>, as shown in the following example:</span></span>

```csharp
class Program
{
    static Task Main(string[] args) =>
        CreateHostBuilder(args).Build().RunAsync();

    static IHostBuilder CreateHostBuilder(string[] args) =>
        Host.CreateDefaultBuilder(args)
            .ConfigureLogging(logging =>
                logging.AddAzureWebAppDiagnostics())
            .ConfigureServices(services =>
                services.Configure<AzureFileLoggerOptions>(options =>
                {
                    options.FileName = "azure-diagnostics-";
                    options.FileSizeLimit = 50 * 1024;
                    options.RetainedFileCountLimit = 5;
                })
                .Configure<AzureBlobLoggerOptions>(options =>
                {
                    options.BlobName = "log.txt";
                }));
}
```

<span data-ttu-id="33ce8-172">Quando implantado no serviço Azure App, o aplicativo usa as configurações na seção [logs do serviço de aplicativo](/azure/app-service/web-sites-enable-diagnostic-log/#enable-application-logging-windows) da página Serviço de **aplicativo** da portal do Azure.</span><span class="sxs-lookup"><span data-stu-id="33ce8-172">When deployed to Azure App Service, the app uses the settings in the [App Service logs](/azure/app-service/web-sites-enable-diagnostic-log/#enable-application-logging-windows) section of the **App Service** page of the Azure portal.</span></span> <span data-ttu-id="33ce8-173">Quando as configurações a seguir são atualizadas, as alterações entram em vigor imediatamente sem a necessidade de uma reinicialização ou reimplantação do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="33ce8-173">When the following settings are updated, the changes take effect immediately without requiring a restart or redeployment of the app.</span></span>

- <span data-ttu-id="33ce8-174">**Log de aplicativo (Sistema de Arquivos)**</span><span class="sxs-lookup"><span data-stu-id="33ce8-174">**Application Logging (Filesystem)**</span></span>
- <span data-ttu-id="33ce8-175">**Log de aplicativo (Blob)**</span><span class="sxs-lookup"><span data-stu-id="33ce8-175">**Application Logging (Blob)**</span></span>

<span data-ttu-id="33ce8-176">O local padrão para arquivos de log é na pasta *D:\\home\\LogFiles\\Application* e o nome de arquivo padrão é *diagnostics-aaaammdd.txt*.</span><span class="sxs-lookup"><span data-stu-id="33ce8-176">The default location for log files is in the *D:\\home\\LogFiles\\Application* folder, and the default file name is *diagnostics-yyyymmdd.txt*.</span></span> <span data-ttu-id="33ce8-177">O limite padrão de tamanho do arquivo é 10 MB e o número padrão máximo de arquivos mantidos é 2.</span><span class="sxs-lookup"><span data-stu-id="33ce8-177">The default file size limit is 10 MB, and the default maximum number of files retained is 2.</span></span> <span data-ttu-id="33ce8-178">O nome de blob padrão é *{app-name}{timestamp}/aaaa/mm/dd/hh/{guid}-applicationLog.txt*.</span><span class="sxs-lookup"><span data-stu-id="33ce8-178">The default blob name is *{app-name}{timestamp}/yyyy/mm/dd/hh/{guid}-applicationLog.txt*.</span></span>

<span data-ttu-id="33ce8-179">Esse provedor só registra quando o projeto é executado no ambiente do Azure.</span><span class="sxs-lookup"><span data-stu-id="33ce8-179">This provider only logs when the project runs in the Azure environment.</span></span>

#### <a name="azure-log-streaming"></a><span data-ttu-id="33ce8-180">Fluxo de log do Azure</span><span class="sxs-lookup"><span data-stu-id="33ce8-180">Azure log streaming</span></span>

<span data-ttu-id="33ce8-181">O Azure log streaming dá suporte à exibição da atividade de log em tempo real em:</span><span class="sxs-lookup"><span data-stu-id="33ce8-181">Azure log streaming supports viewing log activity in real time from:</span></span>

- <span data-ttu-id="33ce8-182">O servidor de aplicativos</span><span class="sxs-lookup"><span data-stu-id="33ce8-182">The app server</span></span>
- <span data-ttu-id="33ce8-183">Do servidor Web</span><span class="sxs-lookup"><span data-stu-id="33ce8-183">The web server</span></span>
- <span data-ttu-id="33ce8-184">De uma solicitação de rastreio com falha</span><span class="sxs-lookup"><span data-stu-id="33ce8-184">Failed request tracing</span></span>

<span data-ttu-id="33ce8-185">Para configurar o fluxo de log do Azure:</span><span class="sxs-lookup"><span data-stu-id="33ce8-185">To configure Azure log streaming:</span></span>

- <span data-ttu-id="33ce8-186">Navegue até a página de **logs do serviço de aplicativo** na página do portal do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="33ce8-186">Navigate to the **App Service logs** page from the app's portal page.</span></span>
- <span data-ttu-id="33ce8-187">Defina **Habilitar o log de aplicativo (sistema de arquivos)** como **Ativada**.</span><span class="sxs-lookup"><span data-stu-id="33ce8-187">Set **Application Logging (Filesystem)** to **On**.</span></span>
- <span data-ttu-id="33ce8-188">Escolha o **Nível** de log.</span><span class="sxs-lookup"><span data-stu-id="33ce8-188">Choose the log **Level**.</span></span> <span data-ttu-id="33ce8-189">Essa configuração se aplica somente ao streaming de log do Azure.</span><span class="sxs-lookup"><span data-stu-id="33ce8-189">This setting only applies to Azure log streaming.</span></span>

<span data-ttu-id="33ce8-190">Navegue até a página **fluxo de log** para exibir os logs.</span><span class="sxs-lookup"><span data-stu-id="33ce8-190">Navigate to the **Log Stream** page to view logs.</span></span> <span data-ttu-id="33ce8-191">As mensagens registradas são registradas com a `ILogger` interface.</span><span class="sxs-lookup"><span data-stu-id="33ce8-191">The logged messages are logged with the `ILogger` interface.</span></span>

### <a name="azure-application-insights"></a><span data-ttu-id="33ce8-192">Azure Application Insights</span><span class="sxs-lookup"><span data-stu-id="33ce8-192">Azure Application Insights</span></span>

<span data-ttu-id="33ce8-193">O pacote do provedor [Microsoft. Extensions. Logging. ApplicationInsights](https://www.nuget.org/packages/Microsoft.Extensions.Logging.ApplicationInsights) grava logs em [aplicativo Azure insights](/azure/azure-monitor/app/cloudservices).</span><span class="sxs-lookup"><span data-stu-id="33ce8-193">The [Microsoft.Extensions.Logging.ApplicationInsights](https://www.nuget.org/packages/Microsoft.Extensions.Logging.ApplicationInsights) provider package writes logs to [Azure Application Insights](/azure/azure-monitor/app/cloudservices).</span></span> <span data-ttu-id="33ce8-194">O Application Insights é um serviço que monitora um aplicativo web e fornece ferramentas para consultar e analisar os dados de telemetria.</span><span class="sxs-lookup"><span data-stu-id="33ce8-194">Application Insights is a service that monitors a web app and provides tools for querying and analyzing the telemetry data.</span></span> <span data-ttu-id="33ce8-195">Se você usar esse provedor, poderá consultar e analisar os logs usando as ferramentas do Application Insights.</span><span class="sxs-lookup"><span data-stu-id="33ce8-195">If you use this provider, you can query and analyze your logs by using the Application Insights tools.</span></span>

<span data-ttu-id="33ce8-196">Para saber mais, consulte os recursos a seguir:</span><span class="sxs-lookup"><span data-stu-id="33ce8-196">For more information, see the following resources:</span></span>

- [<span data-ttu-id="33ce8-197">Visão geral do Application Insights</span><span class="sxs-lookup"><span data-stu-id="33ce8-197">Application Insights overview</span></span>](/azure/application-insights/app-insights-overview)
- <span data-ttu-id="33ce8-198">[ApplicationInsightsLoggerProvider para logs do .NET Core ILogger](/azure/azure-monitor/app/ilogger) – Comece aqui se você quiser implementar o provedor de log sem o restante da telemetria do Application Insights.</span><span class="sxs-lookup"><span data-stu-id="33ce8-198">[ApplicationInsightsLoggerProvider for .NET Core ILogger logs](/azure/azure-monitor/app/ilogger) - Start here if you want to implement the logging provider without the rest of Application Insights telemetry.</span></span>
- <span data-ttu-id="33ce8-199">[Application Insights logging adapters](/azure/azure-monitor/app/asp-net-trace-logs) (Adaptadores de registro em log do Application Insights).</span><span class="sxs-lookup"><span data-stu-id="33ce8-199">[Application Insights logging adapters](/azure/azure-monitor/app/asp-net-trace-logs).</span></span>
- <span data-ttu-id="33ce8-200">[Instalar, configurar e inicializar o SDK do Application Insights](/learn/modules/instrument-web-app-code-with-application-insights) – Tutorial interativo no site da Microsoft Learn.</span><span class="sxs-lookup"><span data-stu-id="33ce8-200">[Install, configure, and initialize the Application Insights SDK](/learn/modules/instrument-web-app-code-with-application-insights) - Interactive tutorial on the Microsoft Learn site.</span></span>

## <a name="third-party-logging-providers"></a><span data-ttu-id="33ce8-201">Provedores de log de terceiros</span><span class="sxs-lookup"><span data-stu-id="33ce8-201">Third-party logging providers</span></span>

<span data-ttu-id="33ce8-202">Aqui estão algumas estruturas de log de terceiros que funcionam com várias cargas de trabalho .NET:</span><span class="sxs-lookup"><span data-stu-id="33ce8-202">Here are some third-party logging frameworks that work with various .NET workloads:</span></span>

- <span data-ttu-id="33ce8-203">[elmah.io](https://elmah.io) ([repositório GitHub](https://github.com/elmahio/Elmah.Io.Extensions.Logging))</span><span class="sxs-lookup"><span data-stu-id="33ce8-203">[elmah.io](https://elmah.io) ([GitHub repo](https://github.com/elmahio/Elmah.Io.Extensions.Logging))</span></span>
- <span data-ttu-id="33ce8-204">[Gelf](https://docs.graylog.org/en/2.3/pages/gelf.html) ([repositório do GitHub](https://github.com/mattwcole/gelf-extensions-logging))</span><span class="sxs-lookup"><span data-stu-id="33ce8-204">[Gelf](https://docs.graylog.org/en/2.3/pages/gelf.html) ([GitHub repo](https://github.com/mattwcole/gelf-extensions-logging))</span></span>
- <span data-ttu-id="33ce8-205">[JSNLog](http://jsnlog.com) ([repositório GitHub](https://github.com/mperdeck/jsnlog))</span><span class="sxs-lookup"><span data-stu-id="33ce8-205">[JSNLog](http://jsnlog.com) ([GitHub repo](https://github.com/mperdeck/jsnlog))</span></span>
- <span data-ttu-id="33ce8-206">[KissLog.net](https://kisslog.net) ([Repositório do GitHub](https://github.com/catalingavan/KissLog-net))</span><span class="sxs-lookup"><span data-stu-id="33ce8-206">[KissLog.net](https://kisslog.net) ([GitHub repo](https://github.com/catalingavan/KissLog-net))</span></span>
- <span data-ttu-id="33ce8-207">[Log4net](https://logging.apache.org/log4net) ([repositório GitHub](https://github.com/apache/logging-log4net))</span><span class="sxs-lookup"><span data-stu-id="33ce8-207">[Log4Net](https://logging.apache.org/log4net) ([GitHub repo](https://github.com/apache/logging-log4net))</span></span>
- <span data-ttu-id="33ce8-208">[Loggr](https://loggr.net) ([repositório GitHub](https://github.com/imobile3/Loggr.Extensions.Logging))</span><span class="sxs-lookup"><span data-stu-id="33ce8-208">[Loggr](https://loggr.net) ([GitHub repo](https://github.com/imobile3/Loggr.Extensions.Logging))</span></span>
- <span data-ttu-id="33ce8-209">[NLog](https://nlog-project.org) ([repositório GitHub](https://github.com/NLog/NLog.Extensions.Logging))</span><span class="sxs-lookup"><span data-stu-id="33ce8-209">[NLog](https://nlog-project.org) ([GitHub repo](https://github.com/NLog/NLog.Extensions.Logging))</span></span>
- <span data-ttu-id="33ce8-210">[Sentry](https://sentry.io/welcome) ([repositório GitHub](https://github.com/getsentry/sentry-dotnet))</span><span class="sxs-lookup"><span data-stu-id="33ce8-210">[Sentry](https://sentry.io/welcome) ([GitHub repo](https://github.com/getsentry/sentry-dotnet))</span></span>
- <span data-ttu-id="33ce8-211">[Serilog](https://serilog.net) ([repositório GitHub](https://github.com/serilog/serilog-sinks-console))</span><span class="sxs-lookup"><span data-stu-id="33ce8-211">[Serilog](https://serilog.net) ([GitHub repo](https://github.com/serilog/serilog-sinks-console))</span></span>
- <span data-ttu-id="33ce8-212">[Stackdriver](https://cloud.google.com/dotnet/docs/stackdriver#logging) ([repositório GitHub](https://github.com/googleapis/google-cloud-dotnet))</span><span class="sxs-lookup"><span data-stu-id="33ce8-212">[Stackdriver](https://cloud.google.com/dotnet/docs/stackdriver#logging) ([GitHub repo](https://github.com/googleapis/google-cloud-dotnet))</span></span>

<span data-ttu-id="33ce8-213">Algumas estruturas de terceiros podem fazer o [log semântico, também conhecido como registro em log estruturado](https://softwareengineering.stackexchange.com/questions/312197/benefits-of-structured-logging-vs-basic-logging).</span><span class="sxs-lookup"><span data-stu-id="33ce8-213">Some third-party frameworks can perform [semantic logging, also known as structured logging](https://softwareengineering.stackexchange.com/questions/312197/benefits-of-structured-logging-vs-basic-logging).</span></span>

<span data-ttu-id="33ce8-214">Usar uma estrutura de terceiros é semelhante ao uso de um dos provedores internos:</span><span class="sxs-lookup"><span data-stu-id="33ce8-214">Using a third-party framework is similar to using one of the built-in providers:</span></span>

1. <span data-ttu-id="33ce8-215">Adicione um pacote NuGet ao projeto.</span><span class="sxs-lookup"><span data-stu-id="33ce8-215">Add a NuGet package to your project.</span></span>
1. <span data-ttu-id="33ce8-216">Chame um `ILoggerFactory` `ILoggingBuilder` método de extensão ou fornecido pela estrutura de log.</span><span class="sxs-lookup"><span data-stu-id="33ce8-216">Call an `ILoggerFactory` or `ILoggingBuilder` extension method provided by the logging framework.</span></span>

<span data-ttu-id="33ce8-217">Para saber mais, consulte a documentação de cada provedor.</span><span class="sxs-lookup"><span data-stu-id="33ce8-217">For more information, see each provider's documentation.</span></span> <span data-ttu-id="33ce8-218">Não há suporte para provedores de log de terceiros na Microsoft.</span><span class="sxs-lookup"><span data-stu-id="33ce8-218">Third-party logging providers aren't supported by Microsoft.</span></span>

## <a name="see-also"></a><span data-ttu-id="33ce8-219">Confira também</span><span class="sxs-lookup"><span data-stu-id="33ce8-219">See also</span></span>

- <span data-ttu-id="33ce8-220">[Registro em log no .net](logging.md).</span><span class="sxs-lookup"><span data-stu-id="33ce8-220">[Logging in .NET](logging.md).</span></span>
- <span data-ttu-id="33ce8-221">[Implemente um provedor de log personalizado no .net](custom-logging-provider.md).</span><span class="sxs-lookup"><span data-stu-id="33ce8-221">[Implement a custom logging provider in .NET](custom-logging-provider.md).</span></span>
- <span data-ttu-id="33ce8-222">[Registro em log de alto desempenho no .net](high-performance-logging.md).</span><span class="sxs-lookup"><span data-stu-id="33ce8-222">[High-performance logging in .NET](high-performance-logging.md).</span></span>
