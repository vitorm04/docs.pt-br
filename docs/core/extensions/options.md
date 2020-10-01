---
title: Padrão de opções no .NET
author: IEvangelist
description: Saiba como usar o padrão de opções para representar grupos de configurações relacionadas em aplicativos .NET.
ms.author: dapine
ms.date: 09/30/2020
ms.openlocfilehash: 5c59a14223ec7c35456e1ea84d3f976e236f45dd
ms.sourcegitcommit: 97405ed212f69b0a32faa66a5d5fae7e76628b68
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/01/2020
ms.locfileid: "91614676"
---
# <a name="options-pattern-in-net"></a><span data-ttu-id="22bb7-103">Padrão de opções no .NET</span><span class="sxs-lookup"><span data-stu-id="22bb7-103">Options pattern in .NET</span></span>

<span data-ttu-id="22bb7-104">O padrão de opções usa classes para fornecer acesso fortemente tipado a grupos de configurações relacionadas.</span><span class="sxs-lookup"><span data-stu-id="22bb7-104">The options pattern uses classes to provide strongly-typed access to groups of related settings.</span></span> <span data-ttu-id="22bb7-105">Quando as [definições de configuração](configuration.md) são isoladas por cenário em classes separadas, o aplicativo segue dois princípios importantes de engenharia de software:</span><span class="sxs-lookup"><span data-stu-id="22bb7-105">When [configuration settings](configuration.md) are isolated by scenario into separate classes, the app adheres to two important software engineering principles:</span></span>

- <span data-ttu-id="22bb7-106">O [princípio de diferenciação de interface (ISP) ou encapsulamento](../../architecture/modern-web-apps-azure/architectural-principles.md#encapsulation): cenários (classes) que dependem de definições de configuração dependem apenas dos parâmetros de configuração que eles usam.</span><span class="sxs-lookup"><span data-stu-id="22bb7-106">The [Interface Segregation Principle (ISP) or Encapsulation](../../architecture/modern-web-apps-azure/architectural-principles.md#encapsulation): Scenarios (classes) that depend on configuration settings depend only on the configuration settings that they use.</span></span>
- <span data-ttu-id="22bb7-107">[Separação de Interesses](../../architecture/modern-web-apps-azure/architectural-principles.md#separation-of-concerns): as configurações para diferentes partes do aplicativo não são dependentes nem acopladas entre si.</span><span class="sxs-lookup"><span data-stu-id="22bb7-107">[Separation of Concerns](../../architecture/modern-web-apps-azure/architectural-principles.md#separation-of-concerns): Settings for different parts of the app aren't dependent or coupled to one another.</span></span>

<span data-ttu-id="22bb7-108">As opções também fornecem um mecanismo para validar os dados da configuração.</span><span class="sxs-lookup"><span data-stu-id="22bb7-108">Options also provide a mechanism to validate configuration data.</span></span> <span data-ttu-id="22bb7-109">Para obter mais configurações, consulte a seção [Validação de opções](#options-validation).</span><span class="sxs-lookup"><span data-stu-id="22bb7-109">For more information, see the [Options validation](#options-validation) section.</span></span>

## <a name="bind-hierarchical-configuration"></a><span data-ttu-id="22bb7-110">Associar configuração hierárquica</span><span class="sxs-lookup"><span data-stu-id="22bb7-110">Bind hierarchical configuration</span></span>

<span data-ttu-id="22bb7-111">A maneira preferida de ler valores de configuração relacionados é usar o padrão de opções.</span><span class="sxs-lookup"><span data-stu-id="22bb7-111">The preferred way to read related configuration values is using the options pattern.</span></span> <span data-ttu-id="22bb7-112">Por exemplo, para ler os seguintes valores de configuração:</span><span class="sxs-lookup"><span data-stu-id="22bb7-112">For example, to read the following configuration values:</span></span>

:::code language="json" source="snippets/configuration/console-json/appsettings.json" range="3-6":::

<span data-ttu-id="22bb7-113">Crie a seguinte `TransientFaultHandlingOptions` classe:</span><span class="sxs-lookup"><span data-stu-id="22bb7-113">Create the following `TransientFaultHandlingOptions` class:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/TransientFaultHandlingOptions.cs" range="5-6":::

<span data-ttu-id="22bb7-114">Uma classe de opções:</span><span class="sxs-lookup"><span data-stu-id="22bb7-114">An options class:</span></span>

* <span data-ttu-id="22bb7-115">Deve ser não-abstrato com um construtor público sem parâmetros</span><span class="sxs-lookup"><span data-stu-id="22bb7-115">Must be non-abstract with a public parameterless constructor</span></span>
* <span data-ttu-id="22bb7-116">Conter Propriedades de leitura/gravação públicas para associar (os campos ***não*** estão associados)</span><span class="sxs-lookup"><span data-stu-id="22bb7-116">Contain public read-write properties to bind (fields are ***not*** bound)</span></span>

<span data-ttu-id="22bb7-117">O seguinte código:</span><span class="sxs-lookup"><span data-stu-id="22bb7-117">The following code:</span></span>

* <span data-ttu-id="22bb7-118">Chama [ConfigurationBinder. bind](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind%2A) para associar a `TransientFaultHandlingOptions` classe à `"TransientFaultHandlingOptions"` seção.</span><span class="sxs-lookup"><span data-stu-id="22bb7-118">Calls [ConfigurationBinder.Bind](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Bind%2A) to bind the `TransientFaultHandlingOptions` class to the `"TransientFaultHandlingOptions"` section.</span></span>
* <span data-ttu-id="22bb7-119">Exibe os dados de configuração.</span><span class="sxs-lookup"><span data-stu-id="22bb7-119">Displays the configuration data.</span></span>

:::code language="csharp" source="snippets/configuration/console-json/Program.cs" range="25-32":::

<span data-ttu-id="22bb7-120">No código anterior, as alterações no arquivo de configuração JSON depois que o aplicativo é iniciado são lidas.</span><span class="sxs-lookup"><span data-stu-id="22bb7-120">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

<span data-ttu-id="22bb7-121">[`ConfigurationBinder.Get<T>`](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Get%2A) associa e retorna o tipo especificado.</span><span class="sxs-lookup"><span data-stu-id="22bb7-121">[`ConfigurationBinder.Get<T>`](xref:Microsoft.Extensions.Configuration.ConfigurationBinder.Get%2A) binds and returns the specified type.</span></span> <span data-ttu-id="22bb7-122">`ConfigurationBinder.Get<T>` pode ser mais conveniente do que usar o `ConfigurationBinder.Bind` .</span><span class="sxs-lookup"><span data-stu-id="22bb7-122">`ConfigurationBinder.Get<T>` may be more convenient than using `ConfigurationBinder.Bind`.</span></span> <span data-ttu-id="22bb7-123">O código a seguir mostra como usar `ConfigurationBinder.Get<T>` com a `TransientFaultHandlingOptions` classe:</span><span class="sxs-lookup"><span data-stu-id="22bb7-123">The following code shows how to use `ConfigurationBinder.Get<T>` with the `TransientFaultHandlingOptions` class:</span></span>

```csharp
IConfigurationRoot configurationRoot = configuration.Build();

var options =
    configurationRoot.GetSection(nameof(TransientFaultHandlingOptions))
        .Get<TransientFaultHandlingOptions>();

Console.WriteLine($"TransientFaultHandlingOptions.Enabled={options.Enabled}");
Console.WriteLine($"TransientFaultHandlingOptions.AutoRetryDelay={options.AutoRetryDelay}");
```

<span data-ttu-id="22bb7-124">No código anterior, as alterações no arquivo de configuração JSON depois que o aplicativo é iniciado são lidas.</span><span class="sxs-lookup"><span data-stu-id="22bb7-124">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

<span data-ttu-id="22bb7-125">Uma abordagem alternativa ao usar o padrão de opções é associar a `"TransientFaultHandlingOptions"` seção e adicioná-la ao [contêiner de serviço de injeção de dependência](dependency-injection.md).</span><span class="sxs-lookup"><span data-stu-id="22bb7-125">An alternative approach when using the options pattern is to bind the `"TransientFaultHandlingOptions"` section and add it to the [dependency injection service container](dependency-injection.md).</span></span> <span data-ttu-id="22bb7-126">No código a seguir, `TransientFaultHandlingOptions` é adicionado ao contêiner de serviço com <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%2A> e associado à configuração:</span><span class="sxs-lookup"><span data-stu-id="22bb7-126">In the following code, `TransientFaultHandlingOptions` is added to the service container with <xref:Microsoft.Extensions.DependencyInjection.OptionsConfigurationServiceCollectionExtensions.Configure%2A> and bound to configuration:</span></span>

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        key: nameof(TransientFaultHandlingOptions)));
```

> [!TIP]
> <span data-ttu-id="22bb7-127">O `key` parâmetro é o nome da seção de configuração a ser pesquisada.</span><span class="sxs-lookup"><span data-stu-id="22bb7-127">The `key` parameter is the name of the configuration section to search for.</span></span> <span data-ttu-id="22bb7-128">Ele *não* precisa corresponder ao nome do tipo que o representa.</span><span class="sxs-lookup"><span data-stu-id="22bb7-128">It does *not* have to match the name of the type that represents it.</span></span> <span data-ttu-id="22bb7-129">Por exemplo, você poderia ter uma seção chamada `"FaultHandling"` e ela poderia ser representada pela `TransientFaultHandlingOptions` classe.</span><span class="sxs-lookup"><span data-stu-id="22bb7-129">For example, you could have a section named `"FaultHandling"` and it could be represented by the `TransientFaultHandlingOptions` class.</span></span> <span data-ttu-id="22bb7-130">Nessa instância, você passaria `"FaultHandling"` para a <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> função em vez disso.</span><span class="sxs-lookup"><span data-stu-id="22bb7-130">In this instance, you'd pass `"FaultHandling"` to the <xref:Microsoft.Extensions.Configuration.IConfiguration.GetSection%2A> function instead.</span></span> <span data-ttu-id="22bb7-131">O `nameof` operador é usado como uma conveniência quando a seção nomeada corresponde ao tipo ao qual ela corresponde.</span><span class="sxs-lookup"><span data-stu-id="22bb7-131">The `nameof` operator is used as a convenience when the named section matches the type it corresponds to.</span></span>

<span data-ttu-id="22bb7-132">Usando o código anterior, o código a seguir lê as opções de posição:</span><span class="sxs-lookup"><span data-stu-id="22bb7-132">Using the preceding code, the following code reads the position options:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ExampleService.cs":::

<span data-ttu-id="22bb7-133">No código anterior, as alterações no arquivo de configuração JSON depois que o aplicativo foi iniciado ***não*** são lidas.</span><span class="sxs-lookup"><span data-stu-id="22bb7-133">In the preceding code, changes to the JSON configuration file after the app has started are ***not*** read.</span></span> <span data-ttu-id="22bb7-134">Para ler as alterações depois que o aplicativo for iniciado, use [IOptionsSnapshot](#use-ioptionssnapshot-to-read-updated-data).</span><span class="sxs-lookup"><span data-stu-id="22bb7-134">To read changes after the app has started, use [IOptionsSnapshot](#use-ioptionssnapshot-to-read-updated-data).</span></span>

## <a name="options-interfaces"></a><span data-ttu-id="22bb7-135">Interfaces de opções</span><span class="sxs-lookup"><span data-stu-id="22bb7-135">Options interfaces</span></span>

<span data-ttu-id="22bb7-136"><xref:Microsoft.Extensions.Options.IOptions%601>:</span><span class="sxs-lookup"><span data-stu-id="22bb7-136"><xref:Microsoft.Extensions.Options.IOptions%601>:</span></span>

- <span data-ttu-id="22bb7-137">Não ***oferece suporte a*** :</span><span class="sxs-lookup"><span data-stu-id="22bb7-137">Does ***not*** support:</span></span>
  - <span data-ttu-id="22bb7-138">Leitura de dados de configuração após o aplicativo ser iniciado.</span><span class="sxs-lookup"><span data-stu-id="22bb7-138">Reading of configuration data after the app has started.</span></span>
  - [<span data-ttu-id="22bb7-139">Opções nomeadas</span><span class="sxs-lookup"><span data-stu-id="22bb7-139">Named options</span></span>](#named-options-support-using-iconfigurenamedoptions)
- <span data-ttu-id="22bb7-140">É registrado como um [singleton](dependency-injection.md#singleton) e pode ser injetado em qualquer [tempo de vida do serviço](dependency-injection.md#service-lifetimes).</span><span class="sxs-lookup"><span data-stu-id="22bb7-140">Is registered as a [Singleton](dependency-injection.md#singleton) and can be injected into any [service lifetime](dependency-injection.md#service-lifetimes).</span></span>

<span data-ttu-id="22bb7-141"><xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>:</span><span class="sxs-lookup"><span data-stu-id="22bb7-141"><xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>:</span></span>

- <span data-ttu-id="22bb7-142">É útil em cenários em que as opções devem ser recomputadas em cada resolução de injeção, em [tempos de vida transitórios ou de escopo](dependency-injection.md#service-lifetimes).</span><span class="sxs-lookup"><span data-stu-id="22bb7-142">Is useful in scenarios where options should be recomputed on every injection resolution, in [scoped or transient lifetimes](dependency-injection.md#service-lifetimes).</span></span> <span data-ttu-id="22bb7-143">Para obter mais informações, consulte [usar IOptionsSnapshot para ler dados atualizados](#use-ioptionssnapshot-to-read-updated-data).</span><span class="sxs-lookup"><span data-stu-id="22bb7-143">For more information, see [Use IOptionsSnapshot to read updated data](#use-ioptionssnapshot-to-read-updated-data).</span></span>
- <span data-ttu-id="22bb7-144">Está registrado como [escopo](dependency-injection.md#scoped) e, portanto, não pode ser injetado em um serviço singleton.</span><span class="sxs-lookup"><span data-stu-id="22bb7-144">Is registered as [Scoped](dependency-injection.md#scoped) and therefore cannot be injected into a Singleton service.</span></span>
- <span data-ttu-id="22bb7-145">Dá suporte a [Opções nomeadas](#named-options-support-using-iconfigurenamedoptions)</span><span class="sxs-lookup"><span data-stu-id="22bb7-145">Supports [named options](#named-options-support-using-iconfigurenamedoptions)</span></span>

<span data-ttu-id="22bb7-146"><xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:</span><span class="sxs-lookup"><span data-stu-id="22bb7-146"><xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:</span></span>

- <span data-ttu-id="22bb7-147">É usado para recuperar opções e gerenciar notificações de opções para `TOptions` instâncias.</span><span class="sxs-lookup"><span data-stu-id="22bb7-147">Is used to retrieve options and manage options notifications for `TOptions` instances.</span></span>
- <span data-ttu-id="22bb7-148">É registrado como um [singleton](dependency-injection.md#singleton) e pode ser injetado em qualquer [tempo de vida do serviço](dependency-injection.md#service-lifetimes).</span><span class="sxs-lookup"><span data-stu-id="22bb7-148">Is registered as a [Singleton](dependency-injection.md#singleton) and can be injected into any [service lifetime](dependency-injection.md#service-lifetimes).</span></span>
- <span data-ttu-id="22bb7-149">Oferece suporte a:</span><span class="sxs-lookup"><span data-stu-id="22bb7-149">Supports:</span></span>
  - <span data-ttu-id="22bb7-150">Notificações de alteração</span><span class="sxs-lookup"><span data-stu-id="22bb7-150">Change notifications</span></span>
  - [<span data-ttu-id="22bb7-151">Opções nomeadas</span><span class="sxs-lookup"><span data-stu-id="22bb7-151">Named options</span></span>](#named-options-support-using-iconfigurenamedoptions)
  - [<span data-ttu-id="22bb7-152">Configuração recarregável</span><span class="sxs-lookup"><span data-stu-id="22bb7-152">Reloadable configuration</span></span>](#use-ioptionssnapshot-to-read-updated-data)
  - <span data-ttu-id="22bb7-153">Invalidação seletiva de opções (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601>)</span><span class="sxs-lookup"><span data-stu-id="22bb7-153">Selective options invalidation (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601>)</span></span>
  
<span data-ttu-id="22bb7-154">O <xref:Microsoft.Extensions.Options.IOptionsFactory%601> é responsável por criar novas instâncias de opções.</span><span class="sxs-lookup"><span data-stu-id="22bb7-154"><xref:Microsoft.Extensions.Options.IOptionsFactory%601> is responsible for creating new options instances.</span></span> <span data-ttu-id="22bb7-155">Ele tem um único método <xref:Microsoft.Extensions.Options.IOptionsFactory%601.Create%2A>.</span><span class="sxs-lookup"><span data-stu-id="22bb7-155">It has a single <xref:Microsoft.Extensions.Options.IOptionsFactory%601.Create%2A> method.</span></span> <span data-ttu-id="22bb7-156">A implementação padrão usa todos os <xref:Microsoft.Extensions.Options.IConfigureOptions%601> e <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601> registrados e executa todas as configurações primeiro, seguidas da pós-configuração.</span><span class="sxs-lookup"><span data-stu-id="22bb7-156">The default implementation takes all registered <xref:Microsoft.Extensions.Options.IConfigureOptions%601> and <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601> and runs all the configurations first, followed by the post-configuration.</span></span> <span data-ttu-id="22bb7-157">Ela faz distinção entre <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> e <xref:Microsoft.Extensions.Options.IConfigureOptions%601> e chama apenas a interface apropriada.</span><span class="sxs-lookup"><span data-stu-id="22bb7-157">It distinguishes between <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> and <xref:Microsoft.Extensions.Options.IConfigureOptions%601> and only calls the appropriate interface.</span></span>

<span data-ttu-id="22bb7-158">O <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> é usado pelo <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> para armazenar em cache as instâncias do `TOptions`.</span><span class="sxs-lookup"><span data-stu-id="22bb7-158"><xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> is used by <xref:Microsoft.Extensions.Options.IOptionsMonitor%601> to cache `TOptions` instances.</span></span> <span data-ttu-id="22bb7-159">O <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> invalida as instâncias de opções no monitor, de modo que o valor seja recalculado (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryRemove%2A>).</span><span class="sxs-lookup"><span data-stu-id="22bb7-159">The <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601> invalidates options instances in the monitor so that the value is recomputed (<xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryRemove%2A>).</span></span> <span data-ttu-id="22bb7-160">Os valores podem ser manualmente inseridos com <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryAdd%2A>.</span><span class="sxs-lookup"><span data-stu-id="22bb7-160">Values can be manually introduced with <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.TryAdd%2A>.</span></span> <span data-ttu-id="22bb7-161">O método <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.Clear%2A> é usado quando todas as instâncias nomeadas devem ser recriadas sob demanda.</span><span class="sxs-lookup"><span data-stu-id="22bb7-161">The <xref:Microsoft.Extensions.Options.IOptionsMonitorCache%601.Clear%2A> method is used when all named instances should be recreated on demand.</span></span>

## <a name="use-ioptionssnapshot-to-read-updated-data"></a><span data-ttu-id="22bb7-162">Usar IOptionsSnapshot para ler dados atualizados</span><span class="sxs-lookup"><span data-stu-id="22bb7-162">Use IOptionsSnapshot to read updated data</span></span>

<span data-ttu-id="22bb7-163">Quando você usa <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601> , as opções são computadas uma vez por solicitação quando acessadas e armazenadas em cache durante o tempo de vida da solicitação.</span><span class="sxs-lookup"><span data-stu-id="22bb7-163">when you use <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>, options are computed once per request when accessed and are cached for the lifetime of the request.</span></span> <span data-ttu-id="22bb7-164">As alterações na configuração são lidas depois que o aplicativo é iniciado ao usar provedores de configuração que dão suporte à leitura de valores de configuração atualizados.</span><span class="sxs-lookup"><span data-stu-id="22bb7-164">Changes to the configuration are read after the app starts when using configuration providers that support reading updated configuration values.</span></span>

<span data-ttu-id="22bb7-165">A diferença entre `IOptionsMonitor` e `IOptionsSnapshot` é que:</span><span class="sxs-lookup"><span data-stu-id="22bb7-165">The difference between `IOptionsMonitor` and `IOptionsSnapshot` is that:</span></span>

- <span data-ttu-id="22bb7-166">`IOptionsMonitor` é um [serviço singleton](dependency-injection.md#singleton) que recupera os valores de opção atuais a qualquer momento, o que é especialmente útil em dependências singleton.</span><span class="sxs-lookup"><span data-stu-id="22bb7-166">`IOptionsMonitor` is a [singleton service](dependency-injection.md#singleton) that retrieves current option values at any time, which is especially useful in singleton dependencies.</span></span>
- <span data-ttu-id="22bb7-167">`IOptionsSnapshot` é um [serviço com escopo](dependency-injection.md#scoped) e fornece um instantâneo das opções no momento em que o `IOptionsSnapshot<T>` objeto é construído.</span><span class="sxs-lookup"><span data-stu-id="22bb7-167">`IOptionsSnapshot` is a [scoped service](dependency-injection.md#scoped) and provides a snapshot of the options at the time the `IOptionsSnapshot<T>` object is constructed.</span></span> <span data-ttu-id="22bb7-168">Os instantâneos de opções são projetados para uso com dependências transitórias e com escopo definido.</span><span class="sxs-lookup"><span data-stu-id="22bb7-168">Options snapshots are designed for use with transient and scoped dependencies.</span></span>

<span data-ttu-id="22bb7-169">O código a seguir usa <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601> .</span><span class="sxs-lookup"><span data-stu-id="22bb7-169">The following code uses <xref:Microsoft.Extensions.Options.IOptionsSnapshot%601>.</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ScopedService.cs":::

<span data-ttu-id="22bb7-170">O código a seguir registra uma instância de configuração que se `TransientFaultHandlingOptions` associa a:</span><span class="sxs-lookup"><span data-stu-id="22bb7-170">The following code registers a configuration instance which `TransientFaultHandlingOptions` binds against:</span></span>

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

<span data-ttu-id="22bb7-171">No código anterior, as alterações no arquivo de configuração JSON depois que o aplicativo é iniciado são lidas.</span><span class="sxs-lookup"><span data-stu-id="22bb7-171">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

## <a name="ioptionsmonitor"></a><span data-ttu-id="22bb7-172">IOptionsMonitor</span><span class="sxs-lookup"><span data-stu-id="22bb7-172">IOptionsMonitor</span></span>

<span data-ttu-id="22bb7-173">O código a seguir registra uma instância de configuração que é `TransientFaultHandlingOptions` associada a.</span><span class="sxs-lookup"><span data-stu-id="22bb7-173">The following code registers a configuration instance which `TransientFaultHandlingOptions` binds against.</span></span>

```csharp
services.Configure<TransientFaultHandlingOptions>(
    configurationRoot.GetSection(
        nameof(TransientFaultHandlingOptions)));
```

<span data-ttu-id="22bb7-174">O exemplo a seguir usa <xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:</span><span class="sxs-lookup"><span data-stu-id="22bb7-174">The following example uses <xref:Microsoft.Extensions.Options.IOptionsMonitor%601>:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/MonitorService.cs":::

<span data-ttu-id="22bb7-175">No código anterior, as alterações no arquivo de configuração JSON depois que o aplicativo é iniciado são lidas.</span><span class="sxs-lookup"><span data-stu-id="22bb7-175">In the preceding code, changes to the JSON configuration file after the app has started are read.</span></span>

## <a name="named-options-support-using-iconfigurenamedoptions"></a><span data-ttu-id="22bb7-176">Suporte a opções nomeadas usando IConfigureNamedOptions</span><span class="sxs-lookup"><span data-stu-id="22bb7-176">Named options support using IConfigureNamedOptions</span></span>

<span data-ttu-id="22bb7-177">Opções nomeadas:</span><span class="sxs-lookup"><span data-stu-id="22bb7-177">Named options:</span></span>

- <span data-ttu-id="22bb7-178">São úteis quando várias seções de configuração se associam às mesmas propriedades.</span><span class="sxs-lookup"><span data-stu-id="22bb7-178">Are useful when multiple configuration sections bind to the same properties.</span></span>
- <span data-ttu-id="22bb7-179">Diferenciam maiúsculas de minúsculas.</span><span class="sxs-lookup"><span data-stu-id="22bb7-179">Are case-sensitive.</span></span>

<span data-ttu-id="22bb7-180">Considere o seguinte *appsettings.jsno* arquivo:</span><span class="sxs-lookup"><span data-stu-id="22bb7-180">Consider the following *appsettings.json* file:</span></span>

```json
{
  "Features": {
    "Personalize": {
      "Enabled": true,
      "ApiKey": "aGEgaGEgeW91IHRob3VnaHQgdGhhdCB3YXMgcmVhbGx5IHNvbWV0aGluZw=="
    },
    "WeatherStation": {
      "Enabled": true,
      "ApiKey": "QXJlIHlvdSBhdHRlbXB0aW5nIHRvIGhhY2sgdXM/"
    }
  }
}
```

<span data-ttu-id="22bb7-181">Em vez de criar duas classes para associar `Features:Personalize` e `Features:WeatherStation` , a seguinte classe é usada para cada seção:</span><span class="sxs-lookup"><span data-stu-id="22bb7-181">Rather than creating two classes to bind `Features:Personalize` and `Features:WeatherStation`, the following class is used for each section:</span></span>

```csharp
public class Features
{
    public const string Personalize = nameof(Personalize);
    public const string WeatherStation = nameof(WeatherStation);

    public bool Enabled { get; set; }
    public string ApiKey { get; set; }
}
```

<span data-ttu-id="22bb7-182">O código a seguir configura as opções nomeadas:</span><span class="sxs-lookup"><span data-stu-id="22bb7-182">The following code configures the named options:</span></span>

```csharp
ConfigureServices(services =>
{
    services.Configure<Features>(
        Features.Personalize,
        Configuration.GetSection("Features:Personalize"));

    services.Configure<Features>(
        Features.WeatherStation,
        Configuration.GetSection("Features:WeatherStation"));
});
```

<span data-ttu-id="22bb7-183">O código a seguir exibe as opções nomeadas:</span><span class="sxs-lookup"><span data-stu-id="22bb7-183">The following code displays the named options:</span></span>

```csharp
public class Service
{
    private readonly Features _personalizeFeature;
    private readonly Features _weatherStationFeature;

    public Service(IOptionsSnapshot<Features> namedOptionsAccessor)
    {
        _personalizeFeature = namedOptionsAccessor.Get(Features.Personalize);
        _weatherStationFeature = namedOptionsAccessor.Get(Features.WeatherStation);
    }
}
```

<span data-ttu-id="22bb7-184">Todas as opções são instâncias nomeadas.</span><span class="sxs-lookup"><span data-stu-id="22bb7-184">All options are named instances.</span></span> <span data-ttu-id="22bb7-185"><xref:Microsoft.Extensions.Options.IConfigureOptions%601> as instâncias são tratadas como destino da `Options.DefaultName` instância, que é `string.Empty` .</span><span class="sxs-lookup"><span data-stu-id="22bb7-185"><xref:Microsoft.Extensions.Options.IConfigureOptions%601> instances are treated as targeting the `Options.DefaultName` instance, which is `string.Empty`.</span></span> <span data-ttu-id="22bb7-186"><xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> também implementa <xref:Microsoft.Extensions.Options.IConfigureOptions%601>.</span><span class="sxs-lookup"><span data-stu-id="22bb7-186"><xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> also implements <xref:Microsoft.Extensions.Options.IConfigureOptions%601>.</span></span> <span data-ttu-id="22bb7-187">A implementação padrão de <xref:Microsoft.Extensions.Options.IOptionsFactory%601> tem lógica para usar cada um de forma adequada.</span><span class="sxs-lookup"><span data-stu-id="22bb7-187">The default implementation of the <xref:Microsoft.Extensions.Options.IOptionsFactory%601> has logic to use each appropriately.</span></span> <span data-ttu-id="22bb7-188">A `null` opção nomeada é usada para direcionar todas as instâncias nomeadas em vez de uma instância nomeada específica.</span><span class="sxs-lookup"><span data-stu-id="22bb7-188">The `null` named option is used to target all of the named instances instead of a specific named instance.</span></span> <span data-ttu-id="22bb7-189"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.ConfigureAll%2A> e <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> Use essa convenção.</span><span class="sxs-lookup"><span data-stu-id="22bb7-189"><xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.ConfigureAll%2A> and <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> use this convention.</span></span>

## <a name="optionsbuilder-api"></a><span data-ttu-id="22bb7-190">API OptionsBuilder</span><span class="sxs-lookup"><span data-stu-id="22bb7-190">OptionsBuilder API</span></span>

<span data-ttu-id="22bb7-191"><xref:Microsoft.Extensions.Options.OptionsBuilder%601> é usada para configurar instâncias `TOptions`.</span><span class="sxs-lookup"><span data-stu-id="22bb7-191"><xref:Microsoft.Extensions.Options.OptionsBuilder%601> is used to configure `TOptions` instances.</span></span> <span data-ttu-id="22bb7-192">`OptionsBuilder` simplifica a criação de opções nomeadas, pois é apenas um único parâmetro para a chamada `AddOptions<TOptions>(string optionsName)` inicial, em vez de aparecer em todas as chamadas subsequentes.</span><span class="sxs-lookup"><span data-stu-id="22bb7-192">`OptionsBuilder` streamlines creating named options as it's only a single parameter to the initial `AddOptions<TOptions>(string optionsName)` call instead of appearing in all of the subsequent calls.</span></span> <span data-ttu-id="22bb7-193">A validação de opções e as sobrecargas `ConfigureOptions` que aceitam dependências de serviço só estão disponíveis por meio de `OptionsBuilder`.</span><span class="sxs-lookup"><span data-stu-id="22bb7-193">Options validation and the `ConfigureOptions` overloads that accept service dependencies are only available via `OptionsBuilder`.</span></span>

<span data-ttu-id="22bb7-194">`OptionsBuilder` é usado na seção [validação de opções](#options-validation) .</span><span class="sxs-lookup"><span data-stu-id="22bb7-194">`OptionsBuilder` is used in the [Options validation](#options-validation) section.</span></span>

## <a name="use-di-services-to-configure-options"></a><span data-ttu-id="22bb7-195">Usar os serviços de injeção de dependência para configurar as opções</span><span class="sxs-lookup"><span data-stu-id="22bb7-195">Use DI services to configure options</span></span>

<span data-ttu-id="22bb7-196">Os serviços podem ser acessados da injeção de dependência ao configurar opções de duas maneiras:</span><span class="sxs-lookup"><span data-stu-id="22bb7-196">Services can be accessed from dependency injection while configuring options in two ways:</span></span>

- <span data-ttu-id="22bb7-197">Passe um delegado de configuração para [Configurar](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) no [OptionsBuilder \<TOptions> ](xref:Microsoft.Extensions.Options.OptionsBuilder%601).</span><span class="sxs-lookup"><span data-stu-id="22bb7-197">Pass a configuration delegate to [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) on [OptionsBuilder\<TOptions>](xref:Microsoft.Extensions.Options.OptionsBuilder%601).</span></span> <span data-ttu-id="22bb7-198">`OptionsBuilder<TOptions>` fornece sobrecargas de [configuração](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) que permitem o uso de até cinco serviços para configurar opções:</span><span class="sxs-lookup"><span data-stu-id="22bb7-198">`OptionsBuilder<TOptions>` provides overloads of [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) that allow use of up to five services to configure options:</span></span>

  ```csharp
  services.AddOptions<MyOptions>("optionalName")
      .Configure<ExampleService, ScopedService, MonitorService>(
          (options, es, ss, ms) =>
              options.Property = DoSomethingWith(es, ss, ms));
  ```

- <span data-ttu-id="22bb7-199">Crie um tipo que implemente <xref:Microsoft.Extensions.Options.IConfigureOptions%601> ou <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> Registre o tipo como um serviço.</span><span class="sxs-lookup"><span data-stu-id="22bb7-199">Create a type that implements <xref:Microsoft.Extensions.Options.IConfigureOptions%601> or <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601> and register the type as a service.</span></span>

<span data-ttu-id="22bb7-200">É recomendável transmitir um delegado de configuração para [Configurar](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A), já que a criação de um serviço é algo mais complexo.</span><span class="sxs-lookup"><span data-stu-id="22bb7-200">We recommend passing a configuration delegate to [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A), since creating a service is more complex.</span></span> <span data-ttu-id="22bb7-201">Criar um tipo é equivalente ao que a estrutura faz ao chamar [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A).</span><span class="sxs-lookup"><span data-stu-id="22bb7-201">Creating a type is equivalent to what the framework does when calling [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A).</span></span> <span data-ttu-id="22bb7-202">Chamar [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) registra um genérico transitório <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601>, que tem um construtor que aceita os tipos de serviço genérico especificados.</span><span class="sxs-lookup"><span data-stu-id="22bb7-202">Calling [Configure](xref:Microsoft.Extensions.Options.OptionsBuilder%601.Configure%2A) registers a transient generic <xref:Microsoft.Extensions.Options.IConfigureNamedOptions%601>, which has a constructor that accepts the generic service types specified.</span></span>

## <a name="options-validation"></a><span data-ttu-id="22bb7-203">Validação de opções</span><span class="sxs-lookup"><span data-stu-id="22bb7-203">Options validation</span></span>

<span data-ttu-id="22bb7-204">A validação de opções permite que os valores de opção sejam validados.</span><span class="sxs-lookup"><span data-stu-id="22bb7-204">Options validation enables option values to be validated.</span></span>

<span data-ttu-id="22bb7-205">Considere o seguinte *appsettings.jsno* arquivo:</span><span class="sxs-lookup"><span data-stu-id="22bb7-205">Consider the following *appsettings.json* file:</span></span>

```json
{
  "Settings": {
    "SiteTitle": "Amazing docs from Awesome people!",
    "Scale": 10,
    "VerbosityLevel": 32
  }
}
```

<span data-ttu-id="22bb7-206">A seguinte classe é associada à `"Settings"` seção de configuração e aplica algumas `DataAnnotations` regras:</span><span class="sxs-lookup"><span data-stu-id="22bb7-206">The following class binds to the `"Settings"` configuration section and applies a couple of `DataAnnotations` rules:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/SettingsOptions.cs":::

<span data-ttu-id="22bb7-207">O seguinte código:</span><span class="sxs-lookup"><span data-stu-id="22bb7-207">The following code:</span></span>

- <span data-ttu-id="22bb7-208">Chama <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> para obter um [OptionsBuilder \<TOptions> ](xref:Microsoft.Extensions.Options.OptionsBuilder%601) que se associa à `SettingsOptions` classe.</span><span class="sxs-lookup"><span data-stu-id="22bb7-208">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.AddOptions%2A> to get an [OptionsBuilder\<TOptions>](xref:Microsoft.Extensions.Options.OptionsBuilder%601) that binds to the `SettingsOptions` class.</span></span>
- <span data-ttu-id="22bb7-209">Chamadas <xref:Microsoft.Extensions.DependencyInjection.OptionsBuilderDataAnnotationsExtensions.ValidateDataAnnotations%2A> para habilitar a validação usando `DataAnnotations` .</span><span class="sxs-lookup"><span data-stu-id="22bb7-209">Calls <xref:Microsoft.Extensions.DependencyInjection.OptionsBuilderDataAnnotationsExtensions.ValidateDataAnnotations%2A> to enable validation using `DataAnnotations`.</span></span>

```csharp
services.AddOptions<SettingsOptions>()
    .Bind(Configuration.GetSection(SettingsOptions.Settings))
    .ValidateDataAnnotations();
```

<span data-ttu-id="22bb7-210">O `ValidateDataAnnotations` método de extensão é definido no pacote NuGet [Microsoft. Extensions. Options. Annotations](https://www.nuget.org/packages/Microsoft.Extensions.Options.DataAnnotations) .</span><span class="sxs-lookup"><span data-stu-id="22bb7-210">The `ValidateDataAnnotations` extension method is defined in the [Microsoft.Extensions.Options.DataAnnotations](https://www.nuget.org/packages/Microsoft.Extensions.Options.DataAnnotations) NuGet package.</span></span>

<span data-ttu-id="22bb7-211">O código a seguir exibe os valores de configuração ou os erros de validação:</span><span class="sxs-lookup"><span data-stu-id="22bb7-211">The following code displays the configuration values or the validation errors:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ValidationService.cs":::

<span data-ttu-id="22bb7-212">O código a seguir aplica uma regra de validação mais complexa usando um delegado:</span><span class="sxs-lookup"><span data-stu-id="22bb7-212">The following code applies a more complex validation rule using a delegate:</span></span>

```csharp
services.AddOptions<SettingsOptions>()
    .Bind(Configuration.GetSection(SettingsOptions.Settings))
    .ValidateDataAnnotations()
    .Validate(config =>
    {
        if (config.Scale != 0)
        {
            return config.VerbosityLevel > config.Scale;
        }

        return true;
    }, "VerbosityLevel must be > than Scale.");
```

### <a name="ivalidateoptions-for-complex-validation"></a><span data-ttu-id="22bb7-213">IValidateOptions para validação complexa</span><span class="sxs-lookup"><span data-stu-id="22bb7-213">IValidateOptions for complex validation</span></span>

<span data-ttu-id="22bb7-214">A seguinte classe implementa <xref:Microsoft.Extensions.Options.IValidateOptions%601> :</span><span class="sxs-lookup"><span data-stu-id="22bb7-214">The following class implements <xref:Microsoft.Extensions.Options.IValidateOptions%601>:</span></span>

:::code language="csharp" source="snippets/configuration/console-json/ValidateSettingsOptions.cs":::

<span data-ttu-id="22bb7-215">`IValidateOptions` permite mover o código de validação para uma classe.</span><span class="sxs-lookup"><span data-stu-id="22bb7-215">`IValidateOptions` enables moving the validation code into a class.</span></span>

<span data-ttu-id="22bb7-216">Usando o código anterior, a validação é habilitada no `ConfigureServices` com o seguinte código:</span><span class="sxs-lookup"><span data-stu-id="22bb7-216">Using the preceding code, validation is enabled in `ConfigureServices` with the following code:</span></span>

```csharp
services.Configure<SettingsOptions>(
    Configuration.GetSection(
        SettingsOptions.Settings));
services.TryAddEnumerable(
    ServiceDescriptor.Singleton
        <IValidateOptions<SettingsOptions>, ValidateSettingsOptions>());
```

## <a name="options-post-configuration"></a><span data-ttu-id="22bb7-217">Pós-configuração de opções</span><span class="sxs-lookup"><span data-stu-id="22bb7-217">Options post-configuration</span></span>

<span data-ttu-id="22bb7-218">Defina a pós-configuração com <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601>.</span><span class="sxs-lookup"><span data-stu-id="22bb7-218">Set post-configuration with <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601>.</span></span> <span data-ttu-id="22bb7-219">Pós-configuração é executado depois <xref:Microsoft.Extensions.Options.IConfigureOptions%601> que toda a configuração ocorre e pode ser útil em cenários quando você precisa substituir a configuração:</span><span class="sxs-lookup"><span data-stu-id="22bb7-219">Post-configuration runs after all <xref:Microsoft.Extensions.Options.IConfigureOptions%601> configuration occurs, and can be useful in scenarios when you need to override configuration:</span></span>

```csharp
services.PostConfigure<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

<span data-ttu-id="22bb7-220">O <xref:Microsoft.Extensions.Options.IPostConfigureOptions%601.PostConfigure%2A> está disponível para pós-configurar opções nomeadas:</span><span class="sxs-lookup"><span data-stu-id="22bb7-220"><xref:Microsoft.Extensions.Options.IPostConfigureOptions%601.PostConfigure%2A> is available to post-configure named options:</span></span>

```csharp
services.PostConfigure<CustomOptions>("named_options_1", customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

<span data-ttu-id="22bb7-221">Use <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> para pós-configurar todas as instâncias de configuração:</span><span class="sxs-lookup"><span data-stu-id="22bb7-221">Use <xref:Microsoft.Extensions.DependencyInjection.OptionsServiceCollectionExtensions.PostConfigureAll%2A> to post-configure all configuration instances:</span></span>

```csharp
services.PostConfigureAll<CustomOptions>(customOptions =>
{
    customOptions.Option1 = "post_configured_option1_value";
});
```

## <a name="see-also"></a><span data-ttu-id="22bb7-222">Confira também</span><span class="sxs-lookup"><span data-stu-id="22bb7-222">See also</span></span>

- [<span data-ttu-id="22bb7-223">Configuração no .NET</span><span class="sxs-lookup"><span data-stu-id="22bb7-223">Configuration in .NET</span></span>](configuration.md)
