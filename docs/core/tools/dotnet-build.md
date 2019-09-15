---
title: Comando dotnet build
description: O comando dotnet build compila um projeto e todas as suas dependências.
ms.date: 08/08/2019
ms.openlocfilehash: e92555dad2bc76d8c72eca9a30be1d3a8b5924f7
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988531"
---
# <a name="dotnet-build"></a><span data-ttu-id="92c38-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="92c38-103">dotnet build</span></span>

<span data-ttu-id="92c38-104">**Este artigo se aplica a: ✓** SDK do .NET Core 1.x e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="92c38-104">**This article applies to: ✓** .NET Core 1.x SDK and later versions</span></span>

<!-- todo: uncomment when all CLI commands are reviewed
[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]
-->

## <a name="name"></a><span data-ttu-id="92c38-105">Nome</span><span class="sxs-lookup"><span data-stu-id="92c38-105">Name</span></span>

<span data-ttu-id="92c38-106">`dotnet build` – Compila um projeto e todas as suas dependências.</span><span class="sxs-lookup"><span data-stu-id="92c38-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="92c38-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="92c38-107">Synopsis</span></span>

```console
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a><span data-ttu-id="92c38-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="92c38-108">Description</span></span>

<span data-ttu-id="92c38-109">O comando `dotnet build` compila o projeto e suas dependências em um conjunto de binários.</span><span class="sxs-lookup"><span data-stu-id="92c38-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="92c38-110">Os binários incluem o código do projeto em IL (Linguagem Intermediária) com uma extensão *.dll* e arquivos de símbolo usados para depuração com uma extensão *.pdb*.</span><span class="sxs-lookup"><span data-stu-id="92c38-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="92c38-111">Um arquivo JSON de dependências ( *.deps.json*) é produzido listando as dependências do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92c38-111">A dependencies JSON file (*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="92c38-112">Um arquivo *.runtimeconfig.json* é produzido e especifica o tempo de execução compartilhado e sua versão do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92c38-112">A *.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="92c38-113">Se o projeto tiver dependências de terceiros, como bibliotecas do NuGet, elas serão resolvidas no cache NuGet e não estarão disponíveis com a saída de build do projeto.</span><span class="sxs-lookup"><span data-stu-id="92c38-113">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="92c38-114">Com isso em mente, o produto de `dotnet build` não está pronto para ser transferido para outro computador para execução.</span><span class="sxs-lookup"><span data-stu-id="92c38-114">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="92c38-115">Isso é diferente do comportamento do .NET Framework, no qual compilar um projeto executável (um aplicativo) produz uma saída executável em qualquer computador que tenha o .NET Framework instalado.</span><span class="sxs-lookup"><span data-stu-id="92c38-115">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="92c38-116">Para ter uma experiência semelhante com o .NET Core, é necessário usar o comando [dotnet publish](dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="92c38-116">To have a similar experience with .NET Core, you need to use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="92c38-117">Para saber mais, confira [Implantação de aplicativos .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="92c38-117">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="92c38-118">A compilação exige o arquivo *project.assets.json*, que lista as dependências do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="92c38-118">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="92c38-119">O arquivo é criado quando [`dotnet restore`](dotnet-restore.md) é executado.</span><span class="sxs-lookup"><span data-stu-id="92c38-119">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="92c38-120">Sem o arquivo de ativos em vigor, as ferramentas não conseguem resolver os assemblies de referência, o que resulta em erros.</span><span class="sxs-lookup"><span data-stu-id="92c38-120">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="92c38-121">Com o SDK do .NET Core 1.x, você precisava executar explicitamente o `dotnet restore` antes de executar `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="92c38-121">With .NET Core 1.x SDK, you needed to explicitly run the `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="92c38-122">Começando pelo SDK do .NET Core 2.0, o `dotnet restore` é executado implicitamente quando você executa `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="92c38-122">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="92c38-123">Se você deseja desabilitar a restauração implícita ao executar o comando de build, é possível passar a opção `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="92c38-123">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="92c38-124">O fato de o projeto ser executável ou não é determinado pela propriedade `<OutputType>` do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="92c38-124">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="92c38-125">O seguinte exemplo mostra um projeto que produz um código executável:</span><span class="sxs-lookup"><span data-stu-id="92c38-125">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="92c38-126">Para produzir uma biblioteca, omita a propriedade `<OutputType>`.</span><span class="sxs-lookup"><span data-stu-id="92c38-126">To produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="92c38-127">A diferença principal na saída da compilação é que a DLL de IL para uma biblioteca não contém pontos de entrada e não pode ser executada.</span><span class="sxs-lookup"><span data-stu-id="92c38-127">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="92c38-128">MSBuild</span><span class="sxs-lookup"><span data-stu-id="92c38-128">MSBuild</span></span>

<span data-ttu-id="92c38-129">O `dotnet build` usa o MSBuild para compilar o projeto e, portanto, dá suporte a builds paralelos e incrementais.</span><span class="sxs-lookup"><span data-stu-id="92c38-129">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="92c38-130">Para obter mais informações, consulte [Compilações incrementais](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="92c38-130">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="92c38-131">Além das próprias opções, o comando `dotnet build` também aceita opções do MSBuild, como `-p` para configurar propriedades ou `-l` para definir um agente.</span><span class="sxs-lookup"><span data-stu-id="92c38-131">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="92c38-132">Para obter mais informações sobre essas opções, confira a [Referência de linha de comando do MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="92c38-132">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="92c38-133">Ou você também pode usar o comando [dotnet msbuild](dotnet-msbuild.md).</span><span class="sxs-lookup"><span data-stu-id="92c38-133">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="92c38-134">A execução de `dotnet build` é equivalente a `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="92c38-134">Running `dotnet build` is equivalent to `dotnet msbuild -restore -target:Build`.</span></span>

## <a name="arguments"></a><span data-ttu-id="92c38-135">Arguments</span><span class="sxs-lookup"><span data-stu-id="92c38-135">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="92c38-136">O arquivo de projeto ou solução a ser compilado.</span><span class="sxs-lookup"><span data-stu-id="92c38-136">The project or solution file to build.</span></span> <span data-ttu-id="92c38-137">Se um arquivo de solução ou projeto não for especificado, o MSBuild pesquisará o diretório de trabalho atual em busca de um arquivo que tenha uma extensão terminada em *proj* ou *sln* e usará esse arquivo.</span><span class="sxs-lookup"><span data-stu-id="92c38-137">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="92c38-138">Opções</span><span class="sxs-lookup"><span data-stu-id="92c38-138">Options</span></span>

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="92c38-139">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="92c38-139">Defines the build configuration.</span></span> <span data-ttu-id="92c38-140">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="92c38-140">The default value is `Debug`.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="92c38-141">Compila para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="92c38-141">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="92c38-142">A estrutura precisa ser definida no [arquivo de projeto](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="92c38-142">The framework must be defined in the [project file](csproj.md).</span></span>

* **`--force`**

  <span data-ttu-id="92c38-143">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="92c38-143">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="92c38-144">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="92c38-144">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span> <span data-ttu-id="92c38-145">Disponível desde o SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="92c38-145">Available since .NET Core 2.0 SDK.</span></span>

* **`-h|--help`**

  <span data-ttu-id="92c38-146">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="92c38-146">Prints out a short help for the command.</span></span>

* **`--interactive`**

  <span data-ttu-id="92c38-147">Permite que o comando pare e aguarde entrada ou ação do usuário.</span><span class="sxs-lookup"><span data-stu-id="92c38-147">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="92c38-148">Por exemplo, para concluir a autenticação.</span><span class="sxs-lookup"><span data-stu-id="92c38-148">For example, to complete authentication.</span></span> <span data-ttu-id="92c38-149">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="92c38-149">Available since .NET Core 3.0 SDK.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="92c38-150">Ignora as referências P2P (projeto a projeto) e compila apenas o projeto raiz especificado.</span><span class="sxs-lookup"><span data-stu-id="92c38-150">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

* **`--no-incremental`**

  <span data-ttu-id="92c38-151">Marca o build como não segura para build incremental.</span><span class="sxs-lookup"><span data-stu-id="92c38-151">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="92c38-152">Esse sinalizador desativa a compilação incremental e força uma nova recompilação do grafo de dependência do projeto.</span><span class="sxs-lookup"><span data-stu-id="92c38-152">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

* **`--no-restore`**

  <span data-ttu-id="92c38-153">Não executa uma restauração implícita durante o build.</span><span class="sxs-lookup"><span data-stu-id="92c38-153">Doesn't execute an implicit restore during build.</span></span> <span data-ttu-id="92c38-154">Disponível desde o SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="92c38-154">Available since .NET Core 2.0 SDK.</span></span>

* **`--nologo`**

  <span data-ttu-id="92c38-155">Não exibe a faixa de inicialização nem a mensagem de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="92c38-155">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="92c38-156">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="92c38-156">Available since .NET Core 3.0 SDK.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="92c38-157">Diretório no qual os binários compilados são colocados.</span><span class="sxs-lookup"><span data-stu-id="92c38-157">Directory in which to place the built binaries.</span></span> <span data-ttu-id="92c38-158">Você também precisa definir `--framework` ao especificar essa opção.</span><span class="sxs-lookup"><span data-stu-id="92c38-158">You also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="92c38-159">Se não for especificado, o caminho padrão será `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="92c38-159">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="92c38-160">Especifica o tempo de execução de destino.</span><span class="sxs-lookup"><span data-stu-id="92c38-160">Specifies the target runtime.</span></span> <span data-ttu-id="92c38-161">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="92c38-161">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="92c38-162">Define o nível de detalhamento do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="92c38-162">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="92c38-163">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="92c38-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="92c38-164">O padrão é `minimal`.</span><span class="sxs-lookup"><span data-stu-id="92c38-164">The default is `minimal`.</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="92c38-165">Define o valor da propriedade `$(VersionSuffix)` a ser usada ao compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="92c38-165">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="92c38-166">Isso funcionará apenas se a propriedade `$(Version)` não estiver definida.</span><span class="sxs-lookup"><span data-stu-id="92c38-166">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="92c38-167">Em seguida, `$(Version)` é definido como o `$(VersionPrefix)` combinado com o `$(VersionSuffix)`, separado por um traço.</span><span class="sxs-lookup"><span data-stu-id="92c38-167">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="92c38-168">Exemplos</span><span class="sxs-lookup"><span data-stu-id="92c38-168">Examples</span></span>

* <span data-ttu-id="92c38-169">Compile um projeto e suas dependências:</span><span class="sxs-lookup"><span data-stu-id="92c38-169">Build a project and its dependencies:</span></span>

  ```console
  dotnet build
  ```

* <span data-ttu-id="92c38-170">Compile um projeto e suas dependências usando a configuração da Versão:</span><span class="sxs-lookup"><span data-stu-id="92c38-170">Build a project and its dependencies using Release configuration:</span></span>

  ```console
  dotnet build --configuration Release
  ```

* <span data-ttu-id="92c38-171">Compile um projeto e suas dependências para um tempo de execução específico (no exemplo, Ubuntu 18.04):</span><span class="sxs-lookup"><span data-stu-id="92c38-171">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```console
  dotnet build --runtime ubuntu.18.04-x64
  ```

* <span data-ttu-id="92c38-172">Compile o projeto e use a fonte do pacote NuGet especificada durante a operação de restauração (SDK do .NET Core 2.0 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="92c38-172">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```console
  dotnet build --source c:\packages\mypackages
  ```

* <span data-ttu-id="92c38-173">Compile o projeto e defina a versão 1.2.3.4 como um parâmetro de compilação usando a `-p` [opção MSBuild](#msbuild):</span><span class="sxs-lookup"><span data-stu-id="92c38-173">Build the project and set version 1.2.3.4 as a build parameter using the `-p` [MSBuild option](#msbuild):</span></span>

  ```console
  dotnet build -p:Version=1.2.3.4
  ```
