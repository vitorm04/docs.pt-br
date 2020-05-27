---
title: Comando dotnet build
description: O comando dotnet build compila um projeto e todas as suas dependências.
ms.date: 02/14/2020
ms.openlocfilehash: 5375df61dbf8e9b4db8772b0e2767e9bca0bb254
ms.sourcegitcommit: e5772b3ddcc114c80b4c9767ffdb3f6c7fad8f05
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/26/2020
ms.locfileid: "83840904"
---
# <a name="dotnet-build"></a><span data-ttu-id="99160-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="99160-103">dotnet build</span></span>

<span data-ttu-id="99160-104">**Este artigo aplica-se a:** ✔️ SDK do .NET Core 2. x e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="99160-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="99160-105">Nome</span><span class="sxs-lookup"><span data-stu-id="99160-105">Name</span></span>

<span data-ttu-id="99160-106">`dotnet build` – Compila um projeto e todas as suas dependências.</span><span class="sxs-lookup"><span data-stu-id="99160-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="99160-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="99160-107">Synopsis</span></span>

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive] [--no-dependencies]
    [--no-incremental] [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [-v|--verbosity <LEVEL>] [--version-suffix <VERSION_SUFFIX>]

dotnet build -h|--help
```

## <a name="description"></a><span data-ttu-id="99160-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="99160-108">Description</span></span>

<span data-ttu-id="99160-109">O comando `dotnet build` compila o projeto e suas dependências em um conjunto de binários.</span><span class="sxs-lookup"><span data-stu-id="99160-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="99160-110">Os binários incluem o código do projeto em arquivos de IL (linguagem intermediária) com uma extensão *. dll* .</span><span class="sxs-lookup"><span data-stu-id="99160-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension.</span></span>  <span data-ttu-id="99160-111">Dependendo do tipo de projeto e das configurações, outros arquivos podem ser incluídos, como:</span><span class="sxs-lookup"><span data-stu-id="99160-111">Depending on the project type and settings, other files may be included, such as:</span></span>

- <span data-ttu-id="99160-112">Um executável que pode ser usado para executar o aplicativo, se o tipo de projeto for um executável direcionado ao .NET Core 3,0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="99160-112">An executable that can be used to run the application, if the project type is an executable targeting .NET Core 3.0 or later.</span></span>
- <span data-ttu-id="99160-113">Arquivos de símbolo usados para depuração com uma extensão *. pdb* .</span><span class="sxs-lookup"><span data-stu-id="99160-113">Symbol files used for debugging with a *.pdb* extension.</span></span>
- <span data-ttu-id="99160-114">Um arquivo *. deps. JSON* , que lista as dependências do aplicativo ou da biblioteca.</span><span class="sxs-lookup"><span data-stu-id="99160-114">A *.deps.json* file, which lists the dependencies of the application or library.</span></span>
- <span data-ttu-id="99160-115">Um arquivo *. runtimeconfig. JSON* , que especifica o tempo de execução compartilhado e sua versão para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="99160-115">A *.runtimeconfig.json* file, which specifies the shared runtime and its version for an application.</span></span>
- <span data-ttu-id="99160-116">Outras bibliotecas das quais o projeto depende (por meio de referências de projeto ou referências de pacote NuGet).</span><span class="sxs-lookup"><span data-stu-id="99160-116">Other libraries that the project depends on (via project references or NuGet package references).</span></span>

<span data-ttu-id="99160-117">Para projetos executáveis que visam versões anteriores ao .NET Core 3,0, as dependências de biblioteca do NuGet normalmente não são copiadas para a pasta de saída.</span><span class="sxs-lookup"><span data-stu-id="99160-117">For executable projects targeting versions earlier than .NET Core 3.0, library dependencies from NuGet are typically NOT copied to the output folder.</span></span>  <span data-ttu-id="99160-118">Eles são resolvidos na pasta de pacotes globais do NuGet em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="99160-118">They're resolved from the NuGet global packages folder at run time.</span></span> <span data-ttu-id="99160-119">Com isso em mente, o produto de `dotnet build` não está pronto para ser transferido para outro computador para execução.</span><span class="sxs-lookup"><span data-stu-id="99160-119">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="99160-120">Para criar uma versão do aplicativo que pode ser implantada, você precisa publicá-la (por exemplo, com o comando [dotnet Publish](dotnet-publish.md) ).</span><span class="sxs-lookup"><span data-stu-id="99160-120">To create a version of the application that can be deployed, you need to publish it (for example, with the [dotnet publish](dotnet-publish.md) command).</span></span> <span data-ttu-id="99160-121">Para saber mais, confira [Implantação de aplicativos .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="99160-121">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="99160-122">Para projetos executáveis destinados ao .NET Core 3,0 e posterior, as dependências de biblioteca são copiadas para a pasta de saída.</span><span class="sxs-lookup"><span data-stu-id="99160-122">For executable projects targeting .NET Core 3.0 and later, library dependencies are copied to the output folder.</span></span> <span data-ttu-id="99160-123">Isso significa que, se não houver nenhuma outra lógica específica de publicação (como os projetos Web têm), a saída da compilação deverá ser implantável.</span><span class="sxs-lookup"><span data-stu-id="99160-123">This means that if there isn't any other publish-specific logic (such as Web projects have), the build output should be deployable.</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="99160-124">Restauração implícita</span><span class="sxs-lookup"><span data-stu-id="99160-124">Implicit restore</span></span>

<span data-ttu-id="99160-125">A compilação exige o arquivo *project.assets.json*, que lista as dependências do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="99160-125">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="99160-126">O arquivo é criado quando [`dotnet restore`](dotnet-restore.md) é executado.</span><span class="sxs-lookup"><span data-stu-id="99160-126">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="99160-127">Sem o arquivo de ativos em vigor, as ferramentas não conseguem resolver os assemblies de referência, o que resulta em erros.</span><span class="sxs-lookup"><span data-stu-id="99160-127">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

### <a name="executable-or-library-output"></a><span data-ttu-id="99160-128">Saída de biblioteca ou executável</span><span class="sxs-lookup"><span data-stu-id="99160-128">Executable or library output</span></span>

<span data-ttu-id="99160-129">O fato de o projeto ser executável ou não é determinado pela propriedade `<OutputType>` do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="99160-129">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="99160-130">O seguinte exemplo mostra um projeto que produz um código executável:</span><span class="sxs-lookup"><span data-stu-id="99160-130">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="99160-131">Para produzir uma biblioteca, omita a `<OutputType>` propriedade ou altere seu valor para `Library` .</span><span class="sxs-lookup"><span data-stu-id="99160-131">To produce a library, omit the `<OutputType>` property or change its value to `Library`.</span></span> <span data-ttu-id="99160-132">A DLL de IL para uma biblioteca não contém pontos de entrada e não pode ser executada.</span><span class="sxs-lookup"><span data-stu-id="99160-132">The IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="99160-133">MSBuild</span><span class="sxs-lookup"><span data-stu-id="99160-133">MSBuild</span></span>

<span data-ttu-id="99160-134">O `dotnet build` usa o MSBuild para compilar o projeto e, portanto, dá suporte a builds paralelos e incrementais.</span><span class="sxs-lookup"><span data-stu-id="99160-134">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="99160-135">Para obter mais informações, consulte [Compilações incrementais](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="99160-135">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="99160-136">Além das próprias opções, o comando `dotnet build` também aceita opções do MSBuild, como `-p` para configurar propriedades ou `-l` para definir um agente.</span><span class="sxs-lookup"><span data-stu-id="99160-136">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="99160-137">Para obter mais informações sobre essas opções, confira a [Referência de linha de comando do MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="99160-137">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="99160-138">Ou você também pode usar o comando [dotnet msbuild](dotnet-msbuild.md).</span><span class="sxs-lookup"><span data-stu-id="99160-138">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="99160-139">A execução `dotnet build` é equivalente à execução `dotnet msbuild -restore` ; no entanto, o detalhamento padrão da saída é diferente.</span><span class="sxs-lookup"><span data-stu-id="99160-139">Running `dotnet build` is equivalent to running `dotnet msbuild -restore`; however, the default verbosity of the output is different.</span></span>

## <a name="arguments"></a><span data-ttu-id="99160-140">Argumentos</span><span class="sxs-lookup"><span data-stu-id="99160-140">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="99160-141">O arquivo de projeto ou solução a ser compilado.</span><span class="sxs-lookup"><span data-stu-id="99160-141">The project or solution file to build.</span></span> <span data-ttu-id="99160-142">Se um arquivo de solução ou projeto não for especificado, o MSBuild pesquisará o diretório de trabalho atual em busca de um arquivo que tenha uma extensão terminada em *proj* ou *sln* e usará esse arquivo.</span><span class="sxs-lookup"><span data-stu-id="99160-142">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="99160-143">Opções</span><span class="sxs-lookup"><span data-stu-id="99160-143">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="99160-144">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="99160-144">Defines the build configuration.</span></span> <span data-ttu-id="99160-145">O padrão para a maioria dos projetos é `Debug` , mas você pode substituir as definições de configuração de compilação em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="99160-145">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="99160-146">Compila para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="99160-146">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="99160-147">A estrutura precisa ser definida no [arquivo de projeto](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="99160-147">The framework must be defined in the [project file](csproj.md).</span></span>

- **`--force`**

  <span data-ttu-id="99160-148">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="99160-148">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="99160-149">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="99160-149">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="99160-150">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="99160-150">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="99160-151">Permite que o comando pare e aguarde entrada ou ação do usuário.</span><span class="sxs-lookup"><span data-stu-id="99160-151">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="99160-152">Por exemplo, para concluir a autenticação.</span><span class="sxs-lookup"><span data-stu-id="99160-152">For example, to complete authentication.</span></span> <span data-ttu-id="99160-153">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="99160-153">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="99160-154">Ignora as referências P2P (projeto a projeto) e compila apenas o projeto raiz especificado.</span><span class="sxs-lookup"><span data-stu-id="99160-154">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

- **`--no-incremental`**

  <span data-ttu-id="99160-155">Marca o build como não segura para build incremental.</span><span class="sxs-lookup"><span data-stu-id="99160-155">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="99160-156">Esse sinalizador desativa a compilação incremental e força uma nova recompilação do grafo de dependência do projeto.</span><span class="sxs-lookup"><span data-stu-id="99160-156">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

- **`--no-restore`**

  <span data-ttu-id="99160-157">Não executa uma restauração implícita durante o build.</span><span class="sxs-lookup"><span data-stu-id="99160-157">Doesn't execute an implicit restore during build.</span></span>

- **`--nologo`**

  <span data-ttu-id="99160-158">Não exibe a faixa de inicialização nem a mensagem de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="99160-158">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="99160-159">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="99160-159">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="99160-160">Diretório no qual os binários compilados são colocados.</span><span class="sxs-lookup"><span data-stu-id="99160-160">Directory in which to place the built binaries.</span></span> <span data-ttu-id="99160-161">Se não for especificado, o caminho padrão será `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="99160-161">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="99160-162">Para projetos com várias estruturas de destino (por meio da `TargetFrameworks` Propriedade), também é necessário definir `--framework` quando você especifica essa opção.</span><span class="sxs-lookup"><span data-stu-id="99160-162">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="99160-163">Especifica o runtime de destino.</span><span class="sxs-lookup"><span data-stu-id="99160-163">Specifies the target runtime.</span></span> <span data-ttu-id="99160-164">Para obter uma lista de RIDs (Identificadores de Runtime), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="99160-164">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="99160-165">O URI da origem do pacote NuGet a ser usado durante a operação de restauração.</span><span class="sxs-lookup"><span data-stu-id="99160-165">The URI of the NuGet package source to use during the restore operation.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="99160-166">Define o nível de detalhamento do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="99160-166">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="99160-167">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="99160-167">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="99160-168">O padrão é `minimal`.</span><span class="sxs-lookup"><span data-stu-id="99160-168">The default is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="99160-169">Define o valor da propriedade `$(VersionSuffix)` a ser usada ao compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="99160-169">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="99160-170">Isso funcionará apenas se a propriedade `$(Version)` não estiver definida.</span><span class="sxs-lookup"><span data-stu-id="99160-170">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="99160-171">Em seguida, `$(Version)` é definido como o `$(VersionPrefix)` combinado com o `$(VersionSuffix)`, separado por um traço.</span><span class="sxs-lookup"><span data-stu-id="99160-171">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="99160-172">Exemplos</span><span class="sxs-lookup"><span data-stu-id="99160-172">Examples</span></span>

- <span data-ttu-id="99160-173">Compile um projeto e suas dependências:</span><span class="sxs-lookup"><span data-stu-id="99160-173">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet build
  ```

- <span data-ttu-id="99160-174">Compile um projeto e suas dependências usando a configuração da Versão:</span><span class="sxs-lookup"><span data-stu-id="99160-174">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet build --configuration Release
  ```

- <span data-ttu-id="99160-175">Compile um projeto e suas dependências para um runtime específico (no exemplo, Ubuntu 18.04):</span><span class="sxs-lookup"><span data-stu-id="99160-175">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- <span data-ttu-id="99160-176">Compile o projeto e use a fonte do pacote NuGet especificada durante a operação de restauração (SDK do .NET Core 2.0 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="99160-176">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- <span data-ttu-id="99160-177">Compile o projeto e defina a versão 1.2.3.4 como um parâmetro de compilação usando a `-p` [opção MSBuild](#msbuild):</span><span class="sxs-lookup"><span data-stu-id="99160-177">Build the project and set version 1.2.3.4 as a build parameter using the `-p` [MSBuild option](#msbuild):</span></span>

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
