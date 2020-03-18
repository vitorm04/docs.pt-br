---
title: Comando dotnet
description: Saiba mais sobre o comando dotnet (o driver genérico para o .NET Core CLI) e seu uso.
ms.date: 02/13/2020
ms.openlocfilehash: da37c5cc3b019851e245fa3f65ae9dfb8a3fef54
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "79398891"
---
# <a name="dotnet-command"></a><span data-ttu-id="ae63a-103">Comando dotnet</span><span class="sxs-lookup"><span data-stu-id="ae63a-103">dotnet command</span></span>

<span data-ttu-id="ae63a-104">**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="ae63a-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="ae63a-105">Nome</span><span class="sxs-lookup"><span data-stu-id="ae63a-105">Name</span></span>

<span data-ttu-id="ae63a-106">`dotnet`- O driver genérico para o .NET Core CLI.</span><span class="sxs-lookup"><span data-stu-id="ae63a-106">`dotnet` - The generic driver for the .NET Core CLI.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ae63a-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="ae63a-107">Synopsis</span></span>

<span data-ttu-id="ae63a-108">Para obter informações sobre os comandos disponíveis e o ambiente:</span><span class="sxs-lookup"><span data-stu-id="ae63a-108">To get information about the available commands and the environment:</span></span>

```dotnetcli
dotnet [-h|--help] [--version] [--info]
    [--list-runtimes] [--list-sdks]
```

<span data-ttu-id="ae63a-109">Para executar um comando (requer instalação do SDK):</span><span class="sxs-lookup"><span data-stu-id="ae63a-109">To run a command (requires SDK installation):</span></span>

```dotnetcli
dotnet <COMMAND> [-d|--diagnostics] [-h|--help] [--verbosity]
    [command-options] [arguments]
```

<span data-ttu-id="ae63a-110">Para executar um aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ae63a-110">To run an application:</span></span>

```dotnetcli
dotnet [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]

dotnet exec [--additionalprobingpath] [--additional-deps]
    [--fx-version]  [--roll-forward]
    <PATH_TO_APPLICATION> [arguments]
```

<span data-ttu-id="ae63a-111">`--roll-forward`está disponível desde .NET Core 3.x.</span><span class="sxs-lookup"><span data-stu-id="ae63a-111">`--roll-forward` is available since .NET Core 3.x.</span></span> <span data-ttu-id="ae63a-112">Use `--roll-forward-on-no-candidate-fx` para .NET Core 2.x.</span><span class="sxs-lookup"><span data-stu-id="ae63a-112">Use `--roll-forward-on-no-candidate-fx` for .NET Core 2.x.</span></span>

## <a name="description"></a><span data-ttu-id="ae63a-113">Descrição</span><span class="sxs-lookup"><span data-stu-id="ae63a-113">Description</span></span>

<span data-ttu-id="ae63a-114">O `dotnet` comando tem duas funções:</span><span class="sxs-lookup"><span data-stu-id="ae63a-114">The `dotnet` command has two functions:</span></span>

- <span data-ttu-id="ae63a-115">Ele fornece comandos para trabalhar com projetos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ae63a-115">It provides commands for working with .NET Core projects.</span></span>

  <span data-ttu-id="ae63a-116">Por exemplo, [`dotnet build`](dotnet-build.md) constrói um projeto.</span><span class="sxs-lookup"><span data-stu-id="ae63a-116">For example, [`dotnet build`](dotnet-build.md) builds a project.</span></span> <span data-ttu-id="ae63a-117">Cada comando define suas próprias opções e argumentos.</span><span class="sxs-lookup"><span data-stu-id="ae63a-117">Each command defines its own options and arguments.</span></span> <span data-ttu-id="ae63a-118">Todos os comandos suportam a `--help` opção de imprimir breve documentação sobre como usar o comando.</span><span class="sxs-lookup"><span data-stu-id="ae63a-118">All commands support the `--help` option for printing out brief documentation about how to use the command.</span></span>

- <span data-ttu-id="ae63a-119">Ele executa aplicativos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ae63a-119">It runs .NET Core applications.</span></span>

  <span data-ttu-id="ae63a-120">Você especifica o caminho `.dll` para um arquivo de aplicativo para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ae63a-120">You specify the path to an application `.dll` file to run the application.</span></span> <span data-ttu-id="ae63a-121">Por exemplo, `dotnet myapp.dll` `myapp` executa o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ae63a-121">For example, `dotnet myapp.dll` runs the `myapp` application.</span></span> <span data-ttu-id="ae63a-122">Consulte a [implantação do aplicativo .NET Core](../deploying/index.md) para saber sobre opções de implantação.</span><span class="sxs-lookup"><span data-stu-id="ae63a-122">See [.NET Core application deployment](../deploying/index.md) to learn about deployment options.</span></span>

## <a name="options"></a><span data-ttu-id="ae63a-123">Opções</span><span class="sxs-lookup"><span data-stu-id="ae63a-123">Options</span></span>

<span data-ttu-id="ae63a-124">Diferentes opções `dotnet` estão disponíveis para si só, para executar um comando e para executar um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ae63a-124">Different options are available for `dotnet` by itself, for running a command, and for running an application.</span></span>

### <a name="options-for-dotnet-by-itself"></a><span data-ttu-id="ae63a-125">Opções para dotnet por si só</span><span class="sxs-lookup"><span data-stu-id="ae63a-125">Options for dotnet by itself</span></span>

<span data-ttu-id="ae63a-126">As seguintes `dotnet` opções são para si só.</span><span class="sxs-lookup"><span data-stu-id="ae63a-126">The following options are for `dotnet` by itself.</span></span> <span data-ttu-id="ae63a-127">Por exemplo, `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="ae63a-127">For example, `dotnet --info`.</span></span> <span data-ttu-id="ae63a-128">Eles imprimem informações sobre o meio ambiente.</span><span class="sxs-lookup"><span data-stu-id="ae63a-128">They print out information about the environment.</span></span>

- **`--info`**

  <span data-ttu-id="ae63a-129">Imprime informações detalhadas sobre uma instalação do .NET Core e o ambiente do computador, como o sistema operacional atual, e o SHA da confirmação da versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ae63a-129">Prints out detailed information about a .NET Core installation and the machine environment, such as the current operating system, and commit SHA of the .NET Core version.</span></span>

- **`--version`**

  <span data-ttu-id="ae63a-130">Imprime a versão do SDK do .NET Core em uso.</span><span class="sxs-lookup"><span data-stu-id="ae63a-130">Prints out the version of the .NET Core SDK in use.</span></span>

- **`--list-runtimes`**

  <span data-ttu-id="ae63a-131">Imprime uma lista dos tempos de execução do .NET Core instalados.</span><span class="sxs-lookup"><span data-stu-id="ae63a-131">Prints out a list of the installed .NET Core runtimes.</span></span>

- **`--list-sdks`**

  <span data-ttu-id="ae63a-132">Imprime uma lista dos SDKs do Núcleo .NET instalados.</span><span class="sxs-lookup"><span data-stu-id="ae63a-132">Prints out a list of the installed .NET Core SDKs.</span></span>

- **`-h|--help`**

  <span data-ttu-id="ae63a-133">Imprime uma lista de comandos disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ae63a-133">Prints out a list of available commands.</span></span>

### <a name="sdk-options-for-running-a-command"></a><span data-ttu-id="ae63a-134">Opções de SDK para executar um comando</span><span class="sxs-lookup"><span data-stu-id="ae63a-134">SDK options for running a command</span></span>

<span data-ttu-id="ae63a-135">As seguintes `dotnet` opções são para com um comando.</span><span class="sxs-lookup"><span data-stu-id="ae63a-135">The following options are for `dotnet` with a command.</span></span> <span data-ttu-id="ae63a-136">Por exemplo, `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="ae63a-136">For example, `dotnet build --help`.</span></span>

- **`-d|--diagnostics`**

  <span data-ttu-id="ae63a-137">Habilita a saída de diagnóstico.</span><span class="sxs-lookup"><span data-stu-id="ae63a-137">Enables diagnostic output.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="ae63a-138">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="ae63a-138">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ae63a-139">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ae63a-139">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="ae63a-140">Não suportado em todos os comandos.</span><span class="sxs-lookup"><span data-stu-id="ae63a-140">Not supported in every command.</span></span> <span data-ttu-id="ae63a-141">Consulte a página de comando específica para determinar se essa opção está disponível.</span><span class="sxs-lookup"><span data-stu-id="ae63a-141">See specific command page to determine if this option is available.</span></span>

- **`-h|--help`**

  <span data-ttu-id="ae63a-142">Imprime a documentação para um determinado comando, como `dotnet build --help`.</span><span class="sxs-lookup"><span data-stu-id="ae63a-142">Prints out documentation for a given command, such as `dotnet build --help`.</span></span>

- **`command options`**

  <span data-ttu-id="ae63a-143">Cada comando define opções específicas para esse comando.</span><span class="sxs-lookup"><span data-stu-id="ae63a-143">Each command defines options specific to that command.</span></span> <span data-ttu-id="ae63a-144">Consulte a página de comando específica para obter uma lista de opções disponíveis.</span><span class="sxs-lookup"><span data-stu-id="ae63a-144">See specific command page for a list of available options.</span></span>

### <a name="runtime-options"></a><span data-ttu-id="ae63a-145">Opções de tempo de execução</span><span class="sxs-lookup"><span data-stu-id="ae63a-145">Runtime options</span></span>

<span data-ttu-id="ae63a-146">As seguintes opções estão disponíveis quando `dotnet` executa um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ae63a-146">The following options are available when `dotnet` runs an application.</span></span> <span data-ttu-id="ae63a-147">Por exemplo, `dotnet myapp.dll --fx-version 3.1.1`.</span><span class="sxs-lookup"><span data-stu-id="ae63a-147">For example, `dotnet myapp.dll --fx-version 3.1.1`.</span></span>

- **`--additionalprobingpath <PATH>`**

  <span data-ttu-id="ae63a-148">Caminho que contém a política de investigação e os assemblies a serem investigados.</span><span class="sxs-lookup"><span data-stu-id="ae63a-148">Path containing probing policy and assemblies to probe.</span></span>

- **`--additional-deps <PATH>`**

  <span data-ttu-id="ae63a-149">Caminho para um arquivo *.deps.json* adicional.</span><span class="sxs-lookup"><span data-stu-id="ae63a-149">Path to an additional *.deps.json* file.</span></span> <span data-ttu-id="ae63a-150">Um arquivo *deps.json* contém uma lista de dependências, dependências de compilação e informações de versão usadas para lidar com conflitos de montagem.</span><span class="sxs-lookup"><span data-stu-id="ae63a-150">A *deps.json* file contains a list of dependencies, compilation dependencies, and version information used to address assembly conflicts.</span></span> <span data-ttu-id="ae63a-151">Para obter mais informações, confira [Arquivos de configuração de runtime](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) no GitHub.</span><span class="sxs-lookup"><span data-stu-id="ae63a-151">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md) on GitHub.</span></span>

- **`--fx-version <VERSION>`**

  <span data-ttu-id="ae63a-152">Versão do runtime do .NET Core a ser usada para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ae63a-152">Version of the .NET Core runtime to use to run the application.</span></span>

- **`--runtimeconfig`**

  <span data-ttu-id="ae63a-153">Caminho para um arquivo *runtimeconfig.json*.</span><span class="sxs-lookup"><span data-stu-id="ae63a-153">Path to a *runtimeconfig.json* file.</span></span> <span data-ttu-id="ae63a-154">Um arquivo *runtimeconfig.json* é um arquivo de configuração que contém configurações em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="ae63a-154">A *runtimeconfig.json* file is a configuration file that contains run-time settings.</span></span> <span data-ttu-id="ae63a-155">Para obter mais informações, consulte [as configurações de configuração em tempo de execução do .NET Core](../run-time-config/index.md#runtimeconfigjson).</span><span class="sxs-lookup"><span data-stu-id="ae63a-155">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

- <span data-ttu-id="ae63a-156">**`--roll-forward-on-no-candidate-fx <N>`\*\*\*\*Disponível em .NET Core 2.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="ae63a-156">**`--roll-forward-on-no-candidate-fx <N>`** **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="ae63a-157">Define o comportamento quando a estrutura compartilhada necessária não está disponível.</span><span class="sxs-lookup"><span data-stu-id="ae63a-157">Defines behavior when the required shared framework is not available.</span></span> <span data-ttu-id="ae63a-158">`N` pode ser:</span><span class="sxs-lookup"><span data-stu-id="ae63a-158">`N` can be:</span></span>

  - <span data-ttu-id="ae63a-159">`0` – Desabilitar até mesmo o roll forward da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="ae63a-159">`0` - Disable even minor version roll forward.</span></span>
  - <span data-ttu-id="ae63a-160">`1` – Efetuar roll forward da versão secundária, mas não da versão principal.</span><span class="sxs-lookup"><span data-stu-id="ae63a-160">`1` - Roll forward on minor version, but not on major version.</span></span> <span data-ttu-id="ae63a-161">Esse é o comportamento padrão.</span><span class="sxs-lookup"><span data-stu-id="ae63a-161">This is the default behavior.</span></span>
  - <span data-ttu-id="ae63a-162">`2` – Efetuar roll forward das versões secundária e principal.</span><span class="sxs-lookup"><span data-stu-id="ae63a-162">`2` - Roll forward on minor and major versions.</span></span>

   <span data-ttu-id="ae63a-163">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="ae63a-163">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- <span data-ttu-id="ae63a-164">**`--roll-forward <SETTING>`\*\*\*\*Disponível a partir de .NET Core SDK 3.0.**</span><span class="sxs-lookup"><span data-stu-id="ae63a-164">**`--roll-forward <SETTING>`** **Available starting with .NET Core SDK 3.0.**</span></span>

  <span data-ttu-id="ae63a-165">Controla como o roll forward é aplicado ao aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ae63a-165">Controls how roll forward is applied to the app.</span></span> <span data-ttu-id="ae63a-166">O `SETTING` pode ser um dos seguintes valores.</span><span class="sxs-lookup"><span data-stu-id="ae63a-166">The `SETTING` can be one of the following values.</span></span> <span data-ttu-id="ae63a-167">Se não for `Minor` especificado, é o padrão.</span><span class="sxs-lookup"><span data-stu-id="ae63a-167">If not specified, `Minor` is the default.</span></span>

  - <span data-ttu-id="ae63a-168">`LatestPatch`- Avance para a versão mais alta do patch.</span><span class="sxs-lookup"><span data-stu-id="ae63a-168">`LatestPatch` - Roll forward to the highest patch version.</span></span> <span data-ttu-id="ae63a-169">Isso desabilita o roll forward da versão secundária.</span><span class="sxs-lookup"><span data-stu-id="ae63a-169">This disables minor version roll forward.</span></span>
  - <span data-ttu-id="ae63a-170">`Minor`- Encaminhe para a versão menor mais baixa, se a versão menor solicitada estiver faltando.</span><span class="sxs-lookup"><span data-stu-id="ae63a-170">`Minor` - Roll forward to the lowest higher minor version, if requested minor version is missing.</span></span> <span data-ttu-id="ae63a-171">Se a versão secundária solicitada estiver presente, a política LatestPatch será usada.</span><span class="sxs-lookup"><span data-stu-id="ae63a-171">If the requested minor version is present, then the LatestPatch policy is used.</span></span>
  - <span data-ttu-id="ae63a-172">`Major`- Avance para a versão principal mais baixa e a versão menor mais baixa, se a versão principal solicitada estiver faltando.</span><span class="sxs-lookup"><span data-stu-id="ae63a-172">`Major` - Roll forward to lowest higher major version, and lowest minor version, if requested major version is missing.</span></span> <span data-ttu-id="ae63a-173">Se a versão principal solicitada está presente, a política Secundária é usada.</span><span class="sxs-lookup"><span data-stu-id="ae63a-173">If the requested major version is present, then the Minor policy is used.</span></span>
  - <span data-ttu-id="ae63a-174">`LatestMinor`- Encaminhe para a versão menor mais alta, mesmo que a versão menor solicitada esteja presente.</span><span class="sxs-lookup"><span data-stu-id="ae63a-174">`LatestMinor` - Roll forward to highest minor version, even if requested minor version is present.</span></span> <span data-ttu-id="ae63a-175">Destinado a cenários de hospedagem de componente.</span><span class="sxs-lookup"><span data-stu-id="ae63a-175">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="ae63a-176">`LatestMajor`- Avance para a versão mais alta e menor, mesmo que o major solicitado esteja presente.</span><span class="sxs-lookup"><span data-stu-id="ae63a-176">`LatestMajor` - Roll forward to highest major and highest minor version, even if requested major is present.</span></span> <span data-ttu-id="ae63a-177">Destinado a cenários de hospedagem de componente.</span><span class="sxs-lookup"><span data-stu-id="ae63a-177">Intended for component hosting scenarios.</span></span>
  - <span data-ttu-id="ae63a-178">`Disable`- Não role para a frente.</span><span class="sxs-lookup"><span data-stu-id="ae63a-178">`Disable` - Don't roll forward.</span></span> <span data-ttu-id="ae63a-179">Associar somente à versão especificada.</span><span class="sxs-lookup"><span data-stu-id="ae63a-179">Only bind to specified version.</span></span> <span data-ttu-id="ae63a-180">Essa política não é recomendada para uso geral, pois ela desabilita a capacidade de efetuar roll forward para os patches mais recentes.</span><span class="sxs-lookup"><span data-stu-id="ae63a-180">This policy isn't recommended for general use because it disables the ability to roll forward to the latest patches.</span></span> <span data-ttu-id="ae63a-181">Esse valor só é recomendado para teste.</span><span class="sxs-lookup"><span data-stu-id="ae63a-181">This value is only recommended for testing.</span></span>

<span data-ttu-id="ae63a-182">Com exceção `Disable`de , todas as configurações usarão a versão de patch mais alta disponível.</span><span class="sxs-lookup"><span data-stu-id="ae63a-182">With the exception of `Disable`, all settings will use the highest available patch version.</span></span>

<span data-ttu-id="ae63a-183">O comportamento de encaminhamento também pode ser configurado em uma propriedade de arquivo de projeto, uma propriedade de arquivo de configuração em tempo de execução e uma variável de ambiente.</span><span class="sxs-lookup"><span data-stu-id="ae63a-183">Roll forward behavior can also be configured in a project file property, a run-time configuration file property, and an environment variable.</span></span> <span data-ttu-id="ae63a-184">Para obter mais informações, consulte [o tempo de execução da versão principal para a frente](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span><span class="sxs-lookup"><span data-stu-id="ae63a-184">For more information, see [Major-version runtime roll forward](../whats-new/dotnet-core-3-0.md#major-version-runtime-roll-forward).</span></span>

## <a name="dotnet-commands"></a><span data-ttu-id="ae63a-185">Comandos dotnet</span><span class="sxs-lookup"><span data-stu-id="ae63a-185">dotnet commands</span></span>

### <a name="general"></a><span data-ttu-id="ae63a-186">Geral</span><span class="sxs-lookup"><span data-stu-id="ae63a-186">General</span></span>

| <span data-ttu-id="ae63a-187">Comando</span><span class="sxs-lookup"><span data-stu-id="ae63a-187">Command</span></span>                                       | <span data-ttu-id="ae63a-188">Função</span><span class="sxs-lookup"><span data-stu-id="ae63a-188">Function</span></span>                                                            |
| --------------------------------------------- | ------------------------------------------------------------------- |
| [<span data-ttu-id="ae63a-189">dotnet build</span><span class="sxs-lookup"><span data-stu-id="ae63a-189">dotnet build</span></span>](dotnet-build.md)               | <span data-ttu-id="ae63a-190">Compila um aplicativo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ae63a-190">Builds a .NET Core application.</span></span>                                     |
| [<span data-ttu-id="ae63a-191">dotnet build-server</span><span class="sxs-lookup"><span data-stu-id="ae63a-191">dotnet build-server</span></span>](dotnet-build-server.md) | <span data-ttu-id="ae63a-192">Interage com servidores iniciados por um build.</span><span class="sxs-lookup"><span data-stu-id="ae63a-192">Interacts with servers started by a build.</span></span>                          |
| [<span data-ttu-id="ae63a-193">dotnet clean</span><span class="sxs-lookup"><span data-stu-id="ae63a-193">dotnet clean</span></span>](dotnet-clean.md)               | <span data-ttu-id="ae63a-194">Limpa saídas de build.</span><span class="sxs-lookup"><span data-stu-id="ae63a-194">Clean build outputs.</span></span>                                                |
| [<span data-ttu-id="ae63a-195">dotnet help</span><span class="sxs-lookup"><span data-stu-id="ae63a-195">dotnet help</span></span>](dotnet-help.md)                 | <span data-ttu-id="ae63a-196">Mostra uma documentação mais detalhada online para o comando.</span><span class="sxs-lookup"><span data-stu-id="ae63a-196">Shows more detailed documentation online for the command.</span></span>           |
| [<span data-ttu-id="ae63a-197">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="ae63a-197">dotnet migrate</span></span>](dotnet-migrate.md)           | <span data-ttu-id="ae63a-198">Migra um projeto válido da Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ae63a-198">Migrates a valid Preview 2 project to a .NET Core SDK 1.0 project.</span></span>  |
| [<span data-ttu-id="ae63a-199">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="ae63a-199">dotnet msbuild</span></span>](dotnet-msbuild.md)           | <span data-ttu-id="ae63a-200">Oferece acesso à linha de comando do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="ae63a-200">Provides access to the MSBuild command line.</span></span>                        |
| [<span data-ttu-id="ae63a-201">dotnet new</span><span class="sxs-lookup"><span data-stu-id="ae63a-201">dotnet new</span></span>](dotnet-new.md)                   | <span data-ttu-id="ae63a-202">Inicializa um projeto do C# ou F# de um modelo especificado.</span><span class="sxs-lookup"><span data-stu-id="ae63a-202">Initializes a C# or F# project for a given template.</span></span>                |
| [<span data-ttu-id="ae63a-203">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="ae63a-203">dotnet pack</span></span>](dotnet-pack.md)                 | <span data-ttu-id="ae63a-204">Cria um pacote NuGet do seu código.</span><span class="sxs-lookup"><span data-stu-id="ae63a-204">Creates a NuGet package of your code.</span></span>                               |
| [<span data-ttu-id="ae63a-205">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="ae63a-205">dotnet publish</span></span>](dotnet-publish.md)           | <span data-ttu-id="ae63a-206">Publica um aplicativo dependente do .NET Framework ou autocontido.</span><span class="sxs-lookup"><span data-stu-id="ae63a-206">Publishes a .NET framework-dependent or self-contained application.</span></span> |
| [<span data-ttu-id="ae63a-207">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="ae63a-207">dotnet restore</span></span>](dotnet-restore.md)           | <span data-ttu-id="ae63a-208">Restaura as dependências para um determinado aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ae63a-208">Restores the dependencies for a given application.</span></span>                  |
| [<span data-ttu-id="ae63a-209">dotnet run</span><span class="sxs-lookup"><span data-stu-id="ae63a-209">dotnet run</span></span>](dotnet-run.md)                   | <span data-ttu-id="ae63a-210">Executa o aplicativo na origem.</span><span class="sxs-lookup"><span data-stu-id="ae63a-210">Runs the application from source.</span></span>                                   |
| [<span data-ttu-id="ae63a-211">dotnet sln</span><span class="sxs-lookup"><span data-stu-id="ae63a-211">dotnet sln</span></span>](dotnet-sln.md)                   | <span data-ttu-id="ae63a-212">Opções para adicionar, remover e listar projetos em um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="ae63a-212">Options to add, remove, and list projects in a solution file.</span></span>       |
| [<span data-ttu-id="ae63a-213">dotnet store</span><span class="sxs-lookup"><span data-stu-id="ae63a-213">dotnet store</span></span>](dotnet-store.md)               | <span data-ttu-id="ae63a-214">Armazena os assemblies no repositório de pacotes de runtime.</span><span class="sxs-lookup"><span data-stu-id="ae63a-214">Stores assemblies in the runtime package store.</span></span>                     |
| [<span data-ttu-id="ae63a-215">teste dotnet</span><span class="sxs-lookup"><span data-stu-id="ae63a-215">dotnet test</span></span>](dotnet-test.md)                 | <span data-ttu-id="ae63a-216">Executa testes usando um executor de teste.</span><span class="sxs-lookup"><span data-stu-id="ae63a-216">Runs tests using a test runner.</span></span>                                     |

### <a name="project-references"></a><span data-ttu-id="ae63a-217">Referências de projeto</span><span class="sxs-lookup"><span data-stu-id="ae63a-217">Project references</span></span>

<span data-ttu-id="ae63a-218">Comando</span><span class="sxs-lookup"><span data-stu-id="ae63a-218">Command</span></span> | <span data-ttu-id="ae63a-219">Função</span><span class="sxs-lookup"><span data-stu-id="ae63a-219">Function</span></span>
--- | ---
[<span data-ttu-id="ae63a-220">dotnet add reference</span><span class="sxs-lookup"><span data-stu-id="ae63a-220">dotnet add reference</span></span>](dotnet-add-reference.md) | <span data-ttu-id="ae63a-221">Adiciona uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="ae63a-221">Adds a project reference.</span></span>
[<span data-ttu-id="ae63a-222">dotnet list reference</span><span class="sxs-lookup"><span data-stu-id="ae63a-222">dotnet list reference</span></span>](dotnet-list-reference.md) | <span data-ttu-id="ae63a-223">Lista referências ao projeto.</span><span class="sxs-lookup"><span data-stu-id="ae63a-223">Lists project references.</span></span>
[<span data-ttu-id="ae63a-224">dotnet remove reference</span><span class="sxs-lookup"><span data-stu-id="ae63a-224">dotnet remove reference</span></span>](dotnet-remove-reference.md) | <span data-ttu-id="ae63a-225">Remove uma referência ao projeto.</span><span class="sxs-lookup"><span data-stu-id="ae63a-225">Removes a project reference.</span></span>

### <a name="nuget-packages"></a><span data-ttu-id="ae63a-226">Pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="ae63a-226">NuGet packages</span></span>

<span data-ttu-id="ae63a-227">Comando</span><span class="sxs-lookup"><span data-stu-id="ae63a-227">Command</span></span> | <span data-ttu-id="ae63a-228">Função</span><span class="sxs-lookup"><span data-stu-id="ae63a-228">Function</span></span>
--- | ---
[<span data-ttu-id="ae63a-229">dotnet add package</span><span class="sxs-lookup"><span data-stu-id="ae63a-229">dotnet add package</span></span>](dotnet-add-package.md) | <span data-ttu-id="ae63a-230">Adiciona um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="ae63a-230">Adds a NuGet package.</span></span>
[<span data-ttu-id="ae63a-231">dotnet remove package</span><span class="sxs-lookup"><span data-stu-id="ae63a-231">dotnet remove package</span></span>](dotnet-remove-package.md) | <span data-ttu-id="ae63a-232">Remove um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="ae63a-232">Removes a NuGet package.</span></span>

### <a name="nuget-commands"></a><span data-ttu-id="ae63a-233">Comandos NuGet</span><span class="sxs-lookup"><span data-stu-id="ae63a-233">NuGet commands</span></span>

<span data-ttu-id="ae63a-234">Comando</span><span class="sxs-lookup"><span data-stu-id="ae63a-234">Command</span></span> | <span data-ttu-id="ae63a-235">Função</span><span class="sxs-lookup"><span data-stu-id="ae63a-235">Function</span></span>
--- | ---
[<span data-ttu-id="ae63a-236">dotnet nuget delete</span><span class="sxs-lookup"><span data-stu-id="ae63a-236">dotnet nuget delete</span></span>](dotnet-nuget-delete.md) | <span data-ttu-id="ae63a-237">Exclui ou retira da lista um pacote do servidor.</span><span class="sxs-lookup"><span data-stu-id="ae63a-237">Deletes or unlists a package from the server.</span></span>
[<span data-ttu-id="ae63a-238">dotnet nuget locals</span><span class="sxs-lookup"><span data-stu-id="ae63a-238">dotnet nuget locals</span></span>](dotnet-nuget-locals.md) | <span data-ttu-id="ae63a-239">Limpa ou lista os recursos locais do NuGet, como cache de solicitação http, cache temporário ou pasta de pacotes globais em todo o computador.</span><span class="sxs-lookup"><span data-stu-id="ae63a-239">Clears or lists local NuGet resources such as http-request cache, temporary cache, or machine-wide global packages folder.</span></span>
[<span data-ttu-id="ae63a-240">dotnet nuget push</span><span class="sxs-lookup"><span data-stu-id="ae63a-240">dotnet nuget push</span></span>](dotnet-nuget-push.md) | <span data-ttu-id="ae63a-241">Envia um pacote ao servidor e os publica.</span><span class="sxs-lookup"><span data-stu-id="ae63a-241">Pushes a package to the server and publishes it.</span></span>

### <a name="global-tool-path-and-local-tools-commands"></a><span data-ttu-id="ae63a-242">Comandos de ferramentas globais, de caminho de ferramentas e locais</span><span class="sxs-lookup"><span data-stu-id="ae63a-242">Global, tool-path, and local tools commands</span></span>

<span data-ttu-id="ae63a-243">As ferramentas são aplicativos de console que são instalados a partir de pacotes NuGet e são invocados a partir do prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="ae63a-243">Tools are console applications that are installed from NuGet packages and are invoked from the command prompt.</span></span> <span data-ttu-id="ae63a-244">Você mesmo pode escrever ferramentas ou instalar ferramentas escritas por terceiros.</span><span class="sxs-lookup"><span data-stu-id="ae63a-244">You can write tools yourself or install tools written by third parties.</span></span> <span data-ttu-id="ae63a-245">As ferramentas também são conhecidas como ferramentas globais, ferramentas de caminho de ferramentas e ferramentas locais.</span><span class="sxs-lookup"><span data-stu-id="ae63a-245">Tools are also known as global tools, tool-path tools, and local tools.</span></span> <span data-ttu-id="ae63a-246">Para obter mais informações, consulte [a visão geral das ferramentas .NET Core](global-tools.md).</span><span class="sxs-lookup"><span data-stu-id="ae63a-246">For more information, see [.NET Core tools overview](global-tools.md).</span></span> <span data-ttu-id="ae63a-247">Ferramentas globais e de caminho de ferramentas estão disponíveis a partir do .NET Core SDK 2.1.</span><span class="sxs-lookup"><span data-stu-id="ae63a-247">Global and tool-path tools are available starting with .NET Core SDK 2.1.</span></span> <span data-ttu-id="ae63a-248">As ferramentas locais estão disponíveis a partir do .NET Core SDK 3.0.</span><span class="sxs-lookup"><span data-stu-id="ae63a-248">Local tools are available starting with .NET Core SDK 3.0.</span></span>

<span data-ttu-id="ae63a-249">Comando</span><span class="sxs-lookup"><span data-stu-id="ae63a-249">Command</span></span> | <span data-ttu-id="ae63a-250">Função</span><span class="sxs-lookup"><span data-stu-id="ae63a-250">Function</span></span>
--- | ---
[<span data-ttu-id="ae63a-251">dotnet tool install</span><span class="sxs-lookup"><span data-stu-id="ae63a-251">dotnet tool install</span></span>](dotnet-tool-install.md) | <span data-ttu-id="ae63a-252">Instala uma ferramenta em sua máquina.</span><span class="sxs-lookup"><span data-stu-id="ae63a-252">Installs a tool on your machine.</span></span>
[<span data-ttu-id="ae63a-253">dotnet tool list</span><span class="sxs-lookup"><span data-stu-id="ae63a-253">dotnet tool list</span></span>](dotnet-tool-list.md) | <span data-ttu-id="ae63a-254">Lista todas as ferramentas globais, de caminho de ferramentas ou locais atualmente instaladas em sua máquina.</span><span class="sxs-lookup"><span data-stu-id="ae63a-254">Lists all global, tool-path, or local tools currently installed on your machine.</span></span>
[<span data-ttu-id="ae63a-255">dotnet tool uninstall</span><span class="sxs-lookup"><span data-stu-id="ae63a-255">dotnet tool uninstall</span></span>](dotnet-tool-uninstall.md) | <span data-ttu-id="ae63a-256">Desinstala uma ferramenta da sua máquina.</span><span class="sxs-lookup"><span data-stu-id="ae63a-256">Uninstalls a tool from your machine.</span></span>
[<span data-ttu-id="ae63a-257">dotnet tool update</span><span class="sxs-lookup"><span data-stu-id="ae63a-257">dotnet tool update</span></span>](dotnet-tool-update.md) | <span data-ttu-id="ae63a-258">Atualiza uma ferramenta instalada em sua máquina.</span><span class="sxs-lookup"><span data-stu-id="ae63a-258">Updates a tool that is installed on your machine.</span></span>

### <a name="additional-tools"></a><span data-ttu-id="ae63a-259">Ferramentas adicionais</span><span class="sxs-lookup"><span data-stu-id="ae63a-259">Additional tools</span></span>

<span data-ttu-id="ae63a-260">A partir do SDK do .NET Core 2.1.300, várias ferramentas que estavam disponíveis apenas por projeto usando `DotnetCliToolReference` agora estão disponíveis como parte do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ae63a-260">Starting with .NET Core SDK 2.1.300, a number of tools that were available only on a per project basis using `DotnetCliToolReference` are now available as part of the .NET Core SDK.</span></span> <span data-ttu-id="ae63a-261">Essas ferramentas estão listadas na tabela a seguir:</span><span class="sxs-lookup"><span data-stu-id="ae63a-261">These tools are listed in the following table:</span></span>

| <span data-ttu-id="ae63a-262">Ferramenta</span><span class="sxs-lookup"><span data-stu-id="ae63a-262">Tool</span></span>                                              | <span data-ttu-id="ae63a-263">Função</span><span class="sxs-lookup"><span data-stu-id="ae63a-263">Function</span></span>                                                     |
| ------------------------------------------------- | ------------------------------------------------------------ |
| <span data-ttu-id="ae63a-264">dev-certs</span><span class="sxs-lookup"><span data-stu-id="ae63a-264">dev-certs</span></span>                                         | <span data-ttu-id="ae63a-265">Cria e gerencia certificados de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="ae63a-265">Creates and manages development certificates.</span></span>                |
| [<span data-ttu-id="ae63a-266">Ef</span><span class="sxs-lookup"><span data-stu-id="ae63a-266">ef</span></span>](/ef/core/miscellaneous/cli/dotnet)           | <span data-ttu-id="ae63a-267">Ferramentas de linha de comando do Entity Framework Core.</span><span class="sxs-lookup"><span data-stu-id="ae63a-267">Entity Framework Core command-line tools.</span></span>                    |
| <span data-ttu-id="ae63a-268">sql-cache</span><span class="sxs-lookup"><span data-stu-id="ae63a-268">sql-cache</span></span>                                         | <span data-ttu-id="ae63a-269">Ferramentas de linha de comando de cache do SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ae63a-269">SQL Server cache command-line tools.</span></span>                         |
| [<span data-ttu-id="ae63a-270">user-secrets</span><span class="sxs-lookup"><span data-stu-id="ae63a-270">user-secrets</span></span>](/aspnet/core/security/app-secrets) | <span data-ttu-id="ae63a-271">Gerencia os segredos do usuário de desenvolvimento.</span><span class="sxs-lookup"><span data-stu-id="ae63a-271">Manages development user secrets.</span></span>                            |
| [<span data-ttu-id="ae63a-272">Assistir</span><span class="sxs-lookup"><span data-stu-id="ae63a-272">watch</span></span>](/aspnet/core/tutorials/dotnet-watch)      | <span data-ttu-id="ae63a-273">Inicia um observador de arquivo que executa um comando quando os arquivos são alterados.</span><span class="sxs-lookup"><span data-stu-id="ae63a-273">Starts a file watcher that runs a command when files change.</span></span> |

<span data-ttu-id="ae63a-274">Para obter mais informações sobre cada ferramenta, digite `dotnet <tool-name> --help`.</span><span class="sxs-lookup"><span data-stu-id="ae63a-274">For more information about each tool, type `dotnet <tool-name> --help`.</span></span>

## <a name="examples"></a><span data-ttu-id="ae63a-275">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ae63a-275">Examples</span></span>

<span data-ttu-id="ae63a-276">Crie um novo aplicativo de console .NET Core:</span><span class="sxs-lookup"><span data-stu-id="ae63a-276">Create a new .NET Core console application:</span></span>

```dotnetcli
dotnet new console
```

<span data-ttu-id="ae63a-277">Compile um projeto e suas dependências em um determinado diretório:</span><span class="sxs-lookup"><span data-stu-id="ae63a-277">Build a project and its dependencies in a given directory:</span></span>

```dotnetcli
dotnet build
```

<span data-ttu-id="ae63a-278">Execute um aplicativo:</span><span class="sxs-lookup"><span data-stu-id="ae63a-278">Run an application:</span></span>

```dotnetcli
dotnet myapp.dll
```

## <a name="environment-variables"></a><span data-ttu-id="ae63a-279">Variáveis de ambiente</span><span class="sxs-lookup"><span data-stu-id="ae63a-279">Environment variables</span></span>

- <span data-ttu-id="ae63a-280">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span><span class="sxs-lookup"><span data-stu-id="ae63a-280">`DOTNET_ROOT`, `DOTNET_ROOT(x86)`</span></span>

  <span data-ttu-id="ae63a-281">Especifica a localização dos tempos de execução do .NET Core, se eles não estiverem instalados no local padrão.</span><span class="sxs-lookup"><span data-stu-id="ae63a-281">Specifies the location of the .NET Core runtimes, if they are not installed in the default location.</span></span> <span data-ttu-id="ae63a-282">O local padrão `C:\Program Files\dotnet`no Windows é .</span><span class="sxs-lookup"><span data-stu-id="ae63a-282">The default location on Windows is `C:\Program Files\dotnet`.</span></span> <span data-ttu-id="ae63a-283">A localização padrão no Linux `/usr/share/dotnet`e macOS é .</span><span class="sxs-lookup"><span data-stu-id="ae63a-283">The default location on Linux and macOS is `/usr/share/dotnet`.</span></span> <span data-ttu-id="ae63a-284">Essa variável de ambiente é usada apenas ao executar aplicativos através de executáveis gerados (apphosts).</span><span class="sxs-lookup"><span data-stu-id="ae63a-284">This environment variable is used only when running apps via generated executables (apphosts).</span></span> <span data-ttu-id="ae63a-285">`DOTNET_ROOT(x86)`é usado em vez disso ao executar um executável de 32 bits em um sistema operacional de 64 bits.</span><span class="sxs-lookup"><span data-stu-id="ae63a-285">`DOTNET_ROOT(x86)` is used instead when running a 32-bit executable on a 64-bit OS.</span></span>

- `DOTNET_PACKAGES`

  <span data-ttu-id="ae63a-286">A pasta de pacotes globais.</span><span class="sxs-lookup"><span data-stu-id="ae63a-286">The global packages folder.</span></span> <span data-ttu-id="ae63a-287">Se não estiver definido, o padrão será `~/.nuget/packages` em Unix ou `%userprofile%\.nuget\packages` no Windows.</span><span class="sxs-lookup"><span data-stu-id="ae63a-287">If not set, it defaults to `~/.nuget/packages` on Unix or `%userprofile%\.nuget\packages` on Windows.</span></span>

- `DOTNET_SERVICING`

  <span data-ttu-id="ae63a-288">Especifica o local do índice de manutenção a ser usado pelo host compartilhado ao carregar o runtime.</span><span class="sxs-lookup"><span data-stu-id="ae63a-288">Specifies the location of the servicing index to use by the shared host when loading the runtime.</span></span>

- `DOTNET_CLI_TELEMETRY_OPTOUT`

  <span data-ttu-id="ae63a-289">Especifica se os dados sobre o uso de ferramentas .NET Core são coletados e enviados para a Microsoft.</span><span class="sxs-lookup"><span data-stu-id="ae63a-289">Specifies whether data about the .NET Core tools usage is collected and sent to Microsoft.</span></span> <span data-ttu-id="ae63a-290">Definido como `true` para recusar o recurso de telemetria (os valores `true`, `1` ou `yes` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="ae63a-290">Set to `true` to opt-out of the telemetry feature (values `true`, `1`, or `yes` accepted).</span></span> <span data-ttu-id="ae63a-291">Caso contrário, definido como `false` para aceitar os recursos de telemetria (os valores `false`, `0` ou `no` são aceitos).</span><span class="sxs-lookup"><span data-stu-id="ae63a-291">Otherwise, set to `false` to opt into the telemetry features (values `false`, `0`, or `no` accepted).</span></span> <span data-ttu-id="ae63a-292">Se não estiver definido, o padrão será `false`, e o recurso de telemetria estará ativo.</span><span class="sxs-lookup"><span data-stu-id="ae63a-292">If not set, the default is `false` and the telemetry feature is active.</span></span>

- `DOTNET_MULTILEVEL_LOOKUP`

  <span data-ttu-id="ae63a-293">Especifica se o runtime, a estrutura compartilhada ou o SDK do .NET Core são resolvidos no local global.</span><span class="sxs-lookup"><span data-stu-id="ae63a-293">Specifies whether .NET Core runtime, shared framework, or SDK are resolved from the global location.</span></span> <span data-ttu-id="ae63a-294">Se não for definido, ele `true`é padrão para 1 (lógico ).</span><span class="sxs-lookup"><span data-stu-id="ae63a-294">If not set, it defaults to 1 (logical `true`).</span></span> <span data-ttu-id="ae63a-295">Definir como 0 `false`(lógico ) para não resolver a partir do local global e ter instalações isoladas .NET Core.</span><span class="sxs-lookup"><span data-stu-id="ae63a-295">Set to 0 (logical `false`) to not resolve from the global location and have isolated .NET Core installations.</span></span> <span data-ttu-id="ae63a-296">Para obter mais informações sobre a pesquisa de vários níveis, consulte [Pesquisa SharedFX de vários níveis](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span><span class="sxs-lookup"><span data-stu-id="ae63a-296">For more information about multi-level lookup, see [Multi-level SharedFX Lookup](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/multilevel-sharedfx-lookup.md).</span></span>

- <span data-ttu-id="ae63a-297">`DOTNET_ROLL_FORWARD`**Disponível a partir de .NET Core 3.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="ae63a-297">`DOTNET_ROLL_FORWARD` **Available starting with .NET Core 3.x SDK.**</span></span>

  <span data-ttu-id="ae63a-298">Determina o comportamento de rolagem para a frente.</span><span class="sxs-lookup"><span data-stu-id="ae63a-298">Determines roll forward behavior.</span></span> <span data-ttu-id="ae63a-299">Para obter mais `--roll-forward` informações, consulte a opção no início deste artigo.</span><span class="sxs-lookup"><span data-stu-id="ae63a-299">For more information, see the `--roll-forward` option earlier in this article.</span></span>

- <span data-ttu-id="ae63a-300">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX`**Disponível em .NET Core 2.x SDK.**</span><span class="sxs-lookup"><span data-stu-id="ae63a-300">`DOTNET_ROLL_FORWARD_ON_NO_CANDIDATE_FX` **Available in .NET Core 2.x SDK.**</span></span>

  <span data-ttu-id="ae63a-301">Desabilita o roll forward da versão secundária, se definido como `0`.</span><span class="sxs-lookup"><span data-stu-id="ae63a-301">Disables minor version roll forward, if set to `0`.</span></span> <span data-ttu-id="ae63a-302">Para saber mais, confira [Efetuar roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span><span class="sxs-lookup"><span data-stu-id="ae63a-302">For more information, see [Roll forward](../whats-new/dotnet-core-2-1.md#roll-forward).</span></span>

- `DOTNET_CLI_UI_LANGUAGE`

  <span data-ttu-id="ae63a-303">Define a linguagem da IU CLI usando `en-us`um valor local, como .</span><span class="sxs-lookup"><span data-stu-id="ae63a-303">Sets the language of the CLI UI using a locale value such as `en-us`.</span></span> <span data-ttu-id="ae63a-304">Os valores suportados são os mesmos do Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="ae63a-304">The supported values are the same as for Visual Studio.</span></span> <span data-ttu-id="ae63a-305">Para obter mais informações, consulte a seção sobre a alteração do idioma do instalador na [documentação](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019)de instalação do Visual Studio .</span><span class="sxs-lookup"><span data-stu-id="ae63a-305">For more information, see the section on changing the installer language in the [Visual Studio installation documentation](https://docs.microsoft.com/visualstudio/install/install-visual-studio?view=vs-2019).</span></span> <span data-ttu-id="ae63a-306">As regras do gerenciador de recursos .NET se aplicam,&mdash;para que você não `CultureInfo` tenha que escolher uma correspondência exata, você também pode escolher descendentes na árvore.</span><span class="sxs-lookup"><span data-stu-id="ae63a-306">The .NET resource manager rules apply, so you don't have to pick an exact match&mdash;you can also pick descendants in the `CultureInfo` tree.</span></span> <span data-ttu-id="ae63a-307">Por exemplo, se você `fr-CA`defini-lo para , `fr` o CLI encontrará e usará as traduções.</span><span class="sxs-lookup"><span data-stu-id="ae63a-307">For example, if you set it to `fr-CA`, the CLI will find and use the `fr` translations.</span></span> <span data-ttu-id="ae63a-308">Se você defini-lo para um idioma que não é suportado, o CLI volta para o inglês.</span><span class="sxs-lookup"><span data-stu-id="ae63a-308">If you set it to a language that is not supported, the CLI falls back to English.</span></span>

- `DOTNET_DISABLE_GUI_ERRORS`

  <span data-ttu-id="ae63a-309">Para executáveis gerados habilitados por GUI - desativa o popup de diálogo que normalmente é mostrado para determinadas classes de erros.</span><span class="sxs-lookup"><span data-stu-id="ae63a-309">For GUI-enabled generated executables - disables dialog popup which normally shows for certain classes of errors.</span></span> <span data-ttu-id="ae63a-310">Ele só `stderr` escreve e sai nesses casos.</span><span class="sxs-lookup"><span data-stu-id="ae63a-310">It only writes to `stderr` and exits in those cases.</span></span>
  
- `DOTNET_ADDITIONAL_DEPS`

  <span data-ttu-id="ae63a-311">Equivalente à `--additional-deps`opção CLI .</span><span class="sxs-lookup"><span data-stu-id="ae63a-311">Equivalent to CLI option `--additional-deps`.</span></span>

- `DOTNET_RUNTIME_ID`

  <span data-ttu-id="ae63a-312">Substitui o RID detectado.</span><span class="sxs-lookup"><span data-stu-id="ae63a-312">Overrides the detected RID.</span></span>

- `DOTNET_SHARED_STORE`

  <span data-ttu-id="ae63a-313">A localização da "loja compartilhada" que a resolução do conjunto recua em alguns casos.</span><span class="sxs-lookup"><span data-stu-id="ae63a-313">Location of the "shared store" which assembly resolution falls back to in some cases.</span></span>

- `DOTNET_STARTUP_HOOKS`

  <span data-ttu-id="ae63a-314">Lista de montagens para carregar e executar ganchos de inicialização.</span><span class="sxs-lookup"><span data-stu-id="ae63a-314">List of assemblies to load and execute startup hooks from.</span></span>

- <span data-ttu-id="ae63a-315">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span><span class="sxs-lookup"><span data-stu-id="ae63a-315">`COREHOST_TRACE`, `COREHOST_TRACEFILE`, `COREHOST_TRACE_VERBOSITY`</span></span>

  <span data-ttu-id="ae63a-316">Controla o rastreamento de diagnósticos dos `dotnet.exe`componentes de hospedagem, tais como , `hostfxr`e `hostpolicy`.</span><span class="sxs-lookup"><span data-stu-id="ae63a-316">Controls diagnostics tracing from the hosting components, such as `dotnet.exe`, `hostfxr`, and `hostpolicy`.</span></span>

## <a name="see-also"></a><span data-ttu-id="ae63a-317">Confira também</span><span class="sxs-lookup"><span data-stu-id="ae63a-317">See also</span></span>

- [<span data-ttu-id="ae63a-318">Arquivos de configuração de runtime</span><span class="sxs-lookup"><span data-stu-id="ae63a-318">Runtime Configuration Files</span></span>](https://github.com/dotnet/cli/blob/master/Documentation/specs/runtime-configuration-file.md)
- [<span data-ttu-id="ae63a-319">Configurações de configuração de tempo de execução do .NET Core</span><span class="sxs-lookup"><span data-stu-id="ae63a-319">.NET Core run-time configuration settings</span></span>](../run-time-config/index.md)
