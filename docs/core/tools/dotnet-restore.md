---
title: "Comando dotnet restore – CLI do .NET Core"
description: "Saiba como restaurar as dependências e ferramentas específicas de projeto com o comando dotnet restore."
keywords: dotnet-restore, CLI, comando da CLI, .NET Core
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.openlocfilehash: 82a78dcb0cc85e2ba087b6df5ee029cbfb687358
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="dotnet-restore"></a><span data-ttu-id="799d2-104">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="799d2-104">dotnet restore</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="799d2-105">Nome</span><span class="sxs-lookup"><span data-stu-id="799d2-105">Name</span></span>

<span data-ttu-id="799d2-106">`dotnet restore` – Restaura as dependências e as ferramentas de um projeto.</span><span class="sxs-lookup"><span data-stu-id="799d2-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="799d2-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="799d2-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="799d2-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="799d2-108">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--force] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="799d2-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="799d2-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet restore [<ROOT>] [--configfile] [--disable-parallel] [--ignore-failed-sources] [--no-cache] [--no-dependencies] [--packages] [-r|--runtime] [-s|--source] [-v|--verbosity]
dotnet restore [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="799d2-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="799d2-110">Description</span></span>

<span data-ttu-id="799d2-111">O comando `dotnet restore` usa o NuGet para restaurar as dependências e ferramentas específicas de projeto especificadas no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="799d2-111">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="799d2-112">Por padrão, a restauração das dependências e as ferramentas são feitas em paralelo.</span><span class="sxs-lookup"><span data-stu-id="799d2-112">By default, the restoration of dependencies and tools are performed in parallel.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="799d2-113">Para restaurar as dependências, o NuGet precisa dos feeds de onde se encontram os pacotes.</span><span class="sxs-lookup"><span data-stu-id="799d2-113">In order to restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="799d2-114">Os feeds são geralmente fornecidos por meio do arquivo de configuração *NuGet.config*.</span><span class="sxs-lookup"><span data-stu-id="799d2-114">Feeds are usually provided via the *NuGet.config* configuration file.</span></span> <span data-ttu-id="799d2-115">Um arquivo de configuração padrão é fornecido quando as ferramentas da CLI são instaladas.</span><span class="sxs-lookup"><span data-stu-id="799d2-115">A default configuration file is provided when the CLI tools are installed.</span></span> <span data-ttu-id="799d2-116">Especifique mais feeds criando seu próprio arquivo *NuGet.config* no diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="799d2-116">You specify additional feeds by creating your own *NuGet.config* file in the project directory.</span></span> <span data-ttu-id="799d2-117">Também é possível especificar outros feeds por invocação em um prompt de comando.</span><span class="sxs-lookup"><span data-stu-id="799d2-117">You also specify additional feeds per invocation at a command prompt.</span></span>

<span data-ttu-id="799d2-118">Para dependências, especifique onde os pacotes restaurados são colocados durante a operação de restauração usando o argumento `--packages`.</span><span class="sxs-lookup"><span data-stu-id="799d2-118">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="799d2-119">Se não for especificado, o cache do pacote NuGet padrão será usado, o qual pode ser encontrado no diretório `.nuget/packages` do diretório base do usuário em todos os sistemas operacionais (por exemplo, */home/user1* no Linux ou *C:\Usuários\user1* no Windows).</span><span class="sxs-lookup"><span data-stu-id="799d2-119">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems (for example, */home/user1* on Linux or *C:\Users\user1* on Windows).</span></span>

<span data-ttu-id="799d2-120">Para ferramentas específicas do projeto, o `dotnet restore` primeiro restaura o pacote no qual a ferramenta foi empacotada e prossegue com a restauração das dependências da ferramenta conforme especificado no seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="799d2-120">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

<span data-ttu-id="799d2-121">O comportamento do comando `dotnet restore` é afetado por algumas das configurações no arquivo *Nuget.Config*, se estiver presente.</span><span class="sxs-lookup"><span data-stu-id="799d2-121">The behavior of the `dotnet restore` command is affected by some of the settings in the *Nuget.Config* file, if present.</span></span> <span data-ttu-id="799d2-122">Por exemplo, definir o `globalPackagesFolder` em *NuGet.Config* coloca os pacotes NuGet restaurados na pasta especificada.</span><span class="sxs-lookup"><span data-stu-id="799d2-122">For example, setting the `globalPackagesFolder` in *NuGet.Config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="799d2-123">Essa é uma alternativa para especificar a opção `--packages` no comando `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="799d2-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="799d2-124">Para obter mais informações, consulte a [Referência do NuGet.Config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="799d2-124">For more information, see the [NuGet.Config reference](/nuget/schema/nuget-config-file).</span></span>

## <a name="arguments"></a><span data-ttu-id="799d2-125">Arguments</span><span class="sxs-lookup"><span data-stu-id="799d2-125">Arguments</span></span>

`ROOT`

<span data-ttu-id="799d2-126">Caminho opcional para o arquivo de projeto a ser restaurado.</span><span class="sxs-lookup"><span data-stu-id="799d2-126">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="799d2-127">Opções</span><span class="sxs-lookup"><span data-stu-id="799d2-127">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="799d2-128">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="799d2-128">.NET Core 2.x</span></span>](#tab/netcore2x)

`--configfile <FILE>`

<span data-ttu-id="799d2-129">O arquivo de configuração NuGet (*NuGet.config*) a ser usado para a operação de restauração.</span><span class="sxs-lookup"><span data-stu-id="799d2-129">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="799d2-130">Desabilita a restauração de vários projetos paralelamente.</span><span class="sxs-lookup"><span data-stu-id="799d2-130">Disables restoring multiple projects in parallel.</span></span>

`--force`

<span data-ttu-id="799d2-131">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="799d2-131">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="799d2-132">Isso é equivalente a excluir o arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="799d2-132">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="799d2-133">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="799d2-133">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="799d2-134">Avise somente sobre fontes com falha se houver pacotes que atendem ao requisito de versão.</span><span class="sxs-lookup"><span data-stu-id="799d2-134">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="799d2-135">Especifica para não armazenar os pacotes e solicitações HTTP em cache.</span><span class="sxs-lookup"><span data-stu-id="799d2-135">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="799d2-136">Ao restaurar um projeto com referências de P2P (projeto a projeto), restaura o projeto raiz, não as referências.</span><span class="sxs-lookup"><span data-stu-id="799d2-136">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="799d2-137">Especifica o diretório para os pacotes restaurados.</span><span class="sxs-lookup"><span data-stu-id="799d2-137">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="799d2-138">Especifica um tempo de execução para a restauração do pacote.</span><span class="sxs-lookup"><span data-stu-id="799d2-138">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="799d2-139">Isso é usado para restaurar pacotes para tempos de execução não listados explicitamente na marca `<RuntimeIdentifiers>` no arquivo *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="799d2-139">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="799d2-140">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="799d2-140">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="799d2-141">Forneça diversas RIDs especificando essa opção várias vezes.</span><span class="sxs-lookup"><span data-stu-id="799d2-141">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="799d2-142">Especifica uma origem de pacote NuGet a ser usada durante a operação de restauração.</span><span class="sxs-lookup"><span data-stu-id="799d2-142">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="799d2-143">Isso substitui todas as fontes especificadas nos arquivos *NuGet.config*.</span><span class="sxs-lookup"><span data-stu-id="799d2-143">This overrides all of the sources specified in the *NuGet.config* file(s).</span></span> <span data-ttu-id="799d2-144">Diversas fontes podem ser fornecidas especificando essa opção várias vezes.</span><span class="sxs-lookup"><span data-stu-id="799d2-144">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="799d2-145">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="799d2-145">Sets the verbosity level of the command.</span></span> <span data-ttu-id="799d2-146">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="799d2-146">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="799d2-147">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="799d2-147">.NET Core 1.x</span></span>](#tab/netcore1x)

`--configfile <FILE>`

<span data-ttu-id="799d2-148">O arquivo de configuração NuGet (*NuGet.config*) a ser usado para a operação de restauração.</span><span class="sxs-lookup"><span data-stu-id="799d2-148">The NuGet configuration file (*NuGet.config*) to use for the restore operation.</span></span>

`--disable-parallel`

<span data-ttu-id="799d2-149">Desabilita a restauração de vários projetos paralelamente.</span><span class="sxs-lookup"><span data-stu-id="799d2-149">Disables restoring multiple projects in parallel.</span></span>

`-h|--help`

<span data-ttu-id="799d2-150">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="799d2-150">Prints out a short help for the command.</span></span>

`--ignore-failed-sources`

<span data-ttu-id="799d2-151">Avise somente sobre fontes com falha se houver pacotes que atendem ao requisito de versão.</span><span class="sxs-lookup"><span data-stu-id="799d2-151">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

`--no-cache`

<span data-ttu-id="799d2-152">Especifica para não armazenar os pacotes e solicitações HTTP em cache.</span><span class="sxs-lookup"><span data-stu-id="799d2-152">Specifies to not cache packages and HTTP requests.</span></span>

`--no-dependencies`

<span data-ttu-id="799d2-153">Ao restaurar um projeto com referências de P2P (projeto a projeto), restaura o projeto raiz, não as referências.</span><span class="sxs-lookup"><span data-stu-id="799d2-153">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

`--packages <PACKAGES_DIRECTORY>`

<span data-ttu-id="799d2-154">Especifica o diretório para os pacotes restaurados.</span><span class="sxs-lookup"><span data-stu-id="799d2-154">Specifies the directory for restored packages.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="799d2-155">Especifica um tempo de execução para a restauração do pacote.</span><span class="sxs-lookup"><span data-stu-id="799d2-155">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="799d2-156">Isso é usado para restaurar pacotes para tempos de execução não listados explicitamente na marca `<RuntimeIdentifiers>` no arquivo *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="799d2-156">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="799d2-157">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="799d2-157">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="799d2-158">Forneça diversas RIDs especificando essa opção várias vezes.</span><span class="sxs-lookup"><span data-stu-id="799d2-158">Provide multiple RIDs by specifying this option multiple times.</span></span>

`-s|--source <SOURCE>`

<span data-ttu-id="799d2-159">Especifica uma origem de pacote NuGet a ser usada durante a operação de restauração.</span><span class="sxs-lookup"><span data-stu-id="799d2-159">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="799d2-160">Isso substitui todas as fontes especificadas nos arquivos *NuGet.config*.</span><span class="sxs-lookup"><span data-stu-id="799d2-160">This overrides all of the sources specified in the *NuGet.config* file(s).</span></span> <span data-ttu-id="799d2-161">Diversas fontes podem ser fornecidas especificando essa opção várias vezes.</span><span class="sxs-lookup"><span data-stu-id="799d2-161">Multiple sources can be provided by specifying this option multiple times.</span></span>

`--verbosity <LEVEL>`

<span data-ttu-id="799d2-162">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="799d2-162">Sets the verbosity level of the command.</span></span> <span data-ttu-id="799d2-163">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="799d2-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="799d2-164">Exemplos</span><span class="sxs-lookup"><span data-stu-id="799d2-164">Examples</span></span>

<span data-ttu-id="799d2-165">Restaure as dependências e as ferramentas para o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="799d2-165">Restore dependencies and tools for the project in the current directory:</span></span>

`dotnet restore`

<span data-ttu-id="799d2-166">Restaure as dependências e as ferramentas para o projeto `app1` encontrado no caminho fornecido:</span><span class="sxs-lookup"><span data-stu-id="799d2-166">Restore dependencies and tools for the `app1` project found in the given path:</span></span>

`dotnet restore ~/projects/app1/app1.csproj`

<span data-ttu-id="799d2-167">Restaure as dependências e as ferramentas para o projeto no diretório atual usando o caminho de arquivo fornecido como a fonte:</span><span class="sxs-lookup"><span data-stu-id="799d2-167">Restore the dependencies and tools for the project in the current directory using the file path provided as the source:</span></span>

`dotnet restore -s c:\packages\mypackages`

<span data-ttu-id="799d2-168">Restaure as dependências e as ferramentas para o projeto no diretório atual usando os caminhos dos dois arquivos fornecidos como fontes:</span><span class="sxs-lookup"><span data-stu-id="799d2-168">Restore the dependencies and tools for the project in the current directory using the two file paths provided as sources:</span></span>

`dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages`

<span data-ttu-id="799d2-169">Restaure as dependências e as ferramentas do projeto no diretório atual e mostre apenas a saída mínima:</span><span class="sxs-lookup"><span data-stu-id="799d2-169">Restore dependencies and tools for the project in the current directory and shows only minimal output:</span></span>

`dotnet restore --verbosity minimal`
