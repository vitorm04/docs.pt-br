---
title: "Comando dotnet migrate – CLI do .NET Core"
description: "O comando dotnet migrate migra um projeto e todas as suas dependências."
author: mairaw
ms.author: mairaw
ms.date: 08/14/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.translationtype: HT
ms.sourcegitcommit: a19ab54a6cc44bd7acd1e40a4ca94da52bf14297
ms.openlocfilehash: 674b19f9fc546e057c7b7fa4b024a0b013eda7e5
ms.contentlocale: pt-br
ms.lasthandoff: 08/14/2017

---
# <a name="dotnet-migrate"></a><span data-ttu-id="b51d5-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="b51d5-103">dotnet migrate</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="b51d5-104">Nome</span><span class="sxs-lookup"><span data-stu-id="b51d5-104">Name</span></span>

<span data-ttu-id="b51d5-105">`dotnet migrate` - Migrar um projeto do .NET Core Visualização 2 para um projeto do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b51d5-105">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK 1.0 project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="b51d5-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="b51d5-106">Synopsis</span></span>

`dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [-t|--template-file] [-v|--sdk-package-version] [-x|--xproj-file] [-s|--skip-project-references] [-r|--report-file] [--format-report-file-json] [--skip-backup] [-h|--help]`

## <a name="description"></a><span data-ttu-id="b51d5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b51d5-107">Description</span></span>

<span data-ttu-id="b51d5-108">O comando `dotnet migrate` migra um projeto válido baseado em *project.json* da Visualização 2 para um projeto *csproj* válido do SDK 1.0 do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b51d5-108">The `dotnet migrate` command migrates a valid Preview 2 *project.json*-based project to a valid .NET Core SDK 1.0 *csproj* project.</span></span> 

<span data-ttu-id="b51d5-109">Por padrão, o comando migra o projeto raiz e as referências de projeto que o projeto raiz contém.</span><span class="sxs-lookup"><span data-stu-id="b51d5-109">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="b51d5-110">Esse comportamento é desabilitado usando a opção `--skip-project-references` no tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="b51d5-110">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span> 

<span data-ttu-id="b51d5-111">A migração é executada no seguinte:</span><span class="sxs-lookup"><span data-stu-id="b51d5-111">Migration is performed on the following:</span></span>

* <span data-ttu-id="b51d5-112">Um único projeto, especificando o arquivo *project.json* a ser migrado.</span><span class="sxs-lookup"><span data-stu-id="b51d5-112">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="b51d5-113">Todos os diretórios especificados no arquivo *global.json*, passando um caminho para o arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="b51d5-113">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="b51d5-114">O arquivo *solution.sln*, onde ele migra os projetos referenciados na solução.</span><span class="sxs-lookup"><span data-stu-id="b51d5-114">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="b51d5-115">Em todos os subdiretórios do diretório especificado, recursivamente.</span><span class="sxs-lookup"><span data-stu-id="b51d5-115">On all sub-directories of the given directory recursively.</span></span>

<span data-ttu-id="b51d5-116">O comando `dotnet migrate` mantém o arquivo *project.json* migrado em um diretório `backup`, que será criado se ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="b51d5-116">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="b51d5-117">Esse comportamento pode ser substituído usando a opção `--skip-backup`.</span><span class="sxs-lookup"><span data-stu-id="b51d5-117">This behavior is overriden using the `--skip-backup` option.</span></span>

<span data-ttu-id="b51d5-118">Por padrão, a operação de migração produzirá o estado do processo de migração para a saída padrão (STDOUT).</span><span class="sxs-lookup"><span data-stu-id="b51d5-118">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="b51d5-119">Se você usar a opção `--report-file <REPORT_FILE>`, a saída será salva no arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="b51d5-119">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span> 

<span data-ttu-id="b51d5-120">O comando `dotnet migrate` dá suporte apenas a projetos com base em *project.json* da Visualização 2.</span><span class="sxs-lookup"><span data-stu-id="b51d5-120">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="b51d5-121">Isso significa que você não pode usá-lo para migrar projetos com base em *project.json* de DNX ou Visualização 1 diretamente para projetos de MSBuild/csproj.</span><span class="sxs-lookup"><span data-stu-id="b51d5-121">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="b51d5-122">Primeiro, você precisa migrar manualmente o projeto para um projeto com base em *project.json* de Visualização 2 e, em seguida, usar o comando `dotnet migrate` para migrar o projeto.</span><span class="sxs-lookup"><span data-stu-id="b51d5-122">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="b51d5-123">Arguments</span><span class="sxs-lookup"><span data-stu-id="b51d5-123">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="b51d5-124">O caminho até um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="b51d5-124">The path to one of the following:</span></span>

* <span data-ttu-id="b51d5-125">um arquivo *project.json* a ser migrado.</span><span class="sxs-lookup"><span data-stu-id="b51d5-125">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="b51d5-126">um arquivo *global.json*, ele migrará as pastas especificadas em *global.json*.</span><span class="sxs-lookup"><span data-stu-id="b51d5-126">a *global.json* file, it will migrate the folders specified in *global.json*.</span></span>
* <span data-ttu-id="b51d5-127">um arquivo *solution.sln*, ele migrará os projetos referenciados na solução.</span><span class="sxs-lookup"><span data-stu-id="b51d5-127">a *solution.sln* file, it will migrate the projects referenced in the solution.</span></span>
* <span data-ttu-id="b51d5-128">um diretório para migração, ele procurará recursivamente por arquivos *project.json* para migrar.</span><span class="sxs-lookup"><span data-stu-id="b51d5-128">a directory to migrate, it will recursively search for *project.json* files to migrate.</span></span>

<span data-ttu-id="b51d5-129">Se nada for especificado, o padrão será o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="b51d5-129">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="b51d5-130">Opções</span><span class="sxs-lookup"><span data-stu-id="b51d5-130">Options</span></span>

`-h|--help`

<span data-ttu-id="b51d5-131">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="b51d5-131">Prints out a short help for the command.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="b51d5-132">Arquivo csproj de modelo a ser usado para migração.</span><span class="sxs-lookup"><span data-stu-id="b51d5-132">Template csproj file to use for migration.</span></span> <span data-ttu-id="b51d5-133">Por padrão, o mesmo modelo removido por `dotnet new console` será usado.</span><span class="sxs-lookup"><span data-stu-id="b51d5-133">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="b51d5-134">A versão do pacote do sdk referenciada no aplicativo migrado.</span><span class="sxs-lookup"><span data-stu-id="b51d5-134">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="b51d5-135">O padrão é a versão do SDK no `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="b51d5-135">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="b51d5-136">O caminho para o arquivo xproj a ser usado.</span><span class="sxs-lookup"><span data-stu-id="b51d5-136">The path to the xproj file to use.</span></span> <span data-ttu-id="b51d5-137">Necessário quando há mais de um xproj em um diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="b51d5-137">Required when there is more than one xproj in a project directory.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="b51d5-138">Ignorar referências de projeto migradas.</span><span class="sxs-lookup"><span data-stu-id="b51d5-138">Skip migrating project references.</span></span> <span data-ttu-id="b51d5-139">Por padrão, as referências de projeto são migradas recursivamente.</span><span class="sxs-lookup"><span data-stu-id="b51d5-139">By default, project references are migrated recursively.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="b51d5-140">Relatório de migração de saída em um arquivo além do console.</span><span class="sxs-lookup"><span data-stu-id="b51d5-140">Output migration report to a file in addition to the console.</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="b51d5-141">Arquivo de relatório de migração de saída como JSON em vez de mensagens de usuário.</span><span class="sxs-lookup"><span data-stu-id="b51d5-141">Output migration report file as JSON rather than user messages.</span></span>

`--skip-backup`

<span data-ttu-id="b51d5-142">Ignorar a movimentação de *project.json*, *global.json* e *\*.xproj* para um diretório `backup` após a migração bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="b51d5-142">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

## <a name="examples"></a><span data-ttu-id="b51d5-143">Exemplos</span><span class="sxs-lookup"><span data-stu-id="b51d5-143">Examples</span></span>

<span data-ttu-id="b51d5-144">Migre um projeto no diretório atual e todas as dependências projeto a projeto:</span><span class="sxs-lookup"><span data-stu-id="b51d5-144">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="b51d5-145">Migre todos os projetos incluídos pelo arquivo *global.json*:</span><span class="sxs-lookup"><span data-stu-id="b51d5-145">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="b51d5-146">Migre apenas o projeto atual e não as dependências P2P (projeto a projeto).</span><span class="sxs-lookup"><span data-stu-id="b51d5-146">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="b51d5-147">Além disso, use uma versão específica do SDK:</span><span class="sxs-lookup"><span data-stu-id="b51d5-147">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
