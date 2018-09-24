---
title: Comando dotnet build – CLI do .NET Core
description: O comando dotnet build compila um projeto e todas as suas dependências.
author: mairaw
ms.author: mairaw
ms.date: 05/25/2018
ms.openlocfilehash: da33647e583af8441218f64fb8ac76d5de3cee38
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2018
ms.locfileid: "46580103"
---
# <a name="dotnet-build"></a><span data-ttu-id="92ca6-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="92ca6-103">dotnet build</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="92ca6-104">Nome</span><span class="sxs-lookup"><span data-stu-id="92ca6-104">Name</span></span>

<span data-ttu-id="92ca6-105">`dotnet build` – Compila um projeto e todas as suas dependências.</span><span class="sxs-lookup"><span data-stu-id="92ca6-105">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="92ca6-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="92ca6-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="92ca6-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="92ca6-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet build [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--no-dependencies] [--no-incremental]
    [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet build [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="92ca6-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="92ca6-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet build [<PROJECT>] [-c|--configuration] [-f|--framework] [--no-dependencies] [--no-incremental] [-o|--output]
    [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet build [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="92ca6-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="92ca6-109">Description</span></span>

<span data-ttu-id="92ca6-110">O comando `dotnet build` compila o projeto e suas dependências em um conjunto de binários.</span><span class="sxs-lookup"><span data-stu-id="92ca6-110">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="92ca6-111">Os binários incluem o código do projeto em IL (Linguagem Intermediária) com uma extensão *.dll* e arquivos de símbolo usados para depuração com uma extensão *.pdb*.</span><span class="sxs-lookup"><span data-stu-id="92ca6-111">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="92ca6-112">Um arquivo JSON de dependências (*\*.deps.json*) é produzido listando as dependências do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92ca6-112">A dependencies JSON file (*\*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="92ca6-113">O arquivo *\*.runtimeconfig.json* é produzido, especificando o tempo de execução compartilhado e sua versão do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92ca6-113">A *\*.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="92ca6-114">Se o projeto tiver dependências de terceiros, como bibliotecas do NuGet, elas serão resolvidas no cache NuGet e não estarão disponíveis com a saída de build do projeto.</span><span class="sxs-lookup"><span data-stu-id="92ca6-114">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="92ca6-115">Com isso em mente, o produto de `dotnet build` não está pronto para ser transferido para outro computador para execução.</span><span class="sxs-lookup"><span data-stu-id="92ca6-115">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="92ca6-116">Isso é diferente do comportamento do .NET Framework, no qual compilar um projeto executável (um aplicativo) produz uma saída executável em qualquer computador que tenha o .NET Framework instalado.</span><span class="sxs-lookup"><span data-stu-id="92ca6-116">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="92ca6-117">Para ter uma experiência semelhante com o .NET Core, é necessário usar o comando [dotnet publish](dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="92ca6-117">To have a similar experience with .NET Core, you need to use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="92ca6-118">Para saber mais, confira [Implantação de aplicativos .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="92ca6-118">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="92ca6-119">A compilação exige o arquivo *project.assets.json*, que lista as dependências do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92ca6-119">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="92ca6-120">O arquivo é criado quando [`dotnet restore`](dotnet-restore.md) é executado.</span><span class="sxs-lookup"><span data-stu-id="92ca6-120">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="92ca6-121">Sem o arquivo de ativos, as ferramentas não conseguem resolver os assemblies de referência, o que resulta em erros.</span><span class="sxs-lookup"><span data-stu-id="92ca6-121">Without the assets file in place, the tooling cannot resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="92ca6-122">Com o SDK do .NET Core 1.x, você precisava executar explicitamente o `dotnet restore` antes de executar `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="92ca6-122">With .NET Core 1.x SDK, you needed to explicitly run the `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="92ca6-123">Começando pelo SDK do .NET Core 2.0, o `dotnet restore` é executado implicitamente quando você executa `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="92ca6-123">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="92ca6-124">Se você deseja desabilitar a restauração implícita ao executar o comando de build, é possível passar a opção `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="92ca6-124">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="92ca6-125">O `dotnet build` usa o MSBuild para compilar o projeto e, portanto, dá suporte a builds paralelos e incrementais.</span><span class="sxs-lookup"><span data-stu-id="92ca6-125">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="92ca6-126">Para obter mais informações, consulte [Compilações incrementais](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="92ca6-126">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="92ca6-127">Além das próprias opções, o comando `dotnet build` também aceita opções do MSBuild, como `-p` para configurar propriedades ou `-l` para definir um agente.</span><span class="sxs-lookup"><span data-stu-id="92ca6-127">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="92ca6-128">Para obter mais informações sobre essas opções, confira a [Referência de linha de comando do MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="92ca6-128">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span>

<span data-ttu-id="92ca6-129">O fato de o projeto ser executável ou não é determinado pela propriedade `<OutputType>` do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="92ca6-129">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="92ca6-130">O seguinte exemplo mostra um projeto que produz um código executável:</span><span class="sxs-lookup"><span data-stu-id="92ca6-130">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="92ca6-131">Para produzir uma biblioteca, omita a propriedade `<OutputType>`.</span><span class="sxs-lookup"><span data-stu-id="92ca6-131">In order to produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="92ca6-132">A diferença principal na saída da compilação é que a DLL de IL para uma biblioteca não contém pontos de entrada e não pode ser executada.</span><span class="sxs-lookup"><span data-stu-id="92ca6-132">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

## <a name="arguments"></a><span data-ttu-id="92ca6-133">Arguments</span><span class="sxs-lookup"><span data-stu-id="92ca6-133">Arguments</span></span>

`PROJECT`

<span data-ttu-id="92ca6-134">O arquivo de projeto a ser compilado.</span><span class="sxs-lookup"><span data-stu-id="92ca6-134">The project file to build.</span></span> <span data-ttu-id="92ca6-135">Se um arquivo de projeto não for especificado, o MSBuild pesquisará o diretório de trabalho atual em busca de um arquivo que tem uma extensão de arquivo que termina em *proj* e que usa esse arquivo.</span><span class="sxs-lookup"><span data-stu-id="92ca6-135">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="92ca6-136">Opções</span><span class="sxs-lookup"><span data-stu-id="92ca6-136">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="92ca6-137">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="92ca6-137">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="92ca6-138">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="92ca6-138">Defines the build configuration.</span></span> <span data-ttu-id="92ca6-139">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="92ca6-139">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="92ca6-140">Compila para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="92ca6-140">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="92ca6-141">A estrutura precisa ser definida no [arquivo de projeto](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="92ca6-141">The framework must be defined in the [project file](csproj.md).</span></span>

`--force`

<span data-ttu-id="92ca6-142">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="92ca6-142">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="92ca6-143">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="92ca6-143">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="92ca6-144">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="92ca6-144">Prints out a short help for the command.</span></span>

`--no-dependencies`

<span data-ttu-id="92ca6-145">Ignora as referências P2P (projeto a projeto) e compila apenas o projeto raiz especificado.</span><span class="sxs-lookup"><span data-stu-id="92ca6-145">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

`--no-incremental`

<span data-ttu-id="92ca6-146">Marca o build como não segura para build incremental.</span><span class="sxs-lookup"><span data-stu-id="92ca6-146">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="92ca6-147">Esse sinalizador desativa a compilação incremental e força uma nova recompilação do grafo de dependência do projeto.</span><span class="sxs-lookup"><span data-stu-id="92ca6-147">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

`--no-restore`

<span data-ttu-id="92ca6-148">Não executa uma restauração implícita durante o build.</span><span class="sxs-lookup"><span data-stu-id="92ca6-148">Doesn't execute an implicit restore during build.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="92ca6-149">Diretório no qual os binários compilados são colocados.</span><span class="sxs-lookup"><span data-stu-id="92ca6-149">Directory in which to place the built binaries.</span></span> <span data-ttu-id="92ca6-150">Você também precisa definir `--framework` ao especificar essa opção.</span><span class="sxs-lookup"><span data-stu-id="92ca6-150">You also need to define `--framework` when you specify this option.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="92ca6-151">Especifica o tempo de execução de destino.</span><span class="sxs-lookup"><span data-stu-id="92ca6-151">Specifies the target runtime.</span></span> <span data-ttu-id="92ca6-152">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="92ca6-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="92ca6-153">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="92ca6-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="92ca6-154">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="92ca6-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="92ca6-155">Define o sufixo da versão para um asterisco (`*`) no campo de versão do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="92ca6-155">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="92ca6-156">O formato segue as diretrizes de versão do NuGet.</span><span class="sxs-lookup"><span data-stu-id="92ca6-156">The format follows NuGet's version guidelines.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="92ca6-157">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="92ca6-157">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="92ca6-158">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="92ca6-158">Defines the build configuration.</span></span> <span data-ttu-id="92ca6-159">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="92ca6-159">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="92ca6-160">Compila para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="92ca6-160">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="92ca6-161">A estrutura precisa ser definida no [arquivo de projeto](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="92ca6-161">The framework must be defined in the [project file](csproj.md).</span></span>

`-h|--help`

<span data-ttu-id="92ca6-162">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="92ca6-162">Prints out a short help for the command.</span></span>

`--no-dependencies`

<span data-ttu-id="92ca6-163">Ignora as referências P2P (projeto a projeto) e compila apenas o projeto raiz especificado.</span><span class="sxs-lookup"><span data-stu-id="92ca6-163">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

`--no-incremental`

<span data-ttu-id="92ca6-164">Marca o build como não segura para build incremental.</span><span class="sxs-lookup"><span data-stu-id="92ca6-164">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="92ca6-165">Esse sinalizador desativa a compilação incremental e força uma nova recompilação do grafo de dependência do projeto.</span><span class="sxs-lookup"><span data-stu-id="92ca6-165">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="92ca6-166">Diretório no qual os binários compilados são colocados.</span><span class="sxs-lookup"><span data-stu-id="92ca6-166">Directory in which to place the built binaries.</span></span> <span data-ttu-id="92ca6-167">Você também precisa definir `--framework` ao especificar essa opção.</span><span class="sxs-lookup"><span data-stu-id="92ca6-167">You also need to define `--framework` when you specify this option.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="92ca6-168">Especifica o tempo de execução de destino.</span><span class="sxs-lookup"><span data-stu-id="92ca6-168">Specifies the target runtime.</span></span> <span data-ttu-id="92ca6-169">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="92ca6-169">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="92ca6-170">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="92ca6-170">Sets the verbosity level of the command.</span></span> <span data-ttu-id="92ca6-171">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="92ca6-171">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="92ca6-172">Define o sufixo da versão para um asterisco (`*`) no campo de versão do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="92ca6-172">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="92ca6-173">O formato segue as diretrizes de versão do NuGet.</span><span class="sxs-lookup"><span data-stu-id="92ca6-173">The format follows NuGet's version guidelines.</span></span>

---

## <a name="examples"></a><span data-ttu-id="92ca6-174">Exemplos</span><span class="sxs-lookup"><span data-stu-id="92ca6-174">Examples</span></span>

<span data-ttu-id="92ca6-175">Compile um projeto e suas dependências:</span><span class="sxs-lookup"><span data-stu-id="92ca6-175">Build a project and its dependencies:</span></span>

`dotnet build`

<span data-ttu-id="92ca6-176">Compile um projeto e suas dependências usando a configuração da Versão:</span><span class="sxs-lookup"><span data-stu-id="92ca6-176">Build a project and its dependencies using Release configuration:</span></span>

`dotnet build --configuration Release`

<span data-ttu-id="92ca6-177">Compile um projeto e suas dependências para um tempo de execução específico (nesse exemplo, Ubuntu 16.04):</span><span class="sxs-lookup"><span data-stu-id="92ca6-177">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 16.04):</span></span>

`dotnet build --runtime ubuntu.16.04-x64`

<span data-ttu-id="92ca6-178">Compile o projeto e use a origem do pacote NuGet especificada durante a operação de restauração (SDK do .NET Core 2.0 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="92ca6-178">Build the project and use the specified NuGet package source during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet build --source c:\packages\mypackages`