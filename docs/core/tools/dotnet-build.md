---
title: Comando dotnet build
description: O comando dotnet build compila um projeto e todas as suas dependências.
ms.date: 02/14/2020
ms.openlocfilehash: 9f9a78ec0a6a25c54c8a727c05081ce6835514ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "77503767"
---
# <a name="dotnet-build"></a><span data-ttu-id="07ad6-103">dotnet build</span><span class="sxs-lookup"><span data-stu-id="07ad6-103">dotnet build</span></span>

<span data-ttu-id="07ad6-104">**Este artigo se aplica a:** ✔️ .NET Core 2.x SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="07ad6-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="07ad6-105">Nome</span><span class="sxs-lookup"><span data-stu-id="07ad6-105">Name</span></span>

<span data-ttu-id="07ad6-106">`dotnet build` – Compila um projeto e todas as suas dependências.</span><span class="sxs-lookup"><span data-stu-id="07ad6-106">`dotnet build` - Builds a project and all of its dependencies.</span></span>

## <a name="synopsis"></a><span data-ttu-id="07ad6-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="07ad6-107">Synopsis</span></span>

```dotnetcli
dotnet build [<PROJECT>|<SOLUTION>] [-c|--configuration] [-f|--framework] [--force]
    [--interactive] [--no-dependencies] [--no-incremental] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]

dotnet build [-h|--help]
```

## <a name="description"></a><span data-ttu-id="07ad6-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="07ad6-108">Description</span></span>

<span data-ttu-id="07ad6-109">O comando `dotnet build` compila o projeto e suas dependências em um conjunto de binários.</span><span class="sxs-lookup"><span data-stu-id="07ad6-109">The `dotnet build` command builds the project and its dependencies into a set of binaries.</span></span> <span data-ttu-id="07ad6-110">Os binários incluem o código do projeto em arquivos de idioma intermediário (IL) com uma extensão *.dll.*</span><span class="sxs-lookup"><span data-stu-id="07ad6-110">The binaries include the project's code in Intermediate Language (IL) files with a *.dll* extension.</span></span>  <span data-ttu-id="07ad6-111">Dependendo do tipo de projeto e configurações, outros arquivos podem ser incluídos, tais como:</span><span class="sxs-lookup"><span data-stu-id="07ad6-111">Depending on the project type and settings, other files may be included, such as:</span></span>

- <span data-ttu-id="07ad6-112">Um executável que pode ser usado para executar o aplicativo, se o tipo de projeto for um alvo executável .NET Core 3.0 ou posterior.</span><span class="sxs-lookup"><span data-stu-id="07ad6-112">An executable that can be used to run the application, if the project type is an executable targeting .NET Core 3.0 or later.</span></span>
- <span data-ttu-id="07ad6-113">Arquivos de símbolo usados para depuração com uma extensão *.pdb.*</span><span class="sxs-lookup"><span data-stu-id="07ad6-113">Symbol files used for debugging with a *.pdb* extension.</span></span>
- <span data-ttu-id="07ad6-114">Um arquivo *.deps.json,* que lista as dependências do aplicativo ou biblioteca.</span><span class="sxs-lookup"><span data-stu-id="07ad6-114">A *.deps.json* file, which lists the dependencies of the application or library.</span></span>
- <span data-ttu-id="07ad6-115">Um arquivo *.runtimeconfig.json,* que especifica o tempo de execução compartilhado e sua versão para um aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07ad6-115">A *.runtimeconfig.json* file, which specifies the shared runtime and its version for an application.</span></span>
- <span data-ttu-id="07ad6-116">Outras bibliotecas das as qual o projeto depende (através de referências de projeto ou referências de pacotes NuGet).</span><span class="sxs-lookup"><span data-stu-id="07ad6-116">Other libraries that the project depends on (via project references or NuGet package references).</span></span>

<span data-ttu-id="07ad6-117">Para projetos executáveis direcionados a versões anteriores ao .NET Core 3.0, as dependências de biblioteca do NuGet normalmente NÃO são copiadas para a pasta de saída.</span><span class="sxs-lookup"><span data-stu-id="07ad6-117">For executable projects targeting versions earlier than .NET Core 3.0, library dependencies from NuGet are typically NOT copied to the output folder.</span></span>  <span data-ttu-id="07ad6-118">Eles são resolvidos a partir da pasta de pacotes globais NuGet em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="07ad6-118">They're resolved from the NuGet global packages folder at run time.</span></span> <span data-ttu-id="07ad6-119">Com isso em mente, o produto de `dotnet build` não está pronto para ser transferido para outro computador para execução.</span><span class="sxs-lookup"><span data-stu-id="07ad6-119">With that in mind, the product of `dotnet build` isn't ready to be transferred to another machine to run.</span></span> <span data-ttu-id="07ad6-120">Para criar uma versão do aplicativo que pode ser implantada, você precisa publicá-lo (por exemplo, com o comando [dotnet publish).](dotnet-publish.md)</span><span class="sxs-lookup"><span data-stu-id="07ad6-120">To create a version of the application that can be deployed, you need to publish it (for example, with the [dotnet publish](dotnet-publish.md) command).</span></span> <span data-ttu-id="07ad6-121">Para saber mais, confira [Implantação de aplicativos .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="07ad6-121">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span>

<span data-ttu-id="07ad6-122">Para projetos executáveis direcionados ao .NET Core 3.0 e posteriores, as dependências da biblioteca são copiadas para a pasta de saída.</span><span class="sxs-lookup"><span data-stu-id="07ad6-122">For executable projects targeting .NET Core 3.0 and later, library dependencies are copied to the output folder.</span></span> <span data-ttu-id="07ad6-123">Isso significa que, se não houver nenhuma outra lógica específica de publicação (como projetos da Web), a produção de compilação deve ser implantável.</span><span class="sxs-lookup"><span data-stu-id="07ad6-123">This means that if there isn't any other publish-specific logic (such as Web projects have), the build output should be deployable.</span></span>

<span data-ttu-id="07ad6-124">A compilação exige o arquivo *project.assets.json*, que lista as dependências do seu aplicativo.</span><span class="sxs-lookup"><span data-stu-id="07ad6-124">Building requires the *project.assets.json* file, which lists the dependencies of your application.</span></span> <span data-ttu-id="07ad6-125">O arquivo é [`dotnet restore`](dotnet-restore.md) criado quando é executado.</span><span class="sxs-lookup"><span data-stu-id="07ad6-125">The file is created when [`dotnet restore`](dotnet-restore.md) is executed.</span></span> <span data-ttu-id="07ad6-126">Sem o arquivo de ativos em vigor, as ferramentas não conseguem resolver os assemblies de referência, o que resulta em erros.</span><span class="sxs-lookup"><span data-stu-id="07ad6-126">Without the assets file in place, the tooling can't resolve reference assemblies, which results in errors.</span></span> <span data-ttu-id="07ad6-127">Com o .NET Core 1.x SDK, `dotnet restore` você `dotnet build`precisava ser executado explicitamente antes de executar .</span><span class="sxs-lookup"><span data-stu-id="07ad6-127">With .NET Core 1.x SDK, you needed to explicitly run `dotnet restore` before running `dotnet build`.</span></span> <span data-ttu-id="07ad6-128">Começando pelo SDK do .NET Core 2.0, o `dotnet restore` é executado implicitamente quando você executa `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="07ad6-128">Starting with .NET Core 2.0 SDK, `dotnet restore` runs implicitly when you run `dotnet build`.</span></span> <span data-ttu-id="07ad6-129">Se você deseja desabilitar a restauração implícita ao executar o comando de build, é possível passar a opção `--no-restore`.</span><span class="sxs-lookup"><span data-stu-id="07ad6-129">If you want to disable implicit restore when running the build command, you can pass the `--no-restore` option.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

<span data-ttu-id="07ad6-130">O fato de o projeto ser executável ou não é determinado pela propriedade `<OutputType>` do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="07ad6-130">Whether the project is executable or not is determined by the `<OutputType>` property in the project file.</span></span> <span data-ttu-id="07ad6-131">O seguinte exemplo mostra um projeto que produz um código executável:</span><span class="sxs-lookup"><span data-stu-id="07ad6-131">The following example shows a project that produces executable code:</span></span>

```xml
<PropertyGroup>
  <OutputType>Exe</OutputType>
</PropertyGroup>
```

<span data-ttu-id="07ad6-132">Para produzir uma biblioteca, `<OutputType>` omita a `Library`propriedade ou altere seu valor para .</span><span class="sxs-lookup"><span data-stu-id="07ad6-132">To produce a library, omit the `<OutputType>` property or change its value to `Library`.</span></span> <span data-ttu-id="07ad6-133">O IL DLL para uma biblioteca não contém pontos de entrada e não pode ser executado.</span><span class="sxs-lookup"><span data-stu-id="07ad6-133">The IL DLL for a library doesn't contain entry points and can't be executed.</span></span>

### <a name="msbuild"></a><span data-ttu-id="07ad6-134">MSBuild</span><span class="sxs-lookup"><span data-stu-id="07ad6-134">MSBuild</span></span>

<span data-ttu-id="07ad6-135">O `dotnet build` usa o MSBuild para compilar o projeto e, portanto, dá suporte a builds paralelos e incrementais.</span><span class="sxs-lookup"><span data-stu-id="07ad6-135">`dotnet build` uses MSBuild to build the project, so it supports both parallel and incremental builds.</span></span> <span data-ttu-id="07ad6-136">Para obter mais informações, consulte [Compilações incrementais](/visualstudio/msbuild/incremental-builds).</span><span class="sxs-lookup"><span data-stu-id="07ad6-136">For more information, see [Incremental Builds](/visualstudio/msbuild/incremental-builds).</span></span>

<span data-ttu-id="07ad6-137">Além das próprias opções, o comando `dotnet build` também aceita opções do MSBuild, como `-p` para configurar propriedades ou `-l` para definir um agente.</span><span class="sxs-lookup"><span data-stu-id="07ad6-137">In addition to its options, the `dotnet build` command accepts MSBuild options, such as `-p` for setting properties or `-l` to define a logger.</span></span> <span data-ttu-id="07ad6-138">Para obter mais informações sobre essas opções, confira a [Referência de linha de comando do MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="07ad6-138">For more information about these options, see the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="07ad6-139">Ou você também pode usar o comando [dotnet msbuild](dotnet-msbuild.md).</span><span class="sxs-lookup"><span data-stu-id="07ad6-139">Or you can also use the [dotnet msbuild](dotnet-msbuild.md) command.</span></span>

<span data-ttu-id="07ad6-140">Correr `dotnet build` é equivalente `dotnet msbuild -restore`a correr; no entanto, a verbosidade padrão da saída é diferente.</span><span class="sxs-lookup"><span data-stu-id="07ad6-140">Running `dotnet build` is equivalent to running `dotnet msbuild -restore`; however, the default verbosity of the output is different.</span></span>

## <a name="arguments"></a><span data-ttu-id="07ad6-141">Argumentos</span><span class="sxs-lookup"><span data-stu-id="07ad6-141">Arguments</span></span>

`PROJECT | SOLUTION`

<span data-ttu-id="07ad6-142">O arquivo de projeto ou solução a ser compilado.</span><span class="sxs-lookup"><span data-stu-id="07ad6-142">The project or solution file to build.</span></span> <span data-ttu-id="07ad6-143">Se um arquivo de solução ou projeto não for especificado, o MSBuild pesquisará o diretório de trabalho atual em busca de um arquivo que tenha uma extensão terminada em *proj* ou *sln* e usará esse arquivo.</span><span class="sxs-lookup"><span data-stu-id="07ad6-143">If a project or solution file isn't specified, MSBuild searches the current working directory for a file that has a file extension that ends in either *proj* or *sln* and uses that file.</span></span>

## <a name="options"></a><span data-ttu-id="07ad6-144">Opções</span><span class="sxs-lookup"><span data-stu-id="07ad6-144">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="07ad6-145">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="07ad6-145">Defines the build configuration.</span></span> <span data-ttu-id="07ad6-146">O padrão para `Debug`a maioria dos projetos é, mas você pode substituir as configurações de configuração de compilação em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="07ad6-146">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="07ad6-147">Compila para uma [estrutura](../../standard/frameworks.md) específica.</span><span class="sxs-lookup"><span data-stu-id="07ad6-147">Compiles for a specific [framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="07ad6-148">A estrutura precisa ser definida no [arquivo de projeto](csproj.md).</span><span class="sxs-lookup"><span data-stu-id="07ad6-148">The framework must be defined in the [project file](csproj.md).</span></span>

- **`--force`**

  <span data-ttu-id="07ad6-149">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="07ad6-149">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="07ad6-150">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="07ad6-150">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="07ad6-151">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="07ad6-151">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="07ad6-152">Permite que o comando pare e aguarde entrada ou ação do usuário.</span><span class="sxs-lookup"><span data-stu-id="07ad6-152">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="07ad6-153">Por exemplo, para concluir a autenticação.</span><span class="sxs-lookup"><span data-stu-id="07ad6-153">For example, to complete authentication.</span></span> <span data-ttu-id="07ad6-154">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="07ad6-154">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="07ad6-155">Ignora as referências P2P (projeto a projeto) e compila apenas o projeto raiz especificado.</span><span class="sxs-lookup"><span data-stu-id="07ad6-155">Ignores project-to-project (P2P) references and only builds the specified root project.</span></span>

- **`--no-incremental`**

  <span data-ttu-id="07ad6-156">Marca o build como não segura para build incremental.</span><span class="sxs-lookup"><span data-stu-id="07ad6-156">Marks the build as unsafe for incremental build.</span></span> <span data-ttu-id="07ad6-157">Esse sinalizador desativa a compilação incremental e força uma nova recompilação do grafo de dependência do projeto.</span><span class="sxs-lookup"><span data-stu-id="07ad6-157">This flag turns off incremental compilation and forces a clean rebuild of the project's dependency graph.</span></span>

- **`--no-restore`**

  <span data-ttu-id="07ad6-158">Não executa uma restauração implícita durante o build.</span><span class="sxs-lookup"><span data-stu-id="07ad6-158">Doesn't execute an implicit restore during build.</span></span>

- **`--nologo`**

  <span data-ttu-id="07ad6-159">Não exibe a faixa de inicialização nem a mensagem de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="07ad6-159">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="07ad6-160">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="07ad6-160">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="07ad6-161">Diretório no qual os binários compilados são colocados.</span><span class="sxs-lookup"><span data-stu-id="07ad6-161">Directory in which to place the built binaries.</span></span> <span data-ttu-id="07ad6-162">Se não for especificado, o caminho padrão será `./bin/<configuration>/<framework>/`.</span><span class="sxs-lookup"><span data-stu-id="07ad6-162">If not specified, the default path is `./bin/<configuration>/<framework>/`.</span></span>  <span data-ttu-id="07ad6-163">Para projetos com vários frameworks `TargetFrameworks` de destino (via `--framework` propriedade), você também precisa definir quando você especifica essa opção.</span><span class="sxs-lookup"><span data-stu-id="07ad6-163">For projects with multiple target frameworks (via the `TargetFrameworks` property), you also need to define `--framework` when you specify this option.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="07ad6-164">Especifica o runtime de destino.</span><span class="sxs-lookup"><span data-stu-id="07ad6-164">Specifies the target runtime.</span></span> <span data-ttu-id="07ad6-165">Para obter uma lista de RIDs (Identificadores de Runtime), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="07ad6-165">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="07ad6-166">Define o nível de detalhamento do MSBuild.</span><span class="sxs-lookup"><span data-stu-id="07ad6-166">Sets the MSBuild verbosity level.</span></span> <span data-ttu-id="07ad6-167">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="07ad6-167">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="07ad6-168">O padrão é `minimal`.</span><span class="sxs-lookup"><span data-stu-id="07ad6-168">The default is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="07ad6-169">Define o valor da propriedade `$(VersionSuffix)` a ser usada ao compilar o projeto.</span><span class="sxs-lookup"><span data-stu-id="07ad6-169">Sets the value of the `$(VersionSuffix)` property to use when building the project.</span></span> <span data-ttu-id="07ad6-170">Isso funcionará apenas se a propriedade `$(Version)` não estiver definida.</span><span class="sxs-lookup"><span data-stu-id="07ad6-170">This only works if the `$(Version)` property isn't set.</span></span> <span data-ttu-id="07ad6-171">Em seguida, `$(Version)` é definido como o `$(VersionPrefix)` combinado com o `$(VersionSuffix)`, separado por um traço.</span><span class="sxs-lookup"><span data-stu-id="07ad6-171">Then, `$(Version)` is set to the `$(VersionPrefix)` combined with the `$(VersionSuffix)`, separated by a dash.</span></span>

## <a name="examples"></a><span data-ttu-id="07ad6-172">Exemplos</span><span class="sxs-lookup"><span data-stu-id="07ad6-172">Examples</span></span>

- <span data-ttu-id="07ad6-173">Compile um projeto e suas dependências:</span><span class="sxs-lookup"><span data-stu-id="07ad6-173">Build a project and its dependencies:</span></span>

  ```dotnetcli
  dotnet build
  ```

- <span data-ttu-id="07ad6-174">Compile um projeto e suas dependências usando a configuração da Versão:</span><span class="sxs-lookup"><span data-stu-id="07ad6-174">Build a project and its dependencies using Release configuration:</span></span>

  ```dotnetcli
  dotnet build --configuration Release
  ```

- <span data-ttu-id="07ad6-175">Compile um projeto e suas dependências para um runtime específico (no exemplo, Ubuntu 18.04):</span><span class="sxs-lookup"><span data-stu-id="07ad6-175">Build a project and its dependencies for a specific runtime (in this example, Ubuntu 18.04):</span></span>

  ```dotnetcli
  dotnet build --runtime ubuntu.18.04-x64
  ```

- <span data-ttu-id="07ad6-176">Compile o projeto e use a fonte do pacote NuGet especificada durante a operação de restauração (SDK do .NET Core 2.0 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="07ad6-176">Build the project and use the specified NuGet package source during the restore operation (.NET Core 2.0 SDK and later versions):</span></span>

  ```dotnetcli
  dotnet build --source c:\packages\mypackages
  ```

- <span data-ttu-id="07ad6-177">Compile o projeto e defina a versão 1.2.3.4 como um parâmetro de compilação usando a `-p` [opção MSBuild](#msbuild):</span><span class="sxs-lookup"><span data-stu-id="07ad6-177">Build the project and set version 1.2.3.4 as a build parameter using the `-p` [MSBuild option](#msbuild):</span></span>

  ```dotnetcli
  dotnet build -p:Version=1.2.3.4
  ```
