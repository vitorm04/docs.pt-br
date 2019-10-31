---
title: Novidades do .NET Core 2.1
description: Conheça os novos recursos encontrados no .NET Core 2.1.
dev_langs:
- csharp
- vb
ms.date: 10/10/2018
ms.openlocfilehash: 603e7ae4ffb9e6a4bb477af9597d6948bd63f55e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73100746"
---
# <a name="whats-new-in-net-core-21"></a><span data-ttu-id="dc3be-103">Novidades do .NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="dc3be-103">What's new in .NET Core 2.1</span></span>

<span data-ttu-id="dc3be-104">O .NET Core 2.1 contém melhorias e novos recursos nas seguintes áreas:</span><span class="sxs-lookup"><span data-stu-id="dc3be-104">.NET Core 2.1 includes enhancements and new features in the following areas:</span></span>

- [<span data-ttu-id="dc3be-105">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="dc3be-105">Tooling</span></span>](#tooling)
- [<span data-ttu-id="dc3be-106">Efetuar roll forward</span><span class="sxs-lookup"><span data-stu-id="dc3be-106">Roll forward</span></span>](#roll-forward)
- [<span data-ttu-id="dc3be-107">Implantação</span><span class="sxs-lookup"><span data-stu-id="dc3be-107">Deployment</span></span>](#deployment)
- [<span data-ttu-id="dc3be-108">Pacote de Compatibilidade do Windows</span><span class="sxs-lookup"><span data-stu-id="dc3be-108">Windows Compatibility Pack</span></span>](#windows-compatibility-pack)
- [<span data-ttu-id="dc3be-109">Aprimoramentos da compilação JIT</span><span class="sxs-lookup"><span data-stu-id="dc3be-109">JIT compilation improvements</span></span>](#jit-compiler-improvements)
- [<span data-ttu-id="dc3be-110">Alterações na API</span><span class="sxs-lookup"><span data-stu-id="dc3be-110">API changes</span></span>](#api-changes)

## <a name="tooling"></a><span data-ttu-id="dc3be-111">Ferramentas</span><span class="sxs-lookup"><span data-stu-id="dc3be-111">Tooling</span></span>

<span data-ttu-id="dc3be-112">O SDK do .NET Core 2.1 (v 2.1.300), o conjunto de ferramentas incluído no .NET Core 2.1, inclui as seguintes alterações e aprimoramentos:</span><span class="sxs-lookup"><span data-stu-id="dc3be-112">The .NET Core 2.1 SDK (v 2.1.300), the tooling included with .NET Core 2.1, includes the following changes and enhancements:</span></span>

### <a name="build-performance-improvements"></a><span data-ttu-id="dc3be-113">Melhorias de desempenho de build</span><span class="sxs-lookup"><span data-stu-id="dc3be-113">Build performance improvements</span></span>

<span data-ttu-id="dc3be-114">Um dos principais focos do .NET Core 2.1 é melhorar o desempenho de tempo de build, especialmente para builds incrementais.</span><span class="sxs-lookup"><span data-stu-id="dc3be-114">A major focus of .NET Core 2.1 is improving build-time performance, particularly for incremental builds.</span></span> <span data-ttu-id="dc3be-115">Essas melhorias de desempenho se aplicam a ambos os builds de linha de comando que usam `dotnet build` e a builds no Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="dc3be-115">These performance improvements apply to both command-line builds using `dotnet build` and to builds in Visual Studio.</span></span> <span data-ttu-id="dc3be-116">Algumas áreas individuais de melhoria incluem:</span><span class="sxs-lookup"><span data-stu-id="dc3be-116">Some individual areas of improvement include:</span></span>

- <span data-ttu-id="dc3be-117">Na resolução de ativos de pacote, resolução somente de ativos usados por um build, em vez de todos os ativos.</span><span class="sxs-lookup"><span data-stu-id="dc3be-117">For package asset resolution, resolving only assets used by a build rather than all assets.</span></span>

- <span data-ttu-id="dc3be-118">Armazenamento em cache de referências de assembly.</span><span class="sxs-lookup"><span data-stu-id="dc3be-118">Caching of assembly references.</span></span>

- <span data-ttu-id="dc3be-119">Uso de servidores de build do SDK de longa execução, que são processos que se estendem por chamadas individuais de `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="dc3be-119">Use of long-running SDK build servers, which are processes that span across individual `dotnet build` invocations.</span></span> <span data-ttu-id="dc3be-120">Eles eliminam a necessidade de compilação JIT de grandes blocos de código toda vez que `dotnet build` é executado.</span><span class="sxs-lookup"><span data-stu-id="dc3be-120">They eliminate the need to JIT-compile large blocks of code every time `dotnet build` is run.</span></span> <span data-ttu-id="dc3be-121">Os processos do servidor de build podem ser finalizados automaticamente com o seguinte comando:</span><span class="sxs-lookup"><span data-stu-id="dc3be-121">Build server processes can be automatically terminated with the following command:</span></span>

   ```dotnetcli
   dotnet buildserver shutdown
   ```

### <a name="new-cli-commands"></a><span data-ttu-id="dc3be-122">Novos comandos da CLI</span><span class="sxs-lookup"><span data-stu-id="dc3be-122">New CLI commands</span></span>

<span data-ttu-id="dc3be-123">Várias ferramentas que estavam disponíveis apenas por projeto usando [`DotnetCliToolReference`](../tools/extensibility.md) agora estão disponíveis como parte do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc3be-123">A number of tools that were available only on a per project basis using [`DotnetCliToolReference`](../tools/extensibility.md) are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="dc3be-124">Essas ferramentas incluem:</span><span class="sxs-lookup"><span data-stu-id="dc3be-124">These tools include:</span></span>

- <span data-ttu-id="dc3be-125">`dotnet watch` fornece um observador do sistema de arquivos que aguarda que um arquivo seja alterado antes de executar um conjunto designado de comandos.</span><span class="sxs-lookup"><span data-stu-id="dc3be-125">`dotnet watch` provides a file system watcher that waits for a file to change before executing a designated set of commands.</span></span> <span data-ttu-id="dc3be-126">Por exemplo, o comando a seguir recria automaticamente o projeto atual e gera uma saída detalhada sempre que um arquivo é alterado nele:</span><span class="sxs-lookup"><span data-stu-id="dc3be-126">For example, the following command automatically rebuilds the current project and generates verbose output whenever a file in it changes:</span></span>

   ```dotnetcli
   dotnet watch -- --verbose build
   ```

   <span data-ttu-id="dc3be-127">Observe a opção `--` que precede a opção `--verbose`.</span><span class="sxs-lookup"><span data-stu-id="dc3be-127">Note the `--` option that precedes the `--verbose` option.</span></span> <span data-ttu-id="dc3be-128">Isso delimita as opções passadas diretamente para o comando `dotnet watch` dos argumentos que são passados para o processo `dotnet` filho.</span><span class="sxs-lookup"><span data-stu-id="dc3be-128">It delimits the options passed directly to the `dotnet watch` command from the arguments that are passed to the child `dotnet` process.</span></span> <span data-ttu-id="dc3be-129">Sem isso, a opção `--verbose` se aplica ao comando `dotnet watch`, não ao comando `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="dc3be-129">Without it, the `--verbose` option applies to the `dotnet watch` command, not the `dotnet build` command.</span></span>
  
   <span data-ttu-id="dc3be-130">Para obter mais informações, consulte [desenvolver ASP.NET Core aplicativos usando o relógio dotnet](/aspnet/core/tutorials/dotnet-watch).</span><span class="sxs-lookup"><span data-stu-id="dc3be-130">For more information, see [Develop ASP.NET Core apps using dotnet watch](/aspnet/core/tutorials/dotnet-watch).</span></span>

- <span data-ttu-id="dc3be-131">`dotnet dev-certs` gera e gerencia os certificados usados durante o desenvolvimento de aplicativos do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc3be-131">`dotnet dev-certs` generates and manages certificates used during development in ASP.NET Core applications.</span></span>

- <span data-ttu-id="dc3be-132">`dotnet user-secrets` gerencia os segredos em um repositório de segredos do usuário em aplicativos do ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc3be-132">`dotnet user-secrets` manages the secrets in a user secret store in ASP.NET Core applications.</span></span>

- <span data-ttu-id="dc3be-133">`dotnet sql-cache` cria uma tabela e índices em um banco de dados do Microsoft SQL Server a serem usados para armazenamento em cache distribuído.</span><span class="sxs-lookup"><span data-stu-id="dc3be-133">`dotnet sql-cache` creates a table and indexes in a Microsoft SQL Server database to be used for distributed caching.</span></span>

- <span data-ttu-id="dc3be-134">`dotnet ef` é uma ferramenta para gerenciar bancos de dados, objetos <xref:Microsoft.EntityFrameworkCore.DbContext> e migrações em aplicativos Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="dc3be-134">`dotnet ef` is a tool for managing databases, <xref:Microsoft.EntityFrameworkCore.DbContext> objects, and migrations in Entity Framework Core applications.</span></span> <span data-ttu-id="dc3be-135">Para saber mais, confira [Ferramentas da linha de comando do .NET EF Core](/ef/core/miscellaneous/cli/dotnet).</span><span class="sxs-lookup"><span data-stu-id="dc3be-135">For more information, see [EF Core .NET Command-line Tools](/ef/core/miscellaneous/cli/dotnet).</span></span>

### <a name="global-tools"></a><span data-ttu-id="dc3be-136">Ferramentas Globais</span><span class="sxs-lookup"><span data-stu-id="dc3be-136">Global Tools</span></span>

<span data-ttu-id="dc3be-137">O .NET Core 2.1 oferece suporte a *Ferramentas Globais*, ou seja, ferramentas personalizadas que estão disponíveis globalmente a partir da linha de comando.</span><span class="sxs-lookup"><span data-stu-id="dc3be-137">.NET Core 2.1 supports *Global Tools* -- that is, custom tools that are available globally from the command line.</span></span> <span data-ttu-id="dc3be-138">O modelo de extensibilidade em versões anteriores do .NET Core disponibilizava ferramentas personalizadas apenas por projeto usando [`DotnetCliToolReference`](../tools/extensibility.md#consuming-per-project-tools).</span><span class="sxs-lookup"><span data-stu-id="dc3be-138">The extensibility model in previous versions of .NET Core made custom tools available on a per project basis only by using [`DotnetCliToolReference`](../tools/extensibility.md#consuming-per-project-tools).</span></span>

<span data-ttu-id="dc3be-139">Para instalar uma Ferramenta Global, use o comando [dotnet tool install](../tools/dotnet-tool-install.md).</span><span class="sxs-lookup"><span data-stu-id="dc3be-139">To install a Global Tool, you use the [dotnet tool install](../tools/dotnet-tool-install.md) command.</span></span> <span data-ttu-id="dc3be-140">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="dc3be-140">For example:</span></span>

```dotnetcli
dotnet tool install -g dotnetsay
```

<span data-ttu-id="dc3be-141">Uma vez instalada, a ferramenta pode ser executada a partir da linha de comando, especificando o nome da ferramenta.</span><span class="sxs-lookup"><span data-stu-id="dc3be-141">Once installed, the tool can be run from the command line by specifying the tool name.</span></span> <span data-ttu-id="dc3be-142">Para saber mais, confira [Visão geral das Ferramentas Globais do .NET Core](../tools/global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="dc3be-142">For more information, see [.NET Core Global Tools overview](../tools/global-tools.md).</span></span>

### <a name="tool-management-with-the-dotnet-tool-command"></a><span data-ttu-id="dc3be-143">Gerenciamento de ferramentas com o comando `dotnet tool`</span><span class="sxs-lookup"><span data-stu-id="dc3be-143">Tool management with the `dotnet tool` command</span></span>

<span data-ttu-id="dc3be-144">No SDK do .NET Core 2.1, todas as operações de ferramentas usam o comando `dotnet tool`.</span><span class="sxs-lookup"><span data-stu-id="dc3be-144">In .NET Core 2.1 SDK, all tools operations use the `dotnet tool` command.</span></span> <span data-ttu-id="dc3be-145">As seguintes opções estão disponíveis:</span><span class="sxs-lookup"><span data-stu-id="dc3be-145">The following options are available:</span></span>

- <span data-ttu-id="dc3be-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) para instalar uma ferramenta.</span><span class="sxs-lookup"><span data-stu-id="dc3be-146">[`dotnet tool install`](../tools/dotnet-tool-install.md) to install a tool.</span></span>

- <span data-ttu-id="dc3be-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) para desinstalar e reinstalar uma ferramenta, o que a atualiza com eficiência.</span><span class="sxs-lookup"><span data-stu-id="dc3be-147">[`dotnet tool update`](../tools/dotnet-tool-update.md) to uninstall and reinstall a tool, which effectively updates it.</span></span>

- <span data-ttu-id="dc3be-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) para listar ferramentas atualmente instaladas.</span><span class="sxs-lookup"><span data-stu-id="dc3be-148">[`dotnet tool list`](../tools/dotnet-tool-list.md) to list currently installed tools.</span></span>

- <span data-ttu-id="dc3be-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) para desinstalar ferramentas atualmente instaladas.</span><span class="sxs-lookup"><span data-stu-id="dc3be-149">[`dotnet tool uninstall`](../tools/dotnet-tool-uninstall.md) to uninstall currently installed tools.</span></span>

## <a name="roll-forward"></a><span data-ttu-id="dc3be-150">Efetuar roll forward</span><span class="sxs-lookup"><span data-stu-id="dc3be-150">Roll forward</span></span>

<span data-ttu-id="dc3be-151">Do .NET Core 2.0 em diante, todos os aplicativos .NET Core efetuam roll forward automaticamente para a última *versão secundária* instalada em um sistema.</span><span class="sxs-lookup"><span data-stu-id="dc3be-151">All .NET Core applications starting with .NET Core 2.0 automatically roll forward to the latest *minor version* installed on a system.</span></span>

<span data-ttu-id="dc3be-152">A partir do .NET Core 2.0, se a versão do .NET Core com a qual um aplicativo foi criado não estiver presente no tempo de execução, o aplicativo será executado automaticamente com a *versão secundária* do .NET Core instalada mais recente.</span><span class="sxs-lookup"><span data-stu-id="dc3be-152">Starting with .NET Core 2.0, if the version of .NET Core that an application was built with is not present at runtime, the application automatically runs against the latest installed *minor version* of .NET Core.</span></span> <span data-ttu-id="dc3be-153">Em outras palavras, se um aplicativo for criado com o .NET Core 2.0, e o .NET Core 2.0 não estiver presente no sistema do host, mas o .NET Core 2.1 estiver, o aplicativo será executado com o .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="dc3be-153">In other words, if an application is built with .NET Core 2.0, and .NET Core 2.0 is not present on the host system but .NET Core 2.1 is, the application runs with .NET Core 2.1.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="dc3be-154">Esse comportamento de roll-forward não se aplica a versões prévias.</span><span class="sxs-lookup"><span data-stu-id="dc3be-154">This roll-forward behavior doesn't apply to preview releases.</span></span> <span data-ttu-id="dc3be-155">Por padrão, ele também não se aplica a versões principais, mas isso pode ser alterado com as configurações abaixo.</span><span class="sxs-lookup"><span data-stu-id="dc3be-155">By default, it also doesn't apply to major releases, but this can be changed with the settings below.</span></span>

<span data-ttu-id="dc3be-156">Modifique esse comportamento alterando a configuração de roll forward em nenhuma estrutura compartilhada candidata.</span><span class="sxs-lookup"><span data-stu-id="dc3be-156">You can modify this behavior by changing the setting for the roll-forward on no candidate shared framework.</span></span> <span data-ttu-id="dc3be-157">As configurações disponíveis são:</span><span class="sxs-lookup"><span data-stu-id="dc3be-157">The available settings are:</span></span>

- <span data-ttu-id="dc3be-158">`0` – desabilitar o comportamento de roll forward da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="dc3be-158">`0` - disable minor version roll-forward behavior.</span></span> <span data-ttu-id="dc3be-159">Com essa configuração, um aplicativo criado para o .NET Core 2.0.0 efetuará roll forward para o .NET Core 2.0.1, mas não para o .NET Core 2.2.0 ou o .NET Core 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="dc3be-159">With this setting, an application built for .NET Core 2.0.0 will roll forward to .NET Core 2.0.1, but not to .NET Core 2.2.0 or .NET Core 3.0.0.</span></span>
- <span data-ttu-id="dc3be-160">`1` – habilitar o comportamento de roll forward da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="dc3be-160">`1` - enable minor version roll-forward behavior.</span></span> <span data-ttu-id="dc3be-161">Esse é o valor padrão para a configuração.</span><span class="sxs-lookup"><span data-stu-id="dc3be-161">This is the default value for the setting.</span></span> <span data-ttu-id="dc3be-162">Com essa configuração, um aplicativo criado para o .NET Core 2.0.0 efetuará roll forward para o .NET Core 2.0.1 ou o .NET Core 2.2.0, dependendo de qual estiver instalado, mas não efetuará roll forward para o .NET Core 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="dc3be-162">With this setting, an application built for .NET Core 2.0.0 will roll forward to either .NET Core 2.0.1 or .NET Core 2.2.0, depending on which one is installed, but it will not roll forward to .NET Core 3.0.0.</span></span>
- <span data-ttu-id="dc3be-163">`2` – habilitar o comportamento de roll forward das versões secundária e principal.</span><span class="sxs-lookup"><span data-stu-id="dc3be-163">`2` - enable minor and major version roll-forward behavior.</span></span> <span data-ttu-id="dc3be-164">Se essa opção estiver definida, até mesmo versões principais diferentes serão consideradas e, portanto, um aplicativo criado para o .NET Core 2.0.0 efetuará roll forward para o .NET Core 3.0.0.</span><span class="sxs-lookup"><span data-stu-id="dc3be-164">If set, even different major versions are considered, so an application built for .NET Core 2.0.0 will roll forward to .NET Core 3.0.0.</span></span>

<span data-ttu-id="dc3be-165">Modifique essa configuração de uma das três maneiras:</span><span class="sxs-lookup"><span data-stu-id="dc3be-165">You can modify this setting in any of three ways:</span></span>

- <span data-ttu-id="dc3be-166">Defina a variável de ambiente `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` com o valor desejado.</span><span class="sxs-lookup"><span data-stu-id="dc3be-166">Set the `DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` environment variable to the desired value.</span></span>

- <span data-ttu-id="dc3be-167">Adicione a seguinte linha com o valor desejado ao arquivo *.runtimeconfig.json*:</span><span class="sxs-lookup"><span data-stu-id="dc3be-167">Add the following line with the desired value to the *.runtimeconfig.json* file:</span></span>

   ```json
   "rollForwardOnNoCandidateFx" : 0
   ```

- <span data-ttu-id="dc3be-168">Ao usar as [ferramentas da CLI do .NET Core](../tools/index.md), adicione a seguinte opção com o valor desejado a um comando do .NET Core como `run`:</span><span class="sxs-lookup"><span data-stu-id="dc3be-168">When using [.NET Core CLI tools](../tools/index.md), add the following option with the desired value to a .NET Core command such as `run`:</span></span>

   ```dotnetcli
   dotnet run --rollForwardOnNoCandidateFx=0
   ```

<span data-ttu-id="dc3be-169">O roll forward da versão de patch é independente dessa configuração e é feito após a aplicação de qualquer roll forward potencial da versão secundária ou principal.</span><span class="sxs-lookup"><span data-stu-id="dc3be-169">Patch version roll forward is independent of this setting and is done after any potential minor or major version roll forward is applied.</span></span>

## <a name="deployment"></a><span data-ttu-id="dc3be-170">Implantação</span><span class="sxs-lookup"><span data-stu-id="dc3be-170">Deployment</span></span>

### <a name="self-contained-application-servicing"></a><span data-ttu-id="dc3be-171">Serviço de aplicativo autocontido</span><span class="sxs-lookup"><span data-stu-id="dc3be-171">Self-contained application servicing</span></span>

<span data-ttu-id="dc3be-172">`dotnet publish` agora publica aplicativos autocontidos com uma versão de tempo de execução atendido.</span><span class="sxs-lookup"><span data-stu-id="dc3be-172">`dotnet publish` now publishes self-contained applications with a serviced runtime version.</span></span> <span data-ttu-id="dc3be-173">Quando você publica um aplicativo autocontido com o SDK do .NET Core 2.1 (v 2.1.300), seu aplicativo inclui a versão mais recente de tempo de execução atendido conhecida por esse SDK.</span><span class="sxs-lookup"><span data-stu-id="dc3be-173">When you publish a self-contained application with the .NET Core 2.1 SDK (v 2.1.300), your application includes the latest serviced runtime version known by that SDK.</span></span> <span data-ttu-id="dc3be-174">Quando você faz upgrade para o SDK mais recente, publica com a versão mais recente do tempo de execução do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc3be-174">When you upgrade to the latest SDK, you’ll publish with the latest .NET Core runtime version.</span></span> <span data-ttu-id="dc3be-175">Isso se aplica aos tempos de execução do .NET Core 1.0 e posteriores.</span><span class="sxs-lookup"><span data-stu-id="dc3be-175">This applies for .NET Core 1.0 runtimes and later.</span></span>

<span data-ttu-id="dc3be-176">A publicação independente depende das versões de tempo de execução no NuGet.org. Você não precisa ter o tempo de execução de serviço em seu computador.</span><span class="sxs-lookup"><span data-stu-id="dc3be-176">Self-contained publishing relies on runtime versions on NuGet.org. You do not need to have the serviced runtime on your machine.</span></span>

<span data-ttu-id="dc3be-177">Com o uso do SDK do .NET Core 2.0, os aplicativos autocontidos são publicados com o tempo de execução do .NET Core 2.0.0, a menos que uma versão diferente seja especificada por meio da propriedade `RuntimeFrameworkVersion`.</span><span class="sxs-lookup"><span data-stu-id="dc3be-177">Using the .NET Core 2.0 SDK, self-contained applications are published with the .NET Core 2.0.0 runtime unless a different version is specified via the `RuntimeFrameworkVersion` property.</span></span> <span data-ttu-id="dc3be-178">Com esse novo comportamento, você não precisará mais definir essa propriedade para selecionar uma versão de tempo de execução maior para um aplicativo autocontido.</span><span class="sxs-lookup"><span data-stu-id="dc3be-178">With this new behavior, you’ll no longer need to set this property to select a higher runtime version for a self-contained application.</span></span> <span data-ttu-id="dc3be-179">A abordagem mais fácil daqui para frente é sempre publicar com o SDK do .NET Core 2.1 (v 2.1.300).</span><span class="sxs-lookup"><span data-stu-id="dc3be-179">The easiest approach going forward is to always publish with .NET Core 2.1 SDK (v 2.1.300).</span></span>

<span data-ttu-id="dc3be-180">Veja mais informações em [Efetuar roll forward de tempo de execução de implantação autossuficiente](../deploying/runtime-patch-selection.md).</span><span class="sxs-lookup"><span data-stu-id="dc3be-180">For more information, see [Self-contained deployment runtime roll forward](../deploying/runtime-patch-selection.md).</span></span>
## <a name="windows-compatibility-pack"></a><span data-ttu-id="dc3be-181">Pacote de Compatibilidade do Windows</span><span class="sxs-lookup"><span data-stu-id="dc3be-181">Windows Compatibility Pack</span></span>

<span data-ttu-id="dc3be-182">Ao transmitir código existente do .NET Framework para o .NET Core, você pode usar o [Pacote de Compatibilidade do Windows](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span><span class="sxs-lookup"><span data-stu-id="dc3be-182">When you port existing code from the .NET Framework to .NET Core, you can use the [Windows Compatibility Pack](https://www.nuget.org/packages/Microsoft.Windows.Compatibility).</span></span> <span data-ttu-id="dc3be-183">Ele fornece acesso 20.000 APIs a mais do que as disponíveis no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc3be-183">It provides access to 20,000 more APIs than are available in .NET Core.</span></span> <span data-ttu-id="dc3be-184">Essas APIs incluem tipos no namespace <xref:System.Drawing?displayProperty=nameWithType>, a classe <xref:System.Diagnostics.EventLog>, WMI, contadores de desempenho, Windows Services e os tipos de registro e membros do Windows.</span><span class="sxs-lookup"><span data-stu-id="dc3be-184">These APIs include types in the <xref:System.Drawing?displayProperty=nameWithType> namespace, the <xref:System.Diagnostics.EventLog> class, WMI, Performance Counters, Windows Services, and the Windows registry types and members.</span></span>

## <a name="jit-compiler-improvements"></a><span data-ttu-id="dc3be-185">Melhorias do compilador JIT</span><span class="sxs-lookup"><span data-stu-id="dc3be-185">JIT compiler improvements</span></span>

<span data-ttu-id="dc3be-186">O .NET Core incorpora uma nova tecnologia de compilador JIT chamada de *compilação em camadas* (também conhecida como *otimização adaptativa*) que pode melhorar significativamente o desempenho.</span><span class="sxs-lookup"><span data-stu-id="dc3be-186">.NET Core incorporates a new JIT compiler technology called *tiered compilation* (also known as *adaptive optimization*) that can significantly improve performance.</span></span> <span data-ttu-id="dc3be-187">A compilação em camadas é uma configuração opcional.</span><span class="sxs-lookup"><span data-stu-id="dc3be-187">Tiered compilation is an opt-in setting.</span></span>

<span data-ttu-id="dc3be-188">Uma das tarefas importantes executadas pelo compilador JIT é otimizar a execução de código.</span><span class="sxs-lookup"><span data-stu-id="dc3be-188">One of the important tasks performed by the JIT compiler is optimizing code execution.</span></span> <span data-ttu-id="dc3be-189">No entanto, para caminhos de código pouco usados, o compilador pode gastar mais tempo otimizando o código do que o tempo de execução gasta executando código não otimizado.</span><span class="sxs-lookup"><span data-stu-id="dc3be-189">For little-used code paths, however, the compiler may spend more time optimizing code than the runtime spends running unoptimized code.</span></span> <span data-ttu-id="dc3be-190">A compilação em camadas introduz dois estágios na compilação JIT:</span><span class="sxs-lookup"><span data-stu-id="dc3be-190">Tiered compilation introduces two stages in JIT compilation:</span></span>

- <span data-ttu-id="dc3be-191">Uma **primeira camada**, que gera código o mais rápido possível.</span><span class="sxs-lookup"><span data-stu-id="dc3be-191">A **first tier**, which generates code as quickly as possible.</span></span>

- <span data-ttu-id="dc3be-192">Uma **segunda camada**, que gera código otimizado para os métodos executados com frequência.</span><span class="sxs-lookup"><span data-stu-id="dc3be-192">A **second tier**, which generates optimized code for those methods that are executed frequently.</span></span> <span data-ttu-id="dc3be-193">A segunda camada de compilação é executada em paralelo para melhorar o desempenho.</span><span class="sxs-lookup"><span data-stu-id="dc3be-193">The second tier of compilation is performed in parallel for enhanced performance.</span></span>

<span data-ttu-id="dc3be-194">Você pode optar pela compilação em camadas de duas maneiras.</span><span class="sxs-lookup"><span data-stu-id="dc3be-194">You can opt into tiered compilation in either of two ways.</span></span>

- <span data-ttu-id="dc3be-195">Para usar a compilação em camadas em todos os projetos que usam o SDK do .NET Core 2.1, defina a seguinte variável de ambiente:</span><span class="sxs-lookup"><span data-stu-id="dc3be-195">To use tiered compilation in all projects that use the .NET Core 2.1 SDK, set the following environment variable:</span></span>

  ```console
  COMPlus_TieredCompilation="1"
  ```

- <span data-ttu-id="dc3be-196">Para usar a compilação em camadas por projeto, adicione a propriedade `<TieredCompilation>` à seção `<PropertyGroup>` do arquivo de projeto MSBuild, como mostra o exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="dc3be-196">To use tiered compilation on a per-project basis, add the `<TieredCompilation>` property to the `<PropertyGroup>` section of the MSBuild project file, as the following example shows:</span></span>

   ```xml
   <PropertyGroup>
      <!-- other property definitions -->

      <TieredCompilation>true</TieredCompilation>
   </PropertyGroup>
   ```

## <a name="api-changes"></a><span data-ttu-id="dc3be-197">Alterações na API</span><span class="sxs-lookup"><span data-stu-id="dc3be-197">API changes</span></span>

### <a name="spant-and-memoryt"></a><span data-ttu-id="dc3be-198">`Span<T>` e `Memory<T>`</span><span class="sxs-lookup"><span data-stu-id="dc3be-198">`Span<T>` and `Memory<T>`</span></span>

<span data-ttu-id="dc3be-199">O .NET Core 2.1 inclui alguns novos tipos de tornam o trabalho com matrizes e outros tipos de memória muito mais eficiente.</span><span class="sxs-lookup"><span data-stu-id="dc3be-199">.NET Core 2.1 includes some new types that make working with arrays and other types of memory much more efficient.</span></span> <span data-ttu-id="dc3be-200">Os novos tipos incluem:</span><span class="sxs-lookup"><span data-stu-id="dc3be-200">The new types include:</span></span>

- <span data-ttu-id="dc3be-201"><xref:System.Span%601?displayProperty=nameWithType> e <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dc3be-201"><xref:System.Span%601?displayProperty=nameWithType> and <xref:System.ReadOnlySpan%601?displayProperty=nameWithType>.</span></span>

- <span data-ttu-id="dc3be-202"><xref:System.Memory%601?displayProperty=nameWithType> e <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dc3be-202"><xref:System.Memory%601?displayProperty=nameWithType> and <xref:System.ReadOnlyMemory%601?displayProperty=nameWithType>.</span></span>

<span data-ttu-id="dc3be-203">Sem esses tipos, ao transmitir esses itens como parte de uma matriz ou seção de um buffer de memória, você precisará fazer uma cópia de uma parte dos dados antes de transmiti-los a um método.</span><span class="sxs-lookup"><span data-stu-id="dc3be-203">Without these types, when passing such items as a portion of an array or a section of a memory buffer, you have to make a copy of some portion of the data before passing it to a method.</span></span> <span data-ttu-id="dc3be-204">Esses tipos fornecem uma visão virtual desses dados, o que elimina a necessidade de alocação de memória adicional e operações de cópia.</span><span class="sxs-lookup"><span data-stu-id="dc3be-204">These types provide a virtual view of that data that eliminates the need for the additional memory allocation and copy operations.</span></span>

<span data-ttu-id="dc3be-205">O exemplo a seguir usa uma instância <xref:System.Span%601> e <xref:System.Memory%601> para fornecer uma visão virtual de 10 elementos de uma matriz.</span><span class="sxs-lookup"><span data-stu-id="dc3be-205">The following example uses a <xref:System.Span%601> and <xref:System.Memory%601> instance to provide a virtual view of 10 elements of an array.</span></span>

[!code-csharp[Span\<T>](~/samples/core/whats-new/whats-new-in-21/cs/program.cs)]

[!code-vb[Memory\<T>](~/samples/core/whats-new/whats-new-in-21/vb/program.vb)]

### <a name="brotli-compression"></a><span data-ttu-id="dc3be-206">Compactação Brotli</span><span class="sxs-lookup"><span data-stu-id="dc3be-206">Brotli compression</span></span>

<span data-ttu-id="dc3be-207">O .NET Core 2.1 adiciona suporte para compactação e descompactação Brotli.</span><span class="sxs-lookup"><span data-stu-id="dc3be-207">.NET Core 2.1 adds support for Brotli compression and decompression.</span></span> <span data-ttu-id="dc3be-208">Brotli é um algoritmo de compactação sem perda, de uso geral, que é definido em [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) e é compatível com a maioria dos navegadores da Web e com os principais servidores Web.</span><span class="sxs-lookup"><span data-stu-id="dc3be-208">Brotli is a general-purpose lossless compression algorithm that is defined in [RFC 7932](https://www.ietf.org/rfc/rfc7932.txt) and is supported by most web browsers and major web servers.</span></span> <span data-ttu-id="dc3be-209">Você pode usar a classe <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> baseada em fluxo ou as classes <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> e <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> baseadas em span de alto desempenho.</span><span class="sxs-lookup"><span data-stu-id="dc3be-209">You can use the stream-based <xref:System.IO.Compression.BrotliStream?displayProperty=nameWithType> class or the high-performance span-based <xref:System.IO.Compression.BrotliEncoder?displayProperty=nameWithType> and <xref:System.IO.Compression.BrotliDecoder?displayProperty=nameWithType> classes.</span></span> <span data-ttu-id="dc3be-210">O exemplo a seguir ilustra a compactação com a classe <xref:System.IO.Compression.BrotliStream>:</span><span class="sxs-lookup"><span data-stu-id="dc3be-210">The following example illustrates compression with the <xref:System.IO.Compression.BrotliStream> class:</span></span>

[!code-csharp[Brotli compression](~/samples/core/whats-new/whats-new-in-21/cs/brotli.cs#1)]

[!code-vb[Brotli compression](~/samples/core/whats-new/whats-new-in-21/vb/brotli.vb#1)]

<span data-ttu-id="dc3be-211">O comportamento <xref:System.IO.Compression.BrotliStream> é o mesmo de <xref:System.IO.Compression.DeflateStream> e <xref:System.IO.Compression.GZipStream>, o que facilita a conversão de código que chame essas APIs para <xref:System.IO.Compression.BrotliStream>.</span><span class="sxs-lookup"><span data-stu-id="dc3be-211">The <xref:System.IO.Compression.BrotliStream> behavior is the same as <xref:System.IO.Compression.DeflateStream> and <xref:System.IO.Compression.GZipStream>, which makes it easy to convert code that calls these APIs to <xref:System.IO.Compression.BrotliStream>.</span></span>

### <a name="new-cryptography-apis-and-cryptography-improvements"></a><span data-ttu-id="dc3be-212">Novas APIs de criptografia e aprimoramentos de criptografia</span><span class="sxs-lookup"><span data-stu-id="dc3be-212">New cryptography APIs and cryptography improvements</span></span>

<span data-ttu-id="dc3be-213">O .NET Core 2.1 inclui vários aprimoramentos para a APIs de criptografia:</span><span class="sxs-lookup"><span data-stu-id="dc3be-213">.NET Core 2.1 includes numerous enhancements to the cryptography APIs:</span></span>

- <span data-ttu-id="dc3be-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> está disponível no pacote System.Security.Cryptography.Pkcs.</span><span class="sxs-lookup"><span data-stu-id="dc3be-214"><xref:System.Security.Cryptography.Pkcs.SignedCms?displayProperty=nameWithType> is available in the System.Security.Cryptography.Pkcs package.</span></span> <span data-ttu-id="dc3be-215">A implementação é igual à classe <xref:System.Security.Cryptography.Pkcs.SignedCms> no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dc3be-215">The implementation is the same as the <xref:System.Security.Cryptography.Pkcs.SignedCms> class in the .NET Framework.</span></span>

- <span data-ttu-id="dc3be-216">Novas sobrecargas dos métodos <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> e <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> aceitam um identificador de algoritmo de hash para permitir que os chamadores obtenham valores de impressão digital do certificado usando algoritmos diferentes de SHA-1.</span><span class="sxs-lookup"><span data-stu-id="dc3be-216">New overloads of the <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHash%2A?displayProperty=nameWithType> and <xref:System.Security.Cryptography.X509Certificates.X509Certificate.GetCertHashString%2A?displayProperty=nameWithType> methods accept a hash algorithm identifier to enable callers to get certificate thumbprint values using algorithms other than SHA-1.</span></span>

- <span data-ttu-id="dc3be-217">Novas APIs de criptografia baseadas em <xref:System.Span%601> estão disponíveis para hash, HMAC, geração de número aleatório criptográfico, geração de assinatura assimétrica, processamento de assinatura assimétrica e criptografia RSA.</span><span class="sxs-lookup"><span data-stu-id="dc3be-217">New <xref:System.Span%601>-based cryptography APIs are available for hashing, HMAC, cryptographic random number generation, asymmetric signature generation, asymmetric signature processing, and RSA encryption.</span></span>

- <span data-ttu-id="dc3be-218">O desempenho de <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> melhorou em cerca de 15% usando uma implementação baseada em <xref:System.Span%601>.</span><span class="sxs-lookup"><span data-stu-id="dc3be-218">The performance of <xref:System.Security.Cryptography.Rfc2898DeriveBytes?displayProperty=nameWithType> has improved by about 15% by using a <xref:System.Span%601>-based implementation.</span></span>

- <span data-ttu-id="dc3be-219">A nova classe <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> inclui dois novos métodos:</span><span class="sxs-lookup"><span data-stu-id="dc3be-219">The new <xref:System.Security.Cryptography.CryptographicOperations?displayProperty=nameWithType> class includes two new methods:</span></span>

  - <span data-ttu-id="dc3be-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> leva um período fixo para retornar para duas entradas do mesmo tamanho, o que o torna adequado para uso em verificação criptográfica a fim de evitar contribuir com informações de temporização.</span><span class="sxs-lookup"><span data-stu-id="dc3be-220"><xref:System.Security.Cryptography.CryptographicOperations.FixedTimeEquals%2A> takes a fixed amount of time to return for any two inputs of the same length, which makes it suitable for use in cryptographic verification to avoid contributing to timing side-channel information.</span></span>

  - <span data-ttu-id="dc3be-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> é uma rotina de limpeza de memória que não pode ser otimizada.</span><span class="sxs-lookup"><span data-stu-id="dc3be-221"><xref:System.Security.Cryptography.CryptographicOperations.ZeroMemory%2A> is a memory-clearing routine that cannot be optimized.</span></span>

- <span data-ttu-id="dc3be-222">O método estático <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> preenche um <xref:System.Span%601> com valores aleatórios.</span><span class="sxs-lookup"><span data-stu-id="dc3be-222">The static <xref:System.Security.Cryptography.RandomNumberGenerator.Fill%2A?displayProperty=nameWithType> method fills a <xref:System.Span%601> with random values.</span></span>

- <span data-ttu-id="dc3be-223">Agora há suporte para o <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> no Linux e no macOS.</span><span class="sxs-lookup"><span data-stu-id="dc3be-223">The <xref:System.Security.Cryptography.Pkcs.EnvelopedCms?displayProperty=nameWithType> is now supported on Linux and macOS.</span></span>

- <span data-ttu-id="dc3be-224">A curva elíptica Diffie-Hellman (ECDH) agora está disponível na família de classes <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="dc3be-224">Elliptic-Curve Diffie-Hellman (ECDH) is now available in the <xref:System.Security.Cryptography.ECDiffieHellman?displayProperty=nameWithType> class family.</span></span> <span data-ttu-id="dc3be-225">A área de superfície é o mesmo que no .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="dc3be-225">The surface area is the same as in the .NET Framework.</span></span>

- <span data-ttu-id="dc3be-226">A instância retornada por <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> pode criptografar ou descriptografar com OAEP usando um resumo de SHA-2, bem como gerar ou validar assinaturas usando RSA-PSS.</span><span class="sxs-lookup"><span data-stu-id="dc3be-226">The instance returned by <xref:System.Security.Cryptography.RSA.Create%2A?displayProperty=nameWithType> can encrypt or decrypt with OAEP using a SHA-2 digest, as well as generate or validate signatures using RSA-PSS.</span></span>

### <a name="sockets-improvements"></a><span data-ttu-id="dc3be-227">Aperfeiçoamentos de soquetes</span><span class="sxs-lookup"><span data-stu-id="dc3be-227">Sockets improvements</span></span>

<span data-ttu-id="dc3be-228">O .NET Core inclui um novo tipo, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, e um <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType> reescrito, que formam a base de APIs de rede de nível superior.</span><span class="sxs-lookup"><span data-stu-id="dc3be-228">.NET Core includes a new type, <xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, and a rewritten <xref:System.Net.Http.HttpMessageHandler?displayProperty=nameWithType>, that form the basis of higher-level networking APIs.</span></span>  <span data-ttu-id="dc3be-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, por exemplo, é a base da implementação <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="dc3be-229"><xref:System.Net.Http.SocketsHttpHandler?displayProperty=nameWithType>, for example, is the basis of the <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="dc3be-230">Nas versões anteriores do .NET Core, as APIs de nível superior eram baseadas em implementações de redes nativas.</span><span class="sxs-lookup"><span data-stu-id="dc3be-230">In previous versions of .NET Core, higher-level APIs were based on native networking implementations.</span></span>

<span data-ttu-id="dc3be-231">A implementação de soquetes introduzida no .NET Core 2.1 tem várias vantagens:</span><span class="sxs-lookup"><span data-stu-id="dc3be-231">The sockets implementation introduced in .NET Core 2.1 has a number of advantages:</span></span>

- <span data-ttu-id="dc3be-232">Uma melhoria de desempenho significativa quando comparada com a implementação anterior.</span><span class="sxs-lookup"><span data-stu-id="dc3be-232">A significant performance improvement when compared with the previous implementation.</span></span>

- <span data-ttu-id="dc3be-233">Eliminação das dependências da plataforma, o que simplifica a implantação e a manutenção.</span><span class="sxs-lookup"><span data-stu-id="dc3be-233">Elimination of platform dependencies, which simplifies deployment and servicing.</span></span>

- <span data-ttu-id="dc3be-234">Comportamento consistente em todas as plataformas .NET Core.</span><span class="sxs-lookup"><span data-stu-id="dc3be-234">Consistent behavior across all .NET Core platforms.</span></span>

<span data-ttu-id="dc3be-235"><xref:System.Net.Http.SocketsHttpHandler> é a implementação padrão do .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="dc3be-235"><xref:System.Net.Http.SocketsHttpHandler> is the default implementation in .NET Core 2.1.</span></span> <span data-ttu-id="dc3be-236">No entanto, você pode configurar seu aplicativo para usar a classe <xref:System.Net.Http.HttpClientHandler> mais antiga chamando o método <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType>:</span><span class="sxs-lookup"><span data-stu-id="dc3be-236">However, you can configure your application to use the older <xref:System.Net.Http.HttpClientHandler> class by calling the <xref:System.AppContext.SetSwitch%2A?displayProperty=nameWithType> method:</span></span>

```csharp
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", false);
```

```vb
AppContext.SetSwitch("System.Net.Http.UseSocketsHttpHandler", False)
```

<span data-ttu-id="dc3be-237">Também é possível usar uma variável de ambiente para desativar o uso de implementações de soquetes com base em <xref:System.Net.Http.SocketsHttpHandler>.</span><span class="sxs-lookup"><span data-stu-id="dc3be-237">You can also use an environment variable to opt out of using sockets implementations based on <xref:System.Net.Http.SocketsHttpHandler>.</span></span> <span data-ttu-id="dc3be-238">Para fazer isso, defina `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` para `false` ou 0.</span><span class="sxs-lookup"><span data-stu-id="dc3be-238">To do this, set the `DOTNET_SYSTEM_NET_HTTP_USESOCKETSHTTPHANDLER` to either `false` or 0.</span></span>

<span data-ttu-id="dc3be-239">No Windows, você também pode escolher usar <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, que depende de uma implementação nativa, ou a classe <xref:System.Net.Http.SocketsHttpHandler> transmitindo uma instância da classe para o construtor <xref:System.Net.Http.HttpClient>.</span><span class="sxs-lookup"><span data-stu-id="dc3be-239">On Windows, you can also choose to use <xref:System.Net.Http.WinHttpHandler?displayProperty=nameWithType>, which relies on a native implementation, or the <xref:System.Net.Http.SocketsHttpHandler> class by passing an instance of the class to the <xref:System.Net.Http.HttpClient> constructor.</span></span>

<span data-ttu-id="dc3be-240">No Linux e no macOS, só é possível configurar <xref:System.Net.Http.HttpClient> por processo.</span><span class="sxs-lookup"><span data-stu-id="dc3be-240">On Linux and macOS, you can only configure <xref:System.Net.Http.HttpClient> on a per-process basis.</span></span> <span data-ttu-id="dc3be-241">No Linux, você precisa implantar [libcurl](https://curl.haxx.se/libcurl/) se quiser usar a implementação <xref:System.Net.Http.HttpClient> antiga.</span><span class="sxs-lookup"><span data-stu-id="dc3be-241">On Linux, you need to deploy [libcurl](https://curl.haxx.se/libcurl/) if you want to use the old <xref:System.Net.Http.HttpClient> implementation.</span></span> <span data-ttu-id="dc3be-242">(Ele é instalado com .NET Core 2.0.)</span><span class="sxs-lookup"><span data-stu-id="dc3be-242">(It is installed with .NET Core 2.0.)</span></span>

## <a name="see-also"></a><span data-ttu-id="dc3be-243">Consulte também</span><span class="sxs-lookup"><span data-stu-id="dc3be-243">See also</span></span>

- [<span data-ttu-id="dc3be-244">Novidades do .NET Core</span><span class="sxs-lookup"><span data-stu-id="dc3be-244">What's new in .NET Core</span></span>](index.md)
- [<span data-ttu-id="dc3be-245">Novos recursos no EF Core 2.1</span><span class="sxs-lookup"><span data-stu-id="dc3be-245">New features in EF Core 2.1</span></span>](/ef/core/what-is-new/ef-core-2.1)
- [<span data-ttu-id="dc3be-246">Novidades do ASP.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="dc3be-246">What's new in ASP.NET Core 2.1</span></span>](/aspnet/core/aspnetcore-2.1)
