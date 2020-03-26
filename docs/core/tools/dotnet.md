---
title: Comando dotnet
description: Saiba mais sobre o comando dotnet (o driver genérico para o .NET Core CLI) e seu uso.
ms.date: 02/13/2020
ms.openlocfilehash: 8692d419afd528bf49e1dc7dc1a7a5fd698b363b
ms.sourcegitcommit: 07123a475af89b6da5bb6cc51ea40ab1e8a488f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80134073"
---
# <a name="dotnet-command"></a><span data-ttu-id="0fbda-103">Comando dotnet</span><span class="sxs-lookup"><span data-stu-id="0fbda-103">dotnet command</span></span>

<span data-ttu-id="0fbda-104">**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="0fbda-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="0fbda-105">Nome</span><span class="sxs-lookup"><span data-stu-id="0fbda-105">Name</span></span>

<span data-ttu-id="0fbda-106">`dotnet`- O driver genérico para o .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="0fbda-106">`dotnet` - The generic driver for the .NET Core CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0fbda-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="0fbda-107">Synopsis</span></span>

<span data-ttu-id="0fbda-108">Para obter informações sobre os comandos disponíveis e o ambiente:</span><span class="sxs-lookup"><span data-stu-id="0fbda-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

<span data-ttu-id="0fbda-109">Para executar um comando (requer instalação do SDK):</span><span class="sxs-lookup"><span data-stu-id="0fbda-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

<span data-ttu-id="0fbda-110">Para executar um aplicativo:</span><span class="sxs-lookup"><span data-stu-id="0fbda-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="0fbda-111">`--roll-forward`está disponível desde .NET Core 3.x.</span><span class="sxs-lookup"><span data-stu-id="0fbda-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="0fbda-112">Use `--roll-forward-on-no-candidate-fx` para .NET Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="0fbda-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="0fbda-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="0fbda-113">Description</span></span>

<span data-ttu-id="0fbda-114">O `dotnet` comando tem duas funções:</span><span class="sxs-lookup"><span data-stu-id="0fbda-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="0fbda-115">Ele fornece comandos para trabalhar com projetos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0fbda-115">It provides commands for working with .NET Core projects.</span></span>

  <span data-ttu-id="0fbda-116">Por exemplo, [`dotnet build`](dotnet-build.md) constrói um projeto.</span><span class="sxs-lookup"><span data-stu-id="0fbda-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="0fbda-117">Cada comando define suas próprias opções e argumentos.</span><span class="sxs-lookup"><span data-stu-id="0fbda-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="0fbda-118">Todos os comandos suportam a `--help` opção de imprimir breve documentação sobre como usar o comando.</span><span class="sxs-lookup"><span data-stu-id="0fbda-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="0fbda-119">Ele executa aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0fbda-119">It runs .NET Core applications.</span></span>

  <span data-ttu-id="0fbda-120">Você especifica o caminho `.dll` para um arquivo de aplicativo para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0fbda-120">You specify the path to an application `.dll` file to run the application.</span></span> <span data-ttu-id="0fbda-121">Por exemplo, `dotnet myapp.dll` `myapp` executa o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0fbda-121">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="0fbda-122">Consulte a [implantação do aplicativo .NET Core](../deploying/index.md) para saber sobre opções de implantação.</span><span class="sxs-lookup"><span data-stu-id="0fbda-122">See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="0fbda-123">Opções</span><span class="sxs-lookup"><span data-stu-id="0fbda-123">Options</span></span>

<span data-ttu-id="0fbda-124">Diferentes opções `dotnet` estão disponíveis para si só, para executar um comando e para executar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0fbda-124">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="0fbda-125">Opções para dotnet por si só</span><span class="sxs-lookup"><span data-stu-id="0fbda-125">Options for dotnet by itself</span></span>

<span data-ttu-id="0fbda-126">As seguintes `dotnet` opções são para si só.</span><span class="sxs-lookup"><span data-stu-id="0fbda-126">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="0fbda-127">Por exemplo, `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="0fbda-127">For example, `dotnet --info`.</span></span> <span data-ttu-id="0fbda-128">Eles imprimem informações sobre o meio ambiente.</span><span class="sxs-lookup"><span data-stu-id="0fbda-128">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="0fbda-129">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0fbda-129">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

- **`--version`**

  <span data-ttu-id="0fbda-130">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="0fbda-130">Prints out the version of the .NET Core SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="0fbda-131">Imprime uma lista dos tempos de execução do .NET Core instalados.</span><span class="sxs-lookup"><span data-stu-id="0fbda-131">Prints out a list of the installed .NET Core runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="0fbda-132">Imprime uma lista dos SDKs do Núcleo .NET instalados.</span><span class="sxs-lookup"><span data-stu-id="0fbda-132">Prints out a list of the installed .NET Core SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="0fbda-133">Imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0fbda-133">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="0fbda-134">Opções de SDK para executar um comando</span><span class="sxs-lookup"><span data-stu-id="0fbda-134">SDK options for running a command</span></span>

<span data-ttu-id="0fbda-135">As seguintes `dotnet` opções são para com um comando.</span><span class="sxs-lookup"><span data-stu-id="0fbda-135">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="0fbda-136">Por exemplo, `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="0fbda-136">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="0fbda-137">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="0fbda-137">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="0fbda-138">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="0fbda-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0fbda-139">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="0fbda-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="0fbda-140">Não suportado em todos os comandos.</span><span class="sxs-lookup"><span data-stu-id="0fbda-140">Not supported in every command.</span></span> <span data-ttu-id="0fbda-141">Consulte a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="0fbda-141">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="0fbda-142">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="0fbda-142">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="0fbda-143">Cada comando define opções específicas para esse comando.</span><span class="sxs-lookup"><span data-stu-id="0fbda-143">Each command defines options specific to that command.</span></span> <span data-ttu-id="0fbda-144">Consulte a página de comando específica para obter uma lista de opções disponíveis.</span><span class="sxs-lookup"><span data-stu-id="0fbda-144">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="0fbda-145">Opções de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="0fbda-145">Runtime options</span></span>

<span data-ttu-id="0fbda-146">As seguintes opções estão disponíveis quando `dotnet` executa um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0fbda-146">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="0fbda-147">Por exemplo, `dotnet myapp.dll --fx-version 3.1.1`.</span><span class="sxs-lookup"><span data-stu-id="0fbda-147">For example, `dotnet myapp.dll --fx-version 3.1.1`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="0fbda-148">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="0fbda-148">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="0fbda-149">Caminho para um arquivo *.deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="0fbda-149">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="0fbda-150">Um arquivo *deps.json* contém uma lista de dependências, dependências de compilação e informações de versão usadas para lidar com conflitos de montagem.</span><span class="sxs-lookup"><span data-stu-id="0fbda-150">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="0fbda-151">Para obter mais informações, confira [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="0fbda-151">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="0fbda-152">Versão do runtime do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0fbda-152">Version of the .NET Core runtime to use to run the application.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="0fbda-153">Caminho para um arquivo *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="0fbda-153">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="0fbda-154">Um arquivo *runtimeconfig.json* é um arquivo de configuração que contém configurações em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="0fbda-154">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="0fbda-155">Para obter mais informações, consulte [as configurações de configuração em tempo de execução do .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="0fbda-155">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="0fbda-156">**`--roll-forward-on-no-candidate-fx <N>`\*\*\*\*Disponível em .NET Core 2.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="0fbda-156">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="0fbda-157">Define o comportamento quando a estrutura compartilhada necessária não está disponível.</span><span class="sxs-lookup"><span data-stu-id="0fbda-157">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="0fbda-158">`N` pode ser:</span><span class="sxs-lookup"><span data-stu-id="0fbda-158">`N` can be:</span></span>

  - <span data-ttu-id="0fbda-159">`0` – Desabilitar até mesmo o roll forward da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="0fbda-159">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="0fbda-160">`1` – Efetuar roll forward da versão secundária, mas não da versão principal.</span><span class="sxs-lookup"><span data-stu-id="0fbda-160">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="0fbda-161">Esse é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="0fbda-161">This is the default behavior.</span></span>
  - <span data-ttu-id="0fbda-162">`2` – Efetuar roll forward das versões secundária e principal.</span><span class="sxs-lookup"><span data-stu-id="0fbda-162">`2` - Roll forward on minor and major versions.</span></span>

   <span data-ttu-id="0fbda-163">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="0fbda-163">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- <span data-ttu-id="0fbda-164">**`--roll-forward <SETTING>`\*\*\*\*Disponível a partir de .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="0fbda-164">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="0fbda-165">Controla como o roll forward é aplicado ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0fbda-165">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="0fbda-166">O `SETTING` pode ser um dos seguintes valores.</span><span class="sxs-lookup"><span data-stu-id="0fbda-166">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="0fbda-167">Se não for `Minor` especificado, é o padrão.</span><span class="sxs-lookup"><span data-stu-id="0fbda-167">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="0fbda-168">`LatestPatch`- Avance para a versão mais alta do patch.</span><span class="sxs-lookup"><span data-stu-id="0fbda-168">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="0fbda-169">Isso desabilita o roll forward da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="0fbda-169">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="0fbda-170">`Minor`- Encaminhe para a versão menor mais baixa, se a versão menor solicitada estiver faltando.</span><span class="sxs-lookup"><span data-stu-id="0fbda-170">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="0fbda-171">Se a versão secundária solicitada estiver presente, a política LatestPatch será usada.</span><span class="sxs-lookup"><span data-stu-id="0fbda-171">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="0fbda-172">`Major`- Avance para a versão principal mais baixa e a versão menor mais baixa, se a versão principal solicitada estiver faltando.</span><span class="sxs-lookup"><span data-stu-id="0fbda-172">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="0fbda-173">Se a versão principal solicitada está presente, a política Secundária é usada.</span><span class="sxs-lookup"><span data-stu-id="0fbda-173">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="0fbda-174">`LatestMinor`- Encaminhe para a versão menor mais alta, mesmo que a versão menor solicitada esteja presente.</span><span class="sxs-lookup"><span data-stu-id="0fbda-174">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="0fbda-175">Destinado a cenários de hospedagem de componente.</span><span class="sxs-lookup"><span data-stu-id="0fbda-175">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="0fbda-176">`LatestMajor`- Avance para a versão mais alta e menor, mesmo que o major solicitado esteja presente.</span><span class="sxs-lookup"><span data-stu-id="0fbda-176">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="0fbda-177">Destinado a cenários de hospedagem de componente.</span><span class="sxs-lookup"><span data-stu-id="0fbda-177">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="0fbda-178">`Disable`- Não role para a frente.</span><span class="sxs-lookup"><span data-stu-id="0fbda-178">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="0fbda-179">Associar somente à versão especificada.</span><span class="sxs-lookup"><span data-stu-id="0fbda-179">Only bind to specified version.</span></span> <span data-ttu-id="0fbda-180">Essa política não é recomendada para uso geral, pois ela desabilita a capacidade de efetuar roll forward para os patches mais recentes.</span><span class="sxs-lookup"><span data-stu-id="0fbda-180">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="0fbda-181">Esse valor só é recomendado para teste.</span><span class="sxs-lookup"><span data-stu-id="0fbda-181">This value is only recommended for testing.</span></span>

<span data-ttu-id="0fbda-182">Com exceção `Disable`de , todas as configurações usarão a versão de patch mais alta disponível.</span><span class="sxs-lookup"><span data-stu-id="0fbda-182">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

<span data-ttu-id="0fbda-183">O comportamento de encaminhamento também pode ser configurado em uma propriedade de arquivo de projeto, uma propriedade de arquivo de configuração em tempo de execução e uma variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="0fbda-183">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="0fbda-184">Para obter mais informações, consulte [o tempo de execução da versão principal para a frente](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="0fbda-184">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="0fbda-185">Comandos dotnet</span><span class="sxs-lookup"><span data-stu-id="0fbda-185">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="0fbda-186">Geral</span><span class="sxs-lookup"><span data-stu-id="0fbda-186">General</span></span>

| <span data-ttu-id="0fbda-187">Comando</span><span class="sxs-lookup"><span data-stu-id="0fbda-187">Command</span></span>                                       | <span data-ttu-id="0fbda-188">Função</span><span class="sxs-lookup"><span data-stu-id="0fbda-188">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="0fbda-189">dotnet build</span><span class="sxs-lookup"><span data-stu-id="0fbda-189">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="0fbda-190">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0fbda-190">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="0fbda-191">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="0fbda-191">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="0fbda-192">Interage com servidores iniciados por um build.</span><span class="sxs-lookup"><span data-stu-id="0fbda-192">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="0fbda-193">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="0fbda-193">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="0fbda-194">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="0fbda-194">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="0fbda-195">dotnet help</span><span class="sxs-lookup"><span data-stu-id="0fbda-195">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="0fbda-196">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="0fbda-196">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="0fbda-197">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="0fbda-197">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="0fbda-198">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0fbda-198">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="0fbda-199">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="0fbda-199">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="0fbda-200">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="0fbda-200">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="0fbda-201">dotnet new</span><span class="sxs-lookup"><span data-stu-id="0fbda-201">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="0fbda-202">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="0fbda-202">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="0fbda-203">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="0fbda-203">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="0fbda-204">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="0fbda-204">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="0fbda-205">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="0fbda-205">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="0fbda-206">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="0fbda-206">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="0fbda-207">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="0fbda-207">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="0fbda-208">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0fbda-208">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="0fbda-209">dotnet run</span><span class="sxs-lookup"><span data-stu-id="0fbda-209">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="0fbda-210">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="0fbda-210">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="0fbda-211">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="0fbda-211">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="0fbda-212">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="0fbda-212">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="0fbda-213">dotnet store</span><span class="sxs-lookup"><span data-stu-id="0fbda-213">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="0fbda-214">Armazena os assemblies no repositório de pacotes de runtime.</span><span class="sxs-lookup"><span data-stu-id="0fbda-214">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="0fbda-215">teste dotnet</span><span class="sxs-lookup"><span data-stu-id="0fbda-215">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="0fbda-216">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="0fbda-216">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="0fbda-217">Referências de projeto</span><span class="sxs-lookup"><span data-stu-id="0fbda-217">Project references</span></span>

<span data-ttu-id="0fbda-218">Comando</span><span class="sxs-lookup"><span data-stu-id="0fbda-218">Command</span></span> | <span data-ttu-id="0fbda-219">Função</span><span class="sxs-lookup"><span data-stu-id="0fbda-219">Function</span></span>
--- | ---
[<span data-ttu-id="0fbda-220">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="0fbda-220">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="0fbda-221">Adiciona uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="0fbda-221">Adds a project reference.</span></span>
[<span data-ttu-id="0fbda-222">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="0fbda-222">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="0fbda-223">Lista referências ao projeto.</span><span class="sxs-lookup"><span data-stu-id="0fbda-223">Lists project references.</span></span>
[<span data-ttu-id="0fbda-224">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="0fbda-224">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="0fbda-225">Remove uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="0fbda-225">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="0fbda-226">Pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="0fbda-226">NuGet packages</span></span>

<span data-ttu-id="0fbda-227">Comando</span><span class="sxs-lookup"><span data-stu-id="0fbda-227">Command</span></span> | <span data-ttu-id="0fbda-228">Função</span><span class="sxs-lookup"><span data-stu-id="0fbda-228">Function</span></span>
--- | ---
[<span data-ttu-id="0fbda-229">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="0fbda-229">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="0fbda-230">Adiciona um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="0fbda-230">Adds a NuGet package.</span></span>
[<span data-ttu-id="0fbda-231">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="0fbda-231">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="0fbda-232">Remove um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="0fbda-232">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="0fbda-233">Comandos NuGet</span><span class="sxs-lookup"><span data-stu-id="0fbda-233">NuGet commands</span></span>

<span data-ttu-id="0fbda-234">Comando</span><span class="sxs-lookup"><span data-stu-id="0fbda-234">Command</span></span> | <span data-ttu-id="0fbda-235">Função</span><span class="sxs-lookup"><span data-stu-id="0fbda-235">Function</span></span>
--- | ---
[<span data-ttu-id="0fbda-236">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="0fbda-236">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="0fbda-237">Exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="0fbda-237">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="0fbda-238">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="0fbda-238">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="0fbda-239">Envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="0fbda-239">Pushes a package to the server and publishes it.</span></span>
[<span data-ttu-id="0fbda-240">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="0fbda-240">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="0fbda-241">Limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.</span><span class="sxs-lookup"><span data-stu-id="0fbda-241">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="0fbda-242">dotnet nuget adicionar fonte</span><span class="sxs-lookup"><span data-stu-id="0fbda-242">dotnet nuget add source</span></span>](dotnet-nuget-add-source.md) | <span data-ttu-id="0fbda-243">Adiciona uma fonte NuGet.</span><span class="sxs-lookup"><span data-stu-id="0fbda-243">Adds a NuGet source.</span></span>
[<span data-ttu-id="0fbda-244">dotnet nuget desativar fonte</span><span class="sxs-lookup"><span data-stu-id="0fbda-244">dotnet nuget disable source</span></span>](dotnet-nuget-disable-source.md) | <span data-ttu-id="0fbda-245">Desativa uma fonte NuGet.</span><span class="sxs-lookup"><span data-stu-id="0fbda-245">Disables a NuGet source.</span></span>
[<span data-ttu-id="0fbda-246">dotnet nuget habilitar fonte</span><span class="sxs-lookup"><span data-stu-id="0fbda-246">dotnet nuget enable source</span></span>](dotnet-nuget-enable-source.md) | <span data-ttu-id="0fbda-247">Habilita uma fonte NuGet.</span><span class="sxs-lookup"><span data-stu-id="0fbda-247">Enables a NuGet source.</span></span>
[<span data-ttu-id="0fbda-248">dotnet nuget fonte de lista</span><span class="sxs-lookup"><span data-stu-id="0fbda-248">dotnet nuget list source</span></span>](dotnet-nuget-list-source.md) | <span data-ttu-id="0fbda-249">Lista todas as fontes NuGet configuradas.</span><span class="sxs-lookup"><span data-stu-id="0fbda-249">Lists all configured NuGet sources.</span></span>
[<span data-ttu-id="0fbda-250">dotnet nuget remover fonte</span><span class="sxs-lookup"><span data-stu-id="0fbda-250">dotnet nuget remove source</span></span>](dotnet-nuget-remove-source.md) | <span data-ttu-id="0fbda-251">Remove uma fonte NuGet.</span><span class="sxs-lookup"><span data-stu-id="0fbda-251">Removes a NuGet source.</span></span>
[<span data-ttu-id="0fbda-252">dotnet nuget fonte de atualização</span><span class="sxs-lookup"><span data-stu-id="0fbda-252">dotnet nuget update source</span></span>](dotnet-nuget-update-source.md) | <span data-ttu-id="0fbda-253">Atualiza uma fonte NuGet.</span><span class="sxs-lookup"><span data-stu-id="0fbda-253">Updates a NuGet source.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="0fbda-254">Comandos de ferramentas globais, de caminho de ferramentas e locais</span><span class="sxs-lookup"><span data-stu-id="0fbda-254">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="0fbda-255">As ferramentas são aplicativos de console que são instalados a partir de pacotes NuGet e são invocados a partir do prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="0fbda-255">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="0fbda-256">Você mesmo pode escrever ferramentas ou instalar ferramentas escritas por terceiros.</span><span class="sxs-lookup"><span data-stu-id="0fbda-256">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="0fbda-257">As ferramentas também são conhecidas como ferramentas globais, ferramentas de caminho de ferramentas e ferramentas locais.</span><span class="sxs-lookup"><span data-stu-id="0fbda-257">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="0fbda-258">Para obter mais informações, consulte [a visão geral das ferramentas .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="0fbda-258">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="0fbda-259">Ferramentas globais e de caminho de ferramentas estão disponíveis a partir do .NET Core SDK 2.1.</span><span class="sxs-lookup"><span data-stu-id="0fbda-259">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="0fbda-260">As ferramentas locais estão disponíveis a partir do .NET Core SDK 3.0.</span><span class="sxs-lookup"><span data-stu-id="0fbda-260">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="0fbda-261">Comando</span><span class="sxs-lookup"><span data-stu-id="0fbda-261">Command</span></span> | <span data-ttu-id="0fbda-262">Função</span><span class="sxs-lookup"><span data-stu-id="0fbda-262">Function</span></span>
--- | ---
[<span data-ttu-id="0fbda-263">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="0fbda-263">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="0fbda-264">Instala uma ferramenta em sua máquina.</span><span class="sxs-lookup"><span data-stu-id="0fbda-264">Installs a tool on your machine.</span></span>
[<span data-ttu-id="0fbda-265">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="0fbda-265">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="0fbda-266">Lista todas as ferramentas globais, de caminho de ferramentas ou locais atualmente instaladas em sua máquina.</span><span class="sxs-lookup"><span data-stu-id="0fbda-266">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="0fbda-267">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="0fbda-267">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="0fbda-268">Desinstala uma ferramenta da sua máquina.</span><span class="sxs-lookup"><span data-stu-id="0fbda-268">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="0fbda-269">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="0fbda-269">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="0fbda-270">Atualiza uma ferramenta instalada em sua máquina.</span><span class="sxs-lookup"><span data-stu-id="0fbda-270">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="0fbda-271">Ferramentas adicionais</span><span class="sxs-lookup"><span data-stu-id="0fbda-271">Additional tools</span></span>

<span data-ttu-id="0fbda-272">A partir do SDK do .NET Core 2.1.300, várias ferramentas que estavam disponíveis apenas por projeto usando `DotnetCliToolReference` agora estão disponíveis como parte do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0fbda-272">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="0fbda-273">Essas ferramentas estão listadas na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="0fbda-273">These tools are listed in the following table:</span></span>

| <span data-ttu-id="0fbda-274">Ferramenta</span><span class="sxs-lookup"><span data-stu-id="0fbda-274">Tool</span></span>                                              | <span data-ttu-id="0fbda-275">Função</span><span class="sxs-lookup"><span data-stu-id="0fbda-275">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="0fbda-276">dev-certs</span><span class="sxs-lookup"><span data-stu-id="0fbda-276">dev-certs</span></span>                                         | <span data-ttu-id="0fbda-277">Cria e gerencia certificados de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="0fbda-277">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="0fbda-278">Ef</span><span class="sxs-lookup"><span data-stu-id="0fbda-278">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="0fbda-279">Ferramentas de linha de comando do Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="0fbda-279">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="0fbda-280">sql-cache</span><span class="sxs-lookup"><span data-stu-id="0fbda-280">sql-cache</span></span>                                         | <span data-ttu-id="0fbda-281">Ferramentas de linha de comando de cache do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="0fbda-281">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="0fbda-282">user-secrets</span><span class="sxs-lookup"><span data-stu-id="0fbda-282">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="0fbda-283">Gerencia os segredos do usuário de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="0fbda-283">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="0fbda-284">Assistir</span><span class="sxs-lookup"><span data-stu-id="0fbda-284">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="0fbda-285">Inicia um observador de arquivo que executa um comando quando os arquivos são alterados.</span><span class="sxs-lookup"><span data-stu-id="0fbda-285">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="0fbda-286">Para obter mais informações sobre cada ferramenta, digite `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="0fbda-286">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="0fbda-287">Exemplos</span><span class="sxs-lookup"><span data-stu-id="0fbda-287">Examples</span></span>

<span data-ttu-id="0fbda-288">Crie um novo aplicativo de console .NET Core:</span><span class="sxs-lookup"><span data-stu-id="0fbda-288">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="0fbda-289">Compile um projeto e suas dependências em um determinado diretório:</span><span class="sxs-lookup"><span data-stu-id="0fbda-289">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="0fbda-290">Execute um aplicativo:</span><span class="sxs-lookup"><span data-stu-id="0fbda-290">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="0fbda-291">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="0fbda-291">Environment variables</span></span>

- <span data-ttu-id="0fbda-292">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="0fbda-292">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="0fbda-293">Especifica a localização dos tempos de execução do .NET Core, se eles não estiverem instalados no local padrão.</span><span class="sxs-lookup"><span data-stu-id="0fbda-293">Specifies the location of the .NET Core runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="0fbda-294">O local padrão `C:\Program Files\dotnet`no Windows é .</span><span class="sxs-lookup"><span data-stu-id="0fbda-294">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="0fbda-295">A localização padrão no Linux `/usr/share/dotnet`e macOS é .</span><span class="sxs-lookup"><span data-stu-id="0fbda-295">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="0fbda-296">Essa variável de ambiente é usada apenas ao executar aplicativos através de executáveis gerados (apphosts).</span><span class="sxs-lookup"><span data-stu-id="0fbda-296">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="0fbda-297">`DOTNET_ROOT(x86)`é usado em vez disso ao executar um executável de 32 bits em um sistema operacional de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="0fbda-297">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `DOTNET_PACKAGES`

  <span data-ttu-id="0fbda-298">A pasta de pacotes globais.</span><span class="sxs-lookup"><span data-stu-id="0fbda-298">The global packages folder.</span></span> <span data-ttu-id="0fbda-299">Se não estiver definido, o padrão será `~/.nuget/packages` em Unix ou `%userprofile%\.nuget\packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="0fbda-299">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="0fbda-300">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o runtime.</span><span class="sxs-lookup"><span data-stu-id="0fbda-300">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_NOLOGO`

  <span data-ttu-id="0fbda-301">Especifica se as mensagens de boas-vindas e telemetria do .NET Core são exibidas na primeira execução.</span><span class="sxs-lookup"><span data-stu-id="0fbda-301">Specifies whether .NET Core welcome and telemetry messages are displayed on first run.</span></span> <span data-ttu-id="0fbda-302">Definir `true` para silenciar essas mensagens `true` `1` `yes` (valores , ou `false` aceitos) `false` `0`ou `no` definido para permitir (valores , ou aceitos).</span><span class="sxs-lookup"><span data-stu-id="0fbda-302">Set to `true` to mute these messages (values `true`, `1`, or `yes` accepted) or set to `false` to allow (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="0fbda-303">Se não estiver definido, o padrão é `false` e as mensagens serão exibidas na primeira execução.</span><span class="sxs-lookup"><span data-stu-id="0fbda-303">If not set, the default is `false` and the messages will be displayed on first run.</span></span> <span data-ttu-id="0fbda-304">Observe que esta bandeira não tem efeito `DOTNET_CLI_TELEMETRY_OPTOUT` na telemetria (veja para optar por não enviar telemetria).</span><span class="sxs-lookup"><span data-stu-id="0fbda-304">Note that this flag has no effect on telemetry (see `DOTNET_CLI_TELEMETRY_OPTOUT` for opting out of sending telemetry).</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="0fbda-305">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="0fbda-305">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="0fbda-306">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="0fbda-306">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="0fbda-307">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="0fbda-307">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="0fbda-308">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="0fbda-308">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="0fbda-309">Especifica se o runtime, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global.</span><span class="sxs-lookup"><span data-stu-id="0fbda-309">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="0fbda-310">Se não for definido, ele `true`é padrão para 1 (lógico ).</span><span class="sxs-lookup"><span data-stu-id="0fbda-310">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="0fbda-311">Definir como 0 `false`(lógico ) para não resolver a partir do local global e ter instalações isoladas .NET Core.</span><span class="sxs-lookup"><span data-stu-id="0fbda-311">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET Core installations.</span></span> <span data-ttu-id="0fbda-312">Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="0fbda-312">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="0fbda-313">`DOTNET_ROLL_FORWARD`**Disponível a partir de .NET Core 3.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="0fbda-313">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x SDK.**</span></span>

  <span data-ttu-id="0fbda-314">Determina o comportamento de rolagem para a frente.</span><span class="sxs-lookup"><span data-stu-id="0fbda-314">Determines roll forward behavior.</span></span> <span data-ttu-id="0fbda-315">Para obter mais `--roll-forward` informações, consulte a opção no início deste artigo.</span><span class="sxs-lookup"><span data-stu-id="0fbda-315">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="0fbda-316">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**Disponível em .NET Core 2.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="0fbda-316">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="0fbda-317">Desabilita o roll forward da versão secundária, se definido como `0`.</span><span class="sxs-lookup"><span data-stu-id="0fbda-317">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="0fbda-318">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="0fbda-318">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="0fbda-319">Define a linguagem da IU CLI usando `en-us`um valor local, como .</span><span class="sxs-lookup"><span data-stu-id="0fbda-319">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="0fbda-320">Os valores suportados são os mesmos do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="0fbda-320">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="0fbda-321">Para obter mais informações, consulte a seção sobre a alteração do idioma do instalador na [documentação](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019)de instalação do Visual Studio .</span><span class="sxs-lookup"><span data-stu-id="0fbda-321">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span></span> <span data-ttu-id="0fbda-322">As regras do gerenciador de recursos .NET se aplicam,&mdash;para que você não `CultureInfo` tenha que escolher uma correspondência exata, você também pode escolher descendentes na árvore.</span><span class="sxs-lookup"><span data-stu-id="0fbda-322">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="0fbda-323">Por exemplo, se você `fr-CA`defini-lo para , `fr` o CLI encontrará e usará as traduções.</span><span class="sxs-lookup"><span data-stu-id="0fbda-323">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="0fbda-324">Se você defini-lo para um idioma que não é suportado, o CLI volta para o inglês.</span><span class="sxs-lookup"><span data-stu-id="0fbda-324">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="0fbda-325">Para executáveis gerados habilitados por GUI - desativa o popup de diálogo, que normalmente é mostrada para determinadas classes de erros.</span><span class="sxs-lookup"><span data-stu-id="0fbda-325">For GUI-enabled generated executables - disables dialog popup, which normally shows for certain classes of errors.</span></span> <span data-ttu-id="0fbda-326">Ele só `stderr` escreve e sai nesses casos.</span><span class="sxs-lookup"><span data-stu-id="0fbda-326">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="0fbda-327">Equivalente à `--additional-deps`opção CLI .</span><span class="sxs-lookup"><span data-stu-id="0fbda-327">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="0fbda-328">Substitui o RID detectado.</span><span class="sxs-lookup"><span data-stu-id="0fbda-328">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="0fbda-329">A localização da "loja compartilhada" que a resolução do conjunto recua em alguns casos.</span><span class="sxs-lookup"><span data-stu-id="0fbda-329">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="0fbda-330">Lista de montagens para carregar e executar ganchos de inicialização.</span><span class="sxs-lookup"><span data-stu-id="0fbda-330">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="0fbda-331">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="0fbda-331">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="0fbda-332">Controla o rastreamento de diagnósticos dos `dotnet.exe`componentes de hospedagem, tais como , `hostfxr`e `hostpolicy`.</span><span class="sxs-lookup"><span data-stu-id="0fbda-332">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

## <a name="see-also"></a><span data-ttu-id="0fbda-333">Confira também</span><span class="sxs-lookup"><span data-stu-id="0fbda-333">See also</span></span>

- [<span data-ttu-id="0fbda-334">Arquivos de configuração de runtime</span><span class="sxs-lookup"><span data-stu-id="0fbda-334">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="0fbda-335">Configurações de configuração de tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="0fbda-335">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
