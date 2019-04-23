---
title: Comando dotnet build
description: O comando dotnet build compila um projeto e todas as suas dependências.
ms.date: 12/04/2018
ms.openlocfilehash: 6a701ee371221c780a878e64b996df95f709371f
ms.sourcegitcommit: 438919211260bb415fc8f96ca3eabc33cf2d681d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2019
ms.locfileid: "59612687"
---
# <a name="dotnet-build"></a><span data-ttu-id="0cece-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="0cece-103">dotnet build</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="0cece-104">Nome</span><span class="sxs-lookup"><span data-stu-id="0cece-104">Name</span></span>

<span data-ttu-id="0cece-105">`dotnet build` – Compila um projeto e todas as suas dependências.</span><span class="sxs-lookup"><span data-stu-id="0cece-105">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="0cece-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="0cece-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="0cece-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="0cece-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force] [--no-dependencies] [--no-incremental]
    [--no-restore] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0cece-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="0cece-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--no-dependencies] [--no-incremental] [-o|--output]
    [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="0cece-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="0cece-109">Description</span></span>

<span data-ttu-id="0cece-110">O comando `dotnet build` compila o projeto e suas dependências em um conjunto de binários.</span><span class="sxs-lookup"><span data-stu-id="0cece-110">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="0cece-111">Os binários incluem o código do projeto em IL (Linguagem Intermediária) com uma extensão *.dll* e arquivos de símbolo usados para depuração com uma extensão *.pdb*.</span><span class="sxs-lookup"><span data-stu-id="0cece-111">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension and symbol files used for debugging with a *.pdb* extension.</span></span> <span data-ttu-id="0cece-112">Um arquivo JSON de dependências (*\*.deps.json*) é produzido listando as dependências do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0cece-112">A dependencies JSON file (*\*.deps.json*) is produced that lists the dependencies of the application.</span></span> <span data-ttu-id="0cece-113">O arquivo *\*.runtimeconfig.json* é produzido, especificando o tempo de execução compartilhado e sua versão do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0cece-113">A *\*.runtimeconfig.json* file is produced, which specifies the shared runtime and its version for the application.</span></span>

<span data-ttu-id="0cece-114">Se o projeto tiver dependências de terceiros, como bibliotecas do NuGet, elas serão resolvidas no cache NuGet e não estarão disponíveis com a saída de build do projeto.</span><span class="sxs-lookup"><span data-stu-id="0cece-114">If the project has third-party dependencies, such as libraries from NuGet, they're resolved from the NuGet cache and aren't available with the project's built output.</span></span> <span data-ttu-id="0cece-115">Com isso em mente, o produto de `dotnet build` não está pronto para ser transferido para outro computador para execução.</span><span class="sxs-lookup"><span data-stu-id="0cece-115">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="0cece-116">Isso é diferente do comportamento do .NET Framework, no qual compilar um projeto executável (um aplicativo) produz uma saída executável em qualquer computador que tenha o .NET Framework instalado.</span><span class="sxs-lookup"><span data-stu-id="0cece-116">This is in contrast to the behavior of the .NET Framework in which building an executable project (an application) produces output that's runnable on any machine where the .NET Framework is installed.</span></span> <span data-ttu-id="0cece-117">Para ter uma experiência semelhante com o .NET Core, é necessário usar o comando [dotnet publish](dotnet-publish.md).</span><span class="sxs-lookup"><span data-stu-id="0cece-117">To have a similar experience with .NET Core, you need to use the [dotnet publish](dotnet-publish.md) command.</span></span> <span data-ttu-id="0cece-118">Para saber mais, confira [Implantação de aplicativos .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="0cece-118">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="0cece-119">A compilação exige o arquivo *project.assets.json*, que lista as dependências do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="0cece-119">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="0cece-120">O arquivo é criado quando [`dotnet restore`](dotnet-restore.md) é executado.</span><span class="sxs-lookup"><span data-stu-id="0cece-120">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="0cece-121">Sem o arquivo de ativos, as ferramentas não conseguem resolver os assemblies de referência, o que resulta em erros.</span><span class="sxs-lookup"><span data-stu-id="0cece-121">Without the assets file in place, the tooling cannot resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="0cece-122">Com o SDK do .NET Core 1.x, você precisava executar explicitamente o `dotnet restore` antes de executar `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="0cece-122">With .NET Core 1.x SDK, you needed to explicitly run the `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="0cece-123">Começando pelo SDK do .NET Core 2.0, o `dotnet restore` é executado implicitamente quando você executa `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="0cece-123">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="0cece-124">Se você deseja desabilitar a restauração implícita ao executar o comando de build, é possível passar a opção `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="0cece-124">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="0cece-125">O fato de o projeto ser executável ou não é determinado pela propriedade `<OutputType>` do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="0cece-125">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="0cece-126">O seguinte exemplo mostra um projeto que produz um código executável:</span><span class="sxs-lookup"><span data-stu-id="0cece-126">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="0cece-127">Para produzir uma biblioteca, omita a propriedade `<OutputType>`.</span><span class="sxs-lookup"><span data-stu-id="0cece-127">In order to produce a library, omit the `<OutputType>` property.</span></span> <span data-ttu-id="0cece-128">A diferença principal na saída da compilação é que a DLL de IL para uma biblioteca não contém pontos de entrada e não pode ser executada.</span><span class="sxs-lookup"><span data-stu-id="0cece-128">The main difference in built output is that the IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="0cece-129">MSBuild</span><span class="sxs-lookup"><span data-stu-id="0cece-129">MSBuild</span></span>

<span data-ttu-id="0cece-130">O `dotnet build` usa o MSBuild para compilar o projeto e, portanto, dá suporte a builds paralelos e incrementais.</span><span class="sxs-lookup"><span data-stu-id="0cece-130">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="0cece-131">Para obter mais informações, consulte [Compilações incrementais](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="0cece-131">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="0cece-132">Além das próprias opções, o comando `dotnet build` também aceita opções do MSBuild, como `-p` para configurar propriedades ou `-l` para definir um agente.</span><span class="sxs-lookup"><span data-stu-id="0cece-132">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="0cece-133">Para obter mais informações sobre essas opções, confira a [Referência de linha de comando do MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="0cece-133">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="0cece-134">Ou você também pode usar o comando [dotnet msbuild](dotnet-msbuild.md).</span><span class="sxs-lookup"><span data-stu-id="0cece-134">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="0cece-135">A execução de `dotnet build` é equivalente a `dotnet msbuild -restore -target:Build`.</span><span class="sxs-lookup"><span data-stu-id="0cece-135">Running `dotnet build` is equivalent to `dotnet msbuild -restore -target:Build`.</span></span>

## <a name="arguments"></a><span data-ttu-id="0cece-136">Arguments</span><span class="sxs-lookup"><span data-stu-id="0cece-136">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="0cece-137">O arquivo de projeto ou solução a ser compilado.</span><span class="sxs-lookup"><span data-stu-id="0cece-137">The project or solution file to build.</span></span> <span data-ttu-id="0cece-138">Se um arquivo de projeto não for especificado, o MSBuild pesquisará o diretório de trabalho atual em busca de um arquivo que tenha uma extensão de arquivo que termine em *proj* ou *sln* e usará esse arquivo.</span><span class="sxs-lookup"><span data-stu-id="0cece-138">If a project or solution file is not specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="0cece-139">Opções</span><span class="sxs-lookup"><span data-stu-id="0cece-139">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="0cece-140">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="0cece-140">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="0cece-141">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="0cece-141">Defines the build configuration.</span></span> <span data-ttu-id="0cece-142">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="0cece-142">The default value is `Debug`.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="0cece-143">Compila para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="0cece-143">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="0cece-144">A estrutura precisa ser definida no [arquivo de projeto](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="0cece-144">The framework must be defined in the [project file](csproj.md).</span></span>

* **`--force`**

  <span data-ttu-id="0cece-145">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="0cece-145">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="0cece-146">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="0cece-146">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

* **`-h|--help`**

  <span data-ttu-id="0cece-147">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="0cece-147">Prints out a short help for the command.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="0cece-148">Ignora as referências P2P (projeto a projeto) e compila apenas o projeto raiz especificado.</span><span class="sxs-lookup"><span data-stu-id="0cece-148">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

* **`--no-incremental`**

  <span data-ttu-id="0cece-149">Marca o build como não segura para build incremental.</span><span class="sxs-lookup"><span data-stu-id="0cece-149">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="0cece-150">Esse sinalizador desativa a compilação incremental e força uma nova recompilação do grafo de dependência do projeto.</span><span class="sxs-lookup"><span data-stu-id="0cece-150">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

* **`--no-restore`**

  <span data-ttu-id="0cece-151">Não executa uma restauração implícita durante o build.</span><span class="sxs-lookup"><span data-stu-id="0cece-151">Doesn't execute an implicit restore during build.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="0cece-152">Diretório no qual os binários compilados são colocados.</span><span class="sxs-lookup"><span data-stu-id="0cece-152">Directory in which to place the built binaries.</span></span> <span data-ttu-id="0cece-153">Você também precisa definir `--framework` ao especificar essa opção.</span><span class="sxs-lookup"><span data-stu-id="0cece-153">You also need to define `--framework` when you specify this option.</span></span> <span data-ttu-id="0cece-154">Se não for especificado, o caminho padrão será `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="0cece-154">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="0cece-155">Especifica o tempo de execução de destino.</span><span class="sxs-lookup"><span data-stu-id="0cece-155">Specifies the target runtime.</span></span> <span data-ttu-id="0cece-156">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="0cece-156">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="0cece-157">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="0cece-157">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0cece-158">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="0cece-158">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="0cece-159">Define o sufixo da versão para um asterisco (`*`) no campo de versão do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="0cece-159">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="0cece-160">O formato segue as diretrizes de versão do NuGet.</span><span class="sxs-lookup"><span data-stu-id="0cece-160">The format follows NuGet's version guidelines.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="0cece-161">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="0cece-161">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="0cece-162">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="0cece-162">Defines the build configuration.</span></span> <span data-ttu-id="0cece-163">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="0cece-163">The default value is `Debug`.</span></span>

* **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="0cece-164">Compila para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="0cece-164">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="0cece-165">A estrutura precisa ser definida no [arquivo de projeto](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="0cece-165">The framework must be defined in the [project file](csproj.md).</span></span>

* **`-h|--help`**

  <span data-ttu-id="0cece-166">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="0cece-166">Prints out a short help for the command.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="0cece-167">Ignora as referências P2P (projeto a projeto) e compila apenas o projeto raiz especificado.</span><span class="sxs-lookup"><span data-stu-id="0cece-167">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

* **`--no-incremental`**

  <span data-ttu-id="0cece-168">Marca o build como não segura para build incremental.</span><span class="sxs-lookup"><span data-stu-id="0cece-168">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="0cece-169">Esse sinalizador desativa a compilação incremental e força uma nova recompilação do grafo de dependência do projeto.</span><span class="sxs-lookup"><span data-stu-id="0cece-169">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="0cece-170">Diretório no qual os binários compilados são colocados.</span><span class="sxs-lookup"><span data-stu-id="0cece-170">Directory in which to place the built binaries.</span></span> <span data-ttu-id="0cece-171">Você também precisa definir `--framework` ao especificar essa opção.</span><span class="sxs-lookup"><span data-stu-id="0cece-171">You also need to define `--framework` when you specify this option.</span></span>

* **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="0cece-172">Especifica o tempo de execução de destino.</span><span class="sxs-lookup"><span data-stu-id="0cece-172">Specifies the target runtime.</span></span> <span data-ttu-id="0cece-173">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="0cece-173">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="0cece-174">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="0cece-174">Sets the verbosity level of the command.</span></span> <span data-ttu-id="0cece-175">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="0cece-175">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="0cece-176">Define o sufixo da versão para um asterisco (`*`) no campo de versão do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="0cece-176">Defines the version suffix for an asterisk (`*`) in the version field of the project file.</span></span> <span data-ttu-id="0cece-177">O formato segue as diretrizes de versão do NuGet.</span><span class="sxs-lookup"><span data-stu-id="0cece-177">The format follows NuGet's version guidelines.</span></span>

---

## <a name="examples"></a><span data-ttu-id="0cece-178">Exemplos</span><span class="sxs-lookup"><span data-stu-id="0cece-178">Examples</span></span>

* <span data-ttu-id="0cece-179">Compile um projeto e suas dependências:</span><span class="sxs-lookup"><span data-stu-id="0cece-179">Build a project and its dependencies:</span></span>

  ```console
  dotnet build
  ```

* <span data-ttu-id="0cece-180">Compile um projeto e suas dependências usando a configuração da Versão:</span><span class="sxs-lookup"><span data-stu-id="0cece-180">Build a project and its dependencies using Release configuration:</span></span>

  ```console
  dotnet build --configuration Release
  ```

* <span data-ttu-id="0cece-181">Compile um projeto e suas dependências para um tempo de execução específico (nesse exemplo, Ubuntu 16.04):</span><span class="sxs-lookup"><span data-stu-id="0cece-181">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 16.04):</span></span>

  ```console
  dotnet build --runtime ubuntu.16.04-x64
  ```

* <span data-ttu-id="0cece-182">Compile o projeto e use a fonte do pacote NuGet especificada durante a operação de restauração (SDK do .NET Core 2.0 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="0cece-182">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```console
  dotnet build --source c:\packages\mypackages
  ```

* <span data-ttu-id="0cece-183">Compile o projeto e defina a versão 1.2.3.4 como um parâmetro de compilação:</span><span class="sxs-lookup"><span data-stu-id="0cece-183">Build the project and set 1.2.3.4 version as a build parameter:</span></span>

  ```console
  dotnet build -p:Version=1.2.3.4
  ```