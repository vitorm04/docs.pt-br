---
title: Comando dotnet migrate
description: O comando dotnet migrate migra um projeto e todas as suas dependências.
ms.date: 05/25/2018
ms.openlocfilehash: 861cd2cb982c6f41baf00a2cbd7e04b26816af76
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65631947"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="979ab-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="979ab-103">dotnet migrate</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="979ab-104">Nome</span><span class="sxs-lookup"><span data-stu-id="979ab-104">Name</span></span>

<span data-ttu-id="979ab-105">`dotnet migrate` - Migrar um projeto do .NET Core Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="979ab-105">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK 1.0 project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="979ab-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="979ab-106">Synopsis</span></span>

```
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json] [-r|--report-file] [-s|--skip-project-references] [--skip-backup] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file]
dotnet migrate [-h|--help]
```

## <a name="description"></a><span data-ttu-id="979ab-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="979ab-107">Description</span></span>

<span data-ttu-id="979ab-108">O comando `dotnet migrate` migra um projeto válido baseado em *project.json* da Visualização 2 para um projeto *csproj* válido do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="979ab-108">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK 1.0 *csproj* project.</span></span>

<span data-ttu-id="979ab-109">Por padrão, o comando migra o projeto raiz e as referências de projeto que o projeto raiz contém.</span><span class="sxs-lookup"><span data-stu-id="979ab-109">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="979ab-110">Esse comportamento é desabilitado usando a opção `--skip-project-references` no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="979ab-110">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="979ab-111">A migração pode ser realizada nos seguintes ativos:</span><span class="sxs-lookup"><span data-stu-id="979ab-111">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="979ab-112">Um único projeto, especificando o arquivo *project.json* a ser migrado.</span><span class="sxs-lookup"><span data-stu-id="979ab-112">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="979ab-113">Todos os diretórios especificados no arquivo *global.json*, passando um caminho para o arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="979ab-113">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="979ab-114">O arquivo *solution.sln*, onde ele migra os projetos referenciados na solução.</span><span class="sxs-lookup"><span data-stu-id="979ab-114">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="979ab-115">Em todos os subdiretórios do diretório especificado, recursivamente.</span><span class="sxs-lookup"><span data-stu-id="979ab-115">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="979ab-116">O comando `dotnet migrate` mantém o arquivo *project.json* migrado em um diretório `backup`, que será criado se ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="979ab-116">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="979ab-117">Esse comportamento é substituído com a opção `--skip-backup`.</span><span class="sxs-lookup"><span data-stu-id="979ab-117">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="979ab-118">Por padrão, a operação de migração produzirá o estado do processo de migração para a saída padrão (STDOUT).</span><span class="sxs-lookup"><span data-stu-id="979ab-118">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="979ab-119">Se você usar a opção `--report-file <REPORT_FILE>`, a saída será salva no arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="979ab-119">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="979ab-120">O comando `dotnet migrate` dá suporte apenas a projetos com base em *project.json* da Visualização 2.</span><span class="sxs-lookup"><span data-stu-id="979ab-120">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="979ab-121">Isso significa que você não pode usá-lo para migrar projetos com base em *project.json* de DNX ou Visualização 1 diretamente para projetos de MSBuild/csproj.</span><span class="sxs-lookup"><span data-stu-id="979ab-121">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="979ab-122">Primeiro, você precisa migrar manualmente o projeto para um projeto com base em *project.json* de Visualização 2 e, em seguida, usar o comando `dotnet migrate` para migrar o projeto.</span><span class="sxs-lookup"><span data-stu-id="979ab-122">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="979ab-123">Arguments</span><span class="sxs-lookup"><span data-stu-id="979ab-123">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="979ab-124">O caminho até um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="979ab-124">The path to one of the following:</span></span>

* <span data-ttu-id="979ab-125">um arquivo *project.json* a ser migrado.</span><span class="sxs-lookup"><span data-stu-id="979ab-125">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="979ab-126">um arquivo *global.json*: as pastas especificadas em *global.json* são migradas.</span><span class="sxs-lookup"><span data-stu-id="979ab-126">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="979ab-127">um arquivo *solution.sln*: os projetos referenciados na solução são migrados.</span><span class="sxs-lookup"><span data-stu-id="979ab-127">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="979ab-128">um diretório a ser migrado: pesquisa recursivamente arquivos *project.json* para fazer a migração dentro do diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="979ab-128">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="979ab-129">Se nada for especificado, o padrão será o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="979ab-129">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="979ab-130">Opções</span><span class="sxs-lookup"><span data-stu-id="979ab-130">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="979ab-131">Arquivo de relatório de migração de saída como JSON em vez de mensagens de usuário.</span><span class="sxs-lookup"><span data-stu-id="979ab-131">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="979ab-132">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="979ab-132">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="979ab-133">Relatório de migração de saída em um arquivo além do console.</span><span class="sxs-lookup"><span data-stu-id="979ab-133">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="979ab-134">Ignorar referências de projeto migradas.</span><span class="sxs-lookup"><span data-stu-id="979ab-134">Skip migrating project references.</span></span> <span data-ttu-id="979ab-135">Por padrão, as referências de projeto são migradas recursivamente.</span><span class="sxs-lookup"><span data-stu-id="979ab-135">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="979ab-136">Ignorar a movimentação de *project.json*, *global.json* e *\*.xproj* para um diretório `backup` após a migração bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="979ab-136">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="979ab-137">Arquivo csproj de modelo a ser usado para migração.</span><span class="sxs-lookup"><span data-stu-id="979ab-137">Template csproj file to use for migration.</span></span> <span data-ttu-id="979ab-138">Por padrão, o mesmo modelo removido por `dotnet new console` será usado.</span><span class="sxs-lookup"><span data-stu-id="979ab-138">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="979ab-139">A versão do pacote do sdk referenciada no aplicativo migrado.</span><span class="sxs-lookup"><span data-stu-id="979ab-139">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="979ab-140">O padrão é a versão do SDK no `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="979ab-140">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="979ab-141">O caminho para o arquivo xproj a ser usado.</span><span class="sxs-lookup"><span data-stu-id="979ab-141">The path to the xproj file to use.</span></span> <span data-ttu-id="979ab-142">Necessário quando há mais de um xproj em um diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="979ab-142">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="979ab-143">Exemplos</span><span class="sxs-lookup"><span data-stu-id="979ab-143">Examples</span></span>

<span data-ttu-id="979ab-144">Migre um projeto no diretório atual e todas as dependências projeto a projeto:</span><span class="sxs-lookup"><span data-stu-id="979ab-144">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="979ab-145">Migre todos os projetos incluídos pelo arquivo *global.json*:</span><span class="sxs-lookup"><span data-stu-id="979ab-145">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="979ab-146">Migre apenas o projeto atual e não as dependências P2P (projeto a projeto).</span><span class="sxs-lookup"><span data-stu-id="979ab-146">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="979ab-147">Além disso, use uma versão específica do SDK:</span><span class="sxs-lookup"><span data-stu-id="979ab-147">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
