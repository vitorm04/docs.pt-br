---
title: "Comando dotnet build – CLI do .NET Core"
description: "O comando dotnet build compila um projeto e todas as suas dependências."
author: mairaw
ms.author: mairaw
ms.date: 03/10/2018
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: e7181f502e2a25b17077366da9d9f071e7e94d33
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="dotnet-build"></a><span data-ttu-id="e0b2a-103">dotnet-build</span><span class="sxs-lookup"><span data-stu-id="e0b2a-103">dotnet-build</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="e0b2a-104">Nome</span><span class="sxs-lookup"><span data-stu-id="e0b2a-104">Name</span></span>

<span data-ttu-id="e0b2a-105">`dotnet build` – Compila um projeto e todas as suas dependências.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-105">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="e0b2a-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="e0b2a-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="e0b2a-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="e0b2a-107">.NET Core 2.x</span></span>](#tab/netcore2x)
```
dotnet build [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--no-dependencies] [--no-incremental]
    [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet build [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="e0b2a-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="e0b2a-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet build [<PROJECT>] [-c|--configuration] [-f|--framework] [--no-dependencies] [--no-incremental] [-o|--output]
    [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet build [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="e0b2a-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="e0b2a-109">Description</span></span>

<span data-ttu-id="e0b2a-110">O comando `dotnet build` compila o projeto e suas dependências em um conjunto de binários.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-110">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="e0b2a-111">Os binários incluem o código do projeto em IL (Linguagem Intermediária) com uma extensão *.dll* e arquivos de símbolo usados para depuração com uma extensão *.pdb*.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-111">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="e0b2a-112">Um arquivo JSON de dependências (*\*.deps.json*) é produzido listando as dependências do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-112">A dependencies JSON file (*\*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="e0b2a-113">O arquivo *\*.runtimeconfig.json* é produzido, especificando o tempo de execução compartilhado e sua versão do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-113">A *\*.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="e0b2a-114">Se o projeto tiver dependências de terceiros, como bibliotecas do NuGet, elas serão resolvidas no cache NuGet e não estarão disponíveis com a saída de build do projeto.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-114">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="e0b2a-115">Com isso em mente, o produto de `dotnet build` não está pronto para ser transferido para outro computador para execução.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-115">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="e0b2a-116">Isso é diferente do comportamento do .NET Framework, no qual compilar um projeto executável (um aplicativo) produz uma saída executável em qualquer computador que tenha o .NET Framework instalado.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-116">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="e0b2a-117">Para ter uma experiência semelhante com o .NET Core, é necessário usar o comando [dotnet publish](dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="e0b2a-117">To have a similar experience with .NET Core, you need to use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="e0b2a-118">Para saber mais, confira [Implantação de aplicativos .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="e0b2a-118">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="e0b2a-119">A compilação exige o arquivo *project.assets.json*, que lista as dependências do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-119">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="e0b2a-120">O arquivo é criado quando [`dotnet restore`](dotnet-restore.md) é executado.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-120">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="e0b2a-121">Sem o arquivo de ativos, as ferramentas não conseguem resolver os assemblies de referência, o que resulta em erros.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-121">Without the assets file in place, the tooling cannot resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="e0b2a-122">Com o SDK do .NET Core 1.x, era necessário executar explicitamente o `dotnet restore` antes de executar `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-122">With .NET Core 1.x SDK, you needed to explicitily run the `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="e0b2a-123">Começando com o SDK do .NET Core 2.0, o `dotnet restore` é executado implicitamente ao executar `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-123">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitily when you run `dotnet build`.</span></span> <span data-ttu-id="e0b2a-124">Se você deseja desabilitar a restauração implícita ao executar o comando de build, é possível passar a opção `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-124">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="e0b2a-125">O `dotnet build` usa o MSBuild para compilar o projeto e, portanto, dá suporte a builds paralelos e incrementais.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-125">`dotnet build` uses MSBuild to build the project; thus, it supports both parallel and incremental builds.</span></span> <span data-ttu-id="e0b2a-126">Para saber mais, veja [Compilações incrementais](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="e0b2a-126">Refer to [Incremental Builds](/visualstudio/msbuild/incremental-builds) for more information.</span></span>

<span data-ttu-id="e0b2a-127">Além das próprias opções, o comando `dotnet build` também aceita opções do MSBuild, como `/p` para configurar propriedades ou `/l` para definir um agente.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-127">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `/p` for setting properties or `/l` to define a logger.</span></span> <span data-ttu-id="e0b2a-128">Saiba mais sobre essas opções na [Referência de linha de comando do MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="e0b2a-128">Learn more about these options in the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> 

<span data-ttu-id="e0b2a-129">O fato de o projeto ser executável ou não é determinado pela propriedade `<OutputType>` do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-129">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="e0b2a-130">O seguinte exemplo mostra um projeto que produzirá um código executável:</span><span class="sxs-lookup"><span data-stu-id="e0b2a-130">The following example shows a project that will produce executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="e0b2a-131">Para produzir uma biblioteca, omita a propriedade `<OutputType>`.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-131">In order to produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="e0b2a-132">A diferença principal na saída da compilação é que a DLL de IL para uma biblioteca não contém pontos de entrada e não pode ser executada.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-132">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span> 

## <a name="arguments"></a><span data-ttu-id="e0b2a-133">Arguments</span><span class="sxs-lookup"><span data-stu-id="e0b2a-133">Arguments</span></span>

`PROJECT`

<span data-ttu-id="e0b2a-134">O arquivo de projeto a ser compilado.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-134">The project file to build.</span></span> <span data-ttu-id="e0b2a-135">Se um arquivo de projeto não for especificado, o MSBuild pesquisará o diretório de trabalho atual em busca de um arquivo que tem uma extensão de arquivo que termina em *proj* e que usa esse arquivo.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-135">If a project file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in *proj* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="e0b2a-136">Opções</span><span class="sxs-lookup"><span data-stu-id="e0b2a-136">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="e0b2a-137">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="e0b2a-137">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="e0b2a-138">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-138">Defines the build configuration.</span></span> <span data-ttu-id="e0b2a-139">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-139">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="e0b2a-140">Compila para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-140">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="e0b2a-141">A estrutura precisa ser definida no [arquivo de projeto](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="e0b2a-141">The framework must be defined in the [project file](csproj.md).</span></span>

`--force`

 <span data-ttu-id="e0b2a-142">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-142">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="e0b2a-143">Isso é equivalente a excluir o arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-143">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="e0b2a-144">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-144">Prints out a short help for the command.</span></span>

`--no-dependencies`

<span data-ttu-id="e0b2a-145">Ignora as referências projeto a projeto (P2P) e só compila o projeto raiz especificado para o build.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-145">Ignores project-to-project (P2P) references and only builds the root project specified to build.</span></span>

`--no-incremental`

<span data-ttu-id="e0b2a-146">Marca o build como não segura para build incremental.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-146">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="e0b2a-147">Isso desativa a compilação incremental e força uma nova recompilação do grafo de dependência de projeto.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-147">This turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

`--no-restore`

<span data-ttu-id="e0b2a-148">Não executa uma restauração implícita durante o build.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-148">Doesn't perform an implicit restore during build.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="e0b2a-149">Diretório no qual os binários compilados são colocados.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-149">Directory in which to place the built binaries.</span></span> <span data-ttu-id="e0b2a-150">Você também precisa definir `--framework` ao especificar essa opção.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-150">You also need to define `--framework` when you specify this option.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="e0b2a-151">Especifica o tempo de execução de destino.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-151">Specifies the target runtime.</span></span> <span data-ttu-id="e0b2a-152">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="e0b2a-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="e0b2a-153">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e0b2a-154">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="e0b2a-155">Define o sufixo da versão para um asterisco (`*`) no campo de versão do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-155">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="e0b2a-156">O formato segue as diretrizes de versão do NuGet.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-156">The format follows NuGet's version guidelines.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="e0b2a-157">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="e0b2a-157">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="e0b2a-158">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-158">Defines the build configuration.</span></span> <span data-ttu-id="e0b2a-159">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-159">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="e0b2a-160">Compila para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-160">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="e0b2a-161">A estrutura precisa ser definida no [arquivo de projeto](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="e0b2a-161">The framework must be defined in the [project file](csproj.md).</span></span>

`-h|--help`

<span data-ttu-id="e0b2a-162">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-162">Prints out a short help for the command.</span></span>

`--no-dependencies`

<span data-ttu-id="e0b2a-163">Ignora as referências projeto a projeto (P2P) e só compila o projeto raiz especificado para o build.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-163">Ignores project-to-project (P2P) references and only builds the root project specified to build.</span></span>

`--no-incremental`

<span data-ttu-id="e0b2a-164">Marca o build como não segura para build incremental.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-164">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="e0b2a-165">Isso desativa a compilação incremental e força uma nova recompilação do gráfico de dependência de projeto.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-165">This turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="e0b2a-166">Diretório no qual os binários compilados são colocados.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-166">Directory in which to place the built binaries.</span></span> <span data-ttu-id="e0b2a-167">Você também precisa definir `--framework` ao especificar essa opção.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-167">You also need to define `--framework` when you specify this option.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="e0b2a-168">Especifica o tempo de execução de destino.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-168">Specifies the target runtime.</span></span> <span data-ttu-id="e0b2a-169">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="e0b2a-169">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="e0b2a-170">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-170">Sets the verbosity level of the command.</span></span> <span data-ttu-id="e0b2a-171">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-171">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="e0b2a-172">Define o sufixo da versão para um asterisco (`*`) no campo de versão do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-172">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="e0b2a-173">O formato segue as diretrizes de versão do NuGet.</span><span class="sxs-lookup"><span data-stu-id="e0b2a-173">The format follows NuGet's version guidelines.</span></span>

---

## <a name="examples"></a><span data-ttu-id="e0b2a-174">Exemplos</span><span class="sxs-lookup"><span data-stu-id="e0b2a-174">Examples</span></span>

<span data-ttu-id="e0b2a-175">Compile um projeto e suas dependências:</span><span class="sxs-lookup"><span data-stu-id="e0b2a-175">Build a project and its dependencies:</span></span>

`dotnet build`

<span data-ttu-id="e0b2a-176">Compile um projeto e suas dependências usando a configuração da Versão:</span><span class="sxs-lookup"><span data-stu-id="e0b2a-176">Build a project and its dependencies using Release configuration:</span></span>

`dotnet build --configuration Release`

<span data-ttu-id="e0b2a-177">Compile um projeto e suas dependências para um tempo de execução específico (nesse exemplo, Ubuntu 16.04):</span><span class="sxs-lookup"><span data-stu-id="e0b2a-177">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 16.04):</span></span>

`dotnet build --runtime ubuntu.16.04-x64`

<span data-ttu-id="e0b2a-178">Compile o projeto e use a origem do pacote NuGet especificada durante a operação de restauração (SDK do .NET Core 2.0 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="e0b2a-178">Build the project and use the specified NuGet package source during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet build --source c:\packages\mypackages`