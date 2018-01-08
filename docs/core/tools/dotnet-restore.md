---
title: "Comando dotnet restore – CLI do .NET Core"
description: "Saiba como restaurar as dependências e ferramentas específicas de projeto com o comando dotnet restore."
keywords: dotnet-restore, CLI, comando da CLI, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 11/30/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: dc93e0554d422ddf42ac54dd94223f0285451e85
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/23/2017
---
# <a name="dotnet-restore"></a><span data-ttu-id="b82b4-104">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="b82b4-104">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b82b4-105">Nome</span><span class="sxs-lookup"><span data-stu-id="b82b4-105">Name</span></span>

<span data-ttu-id="b82b4-106">`dotnet restore` – Restaura as dependências e as ferramentas de um projeto.</span><span class="sxs-lookup"><span data-stu-id="b82b4-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b82b4-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="b82b4-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b82b4-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="b82b4-108">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b82b4-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b82b4-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="b82b4-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="b82b4-110">Description</span></span>

<span data-ttu-id="b82b4-111">O comando `dotnet restore` usa o NuGet para restaurar as dependências e ferramentas específicas de projeto especificadas no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="b82b4-111">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="b82b4-112">Por padrão, a restauração das dependências e as ferramentas são feitas em paralelo.</span><span class="sxs-lookup"><span data-stu-id="b82b4-112">By default, the restoration of dependencies and tools are performed in parallel.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="b82b4-113">Para restaurar as dependências, o NuGet precisa dos feeds de onde se encontram os pacotes.</span><span class="sxs-lookup"><span data-stu-id="b82b4-113">In order to restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="b82b4-114">Os feeds são geralmente fornecidos por meio do arquivo de configuração *NuGet.config*.</span><span class="sxs-lookup"><span data-stu-id="b82b4-114">Feeds are usually provided via the *NuGet.config* configuration file.</span></span> <span data-ttu-id="b82b4-115">Um arquivo de configuração padrão é fornecido quando as ferramentas da CLI são instaladas.</span><span class="sxs-lookup"><span data-stu-id="b82b4-115">A default configuration file is provided when the CLI tools are installed.</span></span> <span data-ttu-id="b82b4-116">Especifique mais feeds criando seu próprio arquivo *NuGet.config* no diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="b82b4-116">You specify additional feeds by creating your own *NuGet.config* file in the project directory.</span></span> <span data-ttu-id="b82b4-117">Também é possível especificar outros feeds por invocação em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="b82b4-117">You also specify additional feeds per invocation at a command prompt.</span></span>

<span data-ttu-id="b82b4-118">Para dependências, especifique onde os pacotes restaurados são colocados durante a operação de restauração usando o argumento `--packages`.</span><span class="sxs-lookup"><span data-stu-id="b82b4-118">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="b82b4-119">Se não for especificado, o cache do pacote NuGet padrão será usado, o qual pode ser encontrado no diretório `.nuget/packages` do diretório base do usuário em todos os sistemas operacionais (por exemplo, */home/user1* no Linux ou *C:\Usuários\user1* no Windows).</span><span class="sxs-lookup"><span data-stu-id="b82b4-119">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems (for example, */home/user1* on Linux or *C:\Users\user1* on Windows).</span></span>

<span data-ttu-id="b82b4-120">Para ferramentas específicas do projeto, o `dotnet restore` primeiro restaura o pacote no qual a ferramenta foi empacotada e prossegue com a restauração das dependências da ferramenta conforme especificado no seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="b82b4-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

<span data-ttu-id="b82b4-121">O comportamento do comando `dotnet restore` é afetado por algumas das configurações no arquivo *Nuget.Config*, se estiver presente.</span><span class="sxs-lookup"><span data-stu-id="b82b4-121">The behavior of the `dotnet restore` command is affected by some of the settings in the *Nuget.Config* file, if present.</span></span> <span data-ttu-id="b82b4-122">Por exemplo, definir o `globalPackagesFolder` em *NuGet.Config* coloca os pacotes NuGet restaurados na pasta especificada.</span><span class="sxs-lookup"><span data-stu-id="b82b4-122">For example, setting the `globalPackagesFolder` in *NuGet.Config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="b82b4-123">Essa é uma alternativa para especificar a opção `--packages` no comando `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="b82b4-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="b82b4-124">Para obter mais informações, consulte a [Referência do NuGet.Config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="b82b4-124">For more information, see the [NuGet.Config reference](/nuget/schema/nuget-config-file).</span></span>

## <a name="implicit-dotnet-restore"></a><span data-ttu-id="b82b4-125">`dotnet restore` implícito</span><span class="sxs-lookup"><span data-stu-id="b82b4-125">Implicit `dotnet restore`</span></span>

<span data-ttu-id="b82b4-126">Começando com o .NET Core 2.0, se necessário, o `dotnet restore` será executado implicitamente quando você executar os comandos a seguir:</span><span class="sxs-lookup"><span data-stu-id="b82b4-126">Starting with .NET Core 2.0, `dotnet restore` is run implicitly if necessary when you issue the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="b82b4-127">Na maioria dos casos, você não precisa usar o comando `dotnet restore` explicitamente.</span><span class="sxs-lookup"><span data-stu-id="b82b4-127">In most cases, you no longer need to explicitly use the `dotnet restore` command.</span></span> 

<span data-ttu-id="b82b4-128">Em alguns casos, não é oportuno que o `dotnet restore` seja executado implicitamente.</span><span class="sxs-lookup"><span data-stu-id="b82b4-128">In some cases, it is inconvenient for `dotnet restore` to run implicitly.</span></span> <span data-ttu-id="b82b4-129">Por exemplo, alguns sistemas automatizados, como os sistemas de compilação, precisam chamar o `dotnet restore` explicitamente para controlar o momento em que a restauração ocorre para que possam controlar o uso de rede.</span><span class="sxs-lookup"><span data-stu-id="b82b4-129">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="b82b4-130">Para evitar que o `dotnet restore` seja executado implicitamente, você pode usar a opção `--no-restore` com qualquer um desses comandos para desabilitar a restauração implícita.</span><span class="sxs-lookup"><span data-stu-id="b82b4-130">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` switch with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="b82b4-131">Arguments</span><span class="sxs-lookup"><span data-stu-id="b82b4-131">Arguments</span></span>

`ROOT`

<span data-ttu-id="b82b4-132">Caminho opcional para o arquivo de projeto a ser restaurado.</span><span class="sxs-lookup"><span data-stu-id="b82b4-132">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="b82b4-133">Opções</span><span class="sxs-lookup"><span data-stu-id="b82b4-133">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="b82b4-134">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="b82b4-134">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="b82b4-135">O arquivo de configuração NuGet (*NuGet.config*) a ser usado para a operação de restauração.</span><span class="sxs-lookup"><span data-stu-id="b82b4-135">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="b82b4-136">Desabilita a restauração de vários projetos paralelamente.</span><span class="sxs-lookup"><span data-stu-id="b82b4-136">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="b82b4-137">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="b82b4-137">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="b82b4-138">Isso é equivalente a excluir o arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="b82b4-138">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="b82b4-139">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="b82b4-139">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="b82b4-140">Avise somente sobre fontes com falha se houver pacotes que atendem ao requisito de versão.</span><span class="sxs-lookup"><span data-stu-id="b82b4-140">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="b82b4-141">Especifica para não armazenar os pacotes e solicitações HTTP em cache.</span><span class="sxs-lookup"><span data-stu-id="b82b4-141">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="b82b4-142">Ao restaurar um projeto com referências de P2P (projeto a projeto), restaura o projeto raiz, não as referências.</span><span class="sxs-lookup"><span data-stu-id="b82b4-142">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="b82b4-143">Especifica o diretório para os pacotes restaurados.</span><span class="sxs-lookup"><span data-stu-id="b82b4-143">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="b82b4-144">Especifica um tempo de execução para a restauração do pacote.</span><span class="sxs-lookup"><span data-stu-id="b82b4-144">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="b82b4-145">Isso é usado para restaurar pacotes para tempos de execução não listados explicitamente na marca `<RuntimeIdentifiers>` no arquivo *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="b82b4-145">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="b82b4-146">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="b82b4-146">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="b82b4-147">Forneça diversas RIDs especificando essa opção várias vezes.</span><span class="sxs-lookup"><span data-stu-id="b82b4-147">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="b82b4-148">Especifica uma origem de pacote NuGet a ser usada durante a operação de restauração.</span><span class="sxs-lookup"><span data-stu-id="b82b4-148">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="b82b4-149">Isso substitui todas as fontes especificadas nos arquivos *NuGet.config*.</span><span class="sxs-lookup"><span data-stu-id="b82b4-149">This overrides all of the sources specified in the *NuGet.config* file(s).</span></span> <span data-ttu-id="b82b4-150">Diversas fontes podem ser fornecidas especificando essa opção várias vezes.</span><span class="sxs-lookup"><span data-stu-id="b82b4-150">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="b82b4-151">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="b82b4-151">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b82b4-152">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b82b4-152">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="b82b4-153">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="b82b4-153">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="b82b4-154">O arquivo de configuração NuGet (*NuGet.config*) a ser usado para a operação de restauração.</span><span class="sxs-lookup"><span data-stu-id="b82b4-154">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="b82b4-155">Desabilita a restauração de vários projetos paralelamente.</span><span class="sxs-lookup"><span data-stu-id="b82b4-155">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="b82b4-156">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="b82b4-156">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="b82b4-157">Avise somente sobre fontes com falha se houver pacotes que atendem ao requisito de versão.</span><span class="sxs-lookup"><span data-stu-id="b82b4-157">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="b82b4-158">Especifica para não armazenar os pacotes e solicitações HTTP em cache.</span><span class="sxs-lookup"><span data-stu-id="b82b4-158">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="b82b4-159">Ao restaurar um projeto com referências de P2P (projeto a projeto), restaura o projeto raiz, não as referências.</span><span class="sxs-lookup"><span data-stu-id="b82b4-159">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="b82b4-160">Especifica o diretório para os pacotes restaurados.</span><span class="sxs-lookup"><span data-stu-id="b82b4-160">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="b82b4-161">Especifica um tempo de execução para a restauração do pacote.</span><span class="sxs-lookup"><span data-stu-id="b82b4-161">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="b82b4-162">Isso é usado para restaurar pacotes para tempos de execução não listados explicitamente na marca `<RuntimeIdentifiers>` no arquivo *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="b82b4-162">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="b82b4-163">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="b82b4-163">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="b82b4-164">Forneça diversas RIDs especificando essa opção várias vezes.</span><span class="sxs-lookup"><span data-stu-id="b82b4-164">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="b82b4-165">Especifica uma origem de pacote NuGet a ser usada durante a operação de restauração.</span><span class="sxs-lookup"><span data-stu-id="b82b4-165">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="b82b4-166">Isso substitui todas as fontes especificadas nos arquivos *NuGet.config*.</span><span class="sxs-lookup"><span data-stu-id="b82b4-166">This overrides all of the sources specified in the *NuGet.config* file(s).</span></span> <span data-ttu-id="b82b4-167">Diversas fontes podem ser fornecidas especificando essa opção várias vezes.</span><span class="sxs-lookup"><span data-stu-id="b82b4-167">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="b82b4-168">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="b82b4-168">Sets the verbosity level of the command.</span></span> <span data-ttu-id="b82b4-169">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="b82b4-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="b82b4-170">Exemplos</span><span class="sxs-lookup"><span data-stu-id="b82b4-170">Examples</span></span>

<span data-ttu-id="b82b4-171">Restaure as dependências e as ferramentas para o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="b82b4-171">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="b82b4-172">Restaure as dependências e as ferramentas para o projeto `app1` encontrado no caminho fornecido:</span><span class="sxs-lookup"><span data-stu-id="b82b4-172">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="b82b4-173">Restaure as dependências e as ferramentas para o projeto no diretório atual usando o caminho de arquivo fornecido como a fonte:</span><span class="sxs-lookup"><span data-stu-id="b82b4-173">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="b82b4-174">Restaure as dependências e as ferramentas para o projeto no diretório atual usando os caminhos dos dois arquivos fornecidos como fontes:</span><span class="sxs-lookup"><span data-stu-id="b82b4-174">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="b82b4-175">Restaure as dependências e as ferramentas do projeto no diretório atual e mostre apenas a saída mínima:</span><span class="sxs-lookup"><span data-stu-id="b82b4-175">Restore dependencies and tools for the project in the current directory and shows only minimal output:</span></span>

`dotnet restore --verbosity minimal`
