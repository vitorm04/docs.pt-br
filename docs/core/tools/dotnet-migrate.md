---
title: Comando dotnet migrate
description: O comando dotnet migrate migra um projeto e todas as suas dependências.
ms.date: 02/14/2020
ms.openlocfilehash: 71f587c1bfadd445aca818448bdd5f136f009fe0
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463630"
---
# <a name="dotnet-migrate"></a><span data-ttu-id="1a2a0-103">dotnet migrate</span><span class="sxs-lookup"><span data-stu-id="1a2a0-103">dotnet migrate</span></span>

<span data-ttu-id="1a2a0-104">**Este artigo se aplica a:** ✔️ .NET Core 2.x SDK</span><span class="sxs-lookup"><span data-stu-id="1a2a0-104">**This article applies to:** ✔️ .NET Core 2.x SDK</span></span>

## <a name="name"></a><span data-ttu-id="1a2a0-105">Nome</span><span class="sxs-lookup"><span data-stu-id="1a2a0-105">Name</span></span>

<span data-ttu-id="1a2a0-106">`dotnet migrate` – Migrar um projeto do .NET Core Versão Prévia 2 para um projeto no estilo do SDK do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-106">`dotnet migrate` - Migrates a Preview 2 .NET Core project to a .NET Core SDK-style project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="1a2a0-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="1a2a0-107">Synopsis</span></span>

```dotnetcli
dotnet migrate [<SOLUTION_FILE|PROJECT_DIR>] [--format-report-file-json <REPORT_FILE>]
    [-r|--report-file <REPORT_FILE>] [-s|--skip-project-references [Debug|Release]]
    [--skip-backup] [-t|--template-file <TEMPLATE_FILE>] [-v|--sdk-package-version]
    [-x|--xproj-file]

dotnet migrate -h|--help
```

## <a name="description"></a><span data-ttu-id="1a2a0-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="1a2a0-108">Description</span></span>

<span data-ttu-id="1a2a0-109">Este comando é preterido.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-109">This command is deprecated.</span></span> <span data-ttu-id="1a2a0-110">O `dotnet migrate` comando não está mais disponível a partir do .NET Core 3.0 SDK.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-110">The `dotnet migrate` command is no longer available starting with .NET Core 3.0 SDK.</span></span> <span data-ttu-id="1a2a0-111">Ele só pode migrar um projeto Preview 2 .NET Core para um projeto 1.x .NET Core, que está sem suporte.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-111">It can only migrate a Preview 2 .NET Core project to a 1.x .NET Core project, which is out of support.</span></span>

<span data-ttu-id="1a2a0-112">Por padrão, o comando migra o projeto raiz e as referências de projeto que o projeto raiz contém.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-112">By default, the command migrates the root project and any project references that the root project contains.</span></span> <span data-ttu-id="1a2a0-113">Esse comportamento é desabilitado usando a opção `--skip-project-references` no runtime.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-113">This behavior is disabled using the `--skip-project-references` option at runtime.</span></span>

<span data-ttu-id="1a2a0-114">A migração pode ser realizada nos seguintes ativos:</span><span class="sxs-lookup"><span data-stu-id="1a2a0-114">Migration can be performed on the following assets:</span></span>

* <span data-ttu-id="1a2a0-115">Um único projeto, especificando o arquivo *project.json* a ser migrado.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-115">A single project by specifying the *project.json* file to migrate.</span></span>
* <span data-ttu-id="1a2a0-116">Todos os diretórios especificados no arquivo *global.json*, passando um caminho para o arquivo *global.json*.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-116">All of the directories specified in the *global.json* file by passing in a path to the *global.json* file.</span></span>
* <span data-ttu-id="1a2a0-117">O arquivo *solution.sln*, onde ele migra os projetos referenciados na solução.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-117">A *solution.sln* file, where it migrates the projects referenced in the solution.</span></span>
* <span data-ttu-id="1a2a0-118">Em todos os subdiretórios do diretório especificado, recursivamente.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-118">On all subdirectories of the given directory recursively.</span></span>

<span data-ttu-id="1a2a0-119">O comando `dotnet migrate` mantém o arquivo *project.json* migrado em um diretório `backup`, que será criado se ainda não existir.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-119">The `dotnet migrate` command keeps the migrated *project.json* file inside a `backup` directory, which it creates if the directory doesn't exist.</span></span> <span data-ttu-id="1a2a0-120">Esse comportamento é substituído com a opção `--skip-backup`.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-120">This behavior is overridden using the `--skip-backup` option.</span></span>

<span data-ttu-id="1a2a0-121">Por padrão, a operação de migração produzirá o estado do processo de migração para a saída padrão (STDOUT).</span><span class="sxs-lookup"><span data-stu-id="1a2a0-121">By default, the migration operation outputs the state of the migration process to standard output (STDOUT).</span></span> <span data-ttu-id="1a2a0-122">Se você usar a opção `--report-file <REPORT_FILE>`, a saída será salva no arquivo especificado.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-122">If you use the `--report-file <REPORT_FILE>` option, the output is saved to the file specify.</span></span>

<span data-ttu-id="1a2a0-123">O comando `dotnet migrate` dá suporte apenas a projetos com base em *project.json* da Visualização 2.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-123">The `dotnet migrate` command only supports valid Preview 2 *project.json*-based projects.</span></span> <span data-ttu-id="1a2a0-124">Isso significa que você não pode usá-lo para migrar projetos com base em *project.json* de DNX ou Visualização 1 diretamente para projetos de MSBuild/csproj.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-124">This means that you cannot use it to migrate DNX or Preview 1 *project.json*-based projects directly to MSBuild/csproj projects.</span></span> <span data-ttu-id="1a2a0-125">Primeiro, você precisa migrar manualmente o projeto para um projeto com base em *project.json* de Visualização 2 e, em seguida, usar o comando `dotnet migrate` para migrar o projeto.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-125">You first need to manually migrate the project to a Preview 2 *project.json*-based project and then use the `dotnet migrate` command to migrate the project.</span></span>

## <a name="arguments"></a><span data-ttu-id="1a2a0-126">Argumentos</span><span class="sxs-lookup"><span data-stu-id="1a2a0-126">Arguments</span></span>

`PROJECT_JSON/GLOBAL_JSON/SOLUTION_FILE/PROJECT_DIR`

<span data-ttu-id="1a2a0-127">O caminho até um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="1a2a0-127">The path to one of the following:</span></span>

* <span data-ttu-id="1a2a0-128">um arquivo *project.json* a ser migrado.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-128">a *project.json* file to migrate.</span></span>
* <span data-ttu-id="1a2a0-129">um arquivo *global.json*: as pastas especificadas em *global.json* são migradas.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-129">a *global.json* file: the folders specified in *global.json* are migrated.</span></span>
* <span data-ttu-id="1a2a0-130">um arquivo *solution.sln*: os projetos referenciados na solução são migrados.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-130">a *solution.sln* file: the projects referenced in the solution are migrated.</span></span>
* <span data-ttu-id="1a2a0-131">um diretório a ser migrado: pesquisa recursivamente arquivos *project.json* para fazer a migração dentro do diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-131">a directory to migrate: recursively searches for *project.json* files to migrate inside the specified directory.</span></span>

<span data-ttu-id="1a2a0-132">Se nada for especificado, o padrão será o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-132">Defaults to current directory if nothing is specified.</span></span>

## <a name="options"></a><span data-ttu-id="1a2a0-133">Opções</span><span class="sxs-lookup"><span data-stu-id="1a2a0-133">Options</span></span>

`--format-report-file-json <REPORT_FILE>`

<span data-ttu-id="1a2a0-134">Arquivo de relatório de migração de saída como JSON em vez de mensagens de usuário.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-134">Output migration report file as JSON rather than user messages.</span></span>

`-h|--help`

<span data-ttu-id="1a2a0-135">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-135">Prints out a short help for the command.</span></span>

`-r|--report-file <REPORT_FILE>`

<span data-ttu-id="1a2a0-136">Relatório de migração de saída em um arquivo além do console.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-136">Output migration report to a file in addition to the console.</span></span>

`-s|--skip-project-references [Debug|Release]`

<span data-ttu-id="1a2a0-137">Ignorar referências de projeto migradas.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-137">Skip migrating project references.</span></span> <span data-ttu-id="1a2a0-138">Por padrão, as referências de projeto são migradas recursivamente.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-138">By default, project references are migrated recursively.</span></span>

`--skip-backup`

<span data-ttu-id="1a2a0-139">Ignorar a movimentação de *project.json*, *global.json* e *\*.xproj* para um diretório `backup` após a migração bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-139">Skip moving *project.json*, *global.json*, and *\*.xproj* to a `backup` directory after successful migration.</span></span>

`-t|--template-file <TEMPLATE_FILE>`

<span data-ttu-id="1a2a0-140">Arquivo csproj de modelo a ser usado para migração.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-140">Template csproj file to use for migration.</span></span> <span data-ttu-id="1a2a0-141">Por padrão, o mesmo modelo removido por `dotnet new console` será usado.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-141">By default, the same template as the one dropped by `dotnet new console` is used.</span></span>

`-v|--sdk-package-version <VERSION>`

<span data-ttu-id="1a2a0-142">A versão do pacote do sdk referenciada no aplicativo migrado.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-142">The version of the sdk package that's referenced in the migrated app.</span></span> <span data-ttu-id="1a2a0-143">O padrão é a versão do SDK no `dotnet new`.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-143">The default is the version of the SDK in `dotnet new`.</span></span>

`-x|--xproj-file <FILE>`

<span data-ttu-id="1a2a0-144">O caminho para o arquivo xproj a ser usado.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-144">The path to the xproj file to use.</span></span> <span data-ttu-id="1a2a0-145">Necessário quando há mais de um xproj em um diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="1a2a0-145">Required when there is more than one xproj in a project directory.</span></span>

## <a name="examples"></a><span data-ttu-id="1a2a0-146">Exemplos</span><span class="sxs-lookup"><span data-stu-id="1a2a0-146">Examples</span></span>

<span data-ttu-id="1a2a0-147">Migre um projeto no diretório atual e todas as dependências projeto a projeto:</span><span class="sxs-lookup"><span data-stu-id="1a2a0-147">Migrate a project in the current directory and all of its project-to-project dependencies:</span></span>

`dotnet migrate`

<span data-ttu-id="1a2a0-148">Migre todos os projetos incluídos pelo arquivo *global.json*:</span><span class="sxs-lookup"><span data-stu-id="1a2a0-148">Migrate all projects that *global.json* file includes:</span></span>

`dotnet migrate path/to/global.json`

<span data-ttu-id="1a2a0-149">Migre apenas o projeto atual e não as dependências P2P (projeto a projeto).</span><span class="sxs-lookup"><span data-stu-id="1a2a0-149">Migrate only the current project and no project-to-project (P2P) dependencies.</span></span> <span data-ttu-id="1a2a0-150">Além disso, use uma versão específica do SDK:</span><span class="sxs-lookup"><span data-stu-id="1a2a0-150">Also, use a specific SDK version:</span></span>

`dotnet migrate -s -v 1.0.0-preview4`
