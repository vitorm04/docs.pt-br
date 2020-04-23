---
title: Comando dotnet pack
description: O comando dotnet pack cria pacotes NuGet para seu projeto .NET Core.
ms.date: 02/14/2020
ms.openlocfilehash: 2df096a088a177b77256b5d717f31e185507b249
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102808"
---
# <a name="dotnet-pack"></a><span data-ttu-id="9c3ea-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="9c3ea-103">dotnet pack</span></span>

<span data-ttu-id="9c3ea-104">**Este artigo se aplica a:** ✔️ .NET Core 2.x SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="9c3ea-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="9c3ea-105">Nome</span><span class="sxs-lookup"><span data-stu-id="9c3ea-105">Name</span></span>

<span data-ttu-id="9c3ea-106">`dotnet pack` – Empacota o código em um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-106">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="9c3ea-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="9c3ea-107">Synopsis</span></span>

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output <OUTPUT_DIRECTORY>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--serviceable] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet pack -h|--help
```

## <a name="description"></a><span data-ttu-id="9c3ea-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="9c3ea-108">Description</span></span>

<span data-ttu-id="9c3ea-109">O comando `dotnet pack` compila o projeto e cria pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-109">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="9c3ea-110">O resultado deste comando é um pacote NuGet (ou seja, um arquivo *.nupkg).*</span><span class="sxs-lookup"><span data-stu-id="9c3ea-110">The result of this command is a NuGet package (that is, a *.nupkg* file).</span></span>

<span data-ttu-id="9c3ea-111">Se você quiser gerar um pacote que contenha os símbolos de depuração, você tem duas opções disponíveis:</span><span class="sxs-lookup"><span data-stu-id="9c3ea-111">If you want to generate a package that contains the debug symbols, you have two options available:</span></span>

- <span data-ttu-id="9c3ea-112">`--include-symbols`- cria o pacote de símbolos.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-112">`--include-symbols` - it creates the symbols package.</span></span>
- <span data-ttu-id="9c3ea-113">`--include-source`- ele cria o pacote `src` de símbolos com uma pasta dentro contendo os arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-113">`--include-source` - it creates the symbols package with a `src` folder inside containing the source files.</span></span>

<span data-ttu-id="9c3ea-114">As dependências do NuGet do projeto empacotado são adicionadas ao arquivo *.nuspec* para que possam ser resolvidas apropriadamente quando o pacote for instalado.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-114">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="9c3ea-115">As referências de projeto a projeto não são empacotadas dentro do projeto.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-115">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="9c3ea-116">No momento, você precisa ter um pacote por projeto se tiver dependências de projeto a projeto.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-116">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="9c3ea-117">Por padrão, `dotnet pack` compila primeiro o projeto.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-117">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="9c3ea-118">Se você quiser evitar esse comportamento, passe a opção `--no-build`.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-118">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="9c3ea-119">Com frequência, essa opção é útil em cenários de build de CI (integração contínua) nos quais você sabe que o código foi compilado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-119">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

> [!NOTE]
> <span data-ttu-id="9c3ea-120">Em alguns casos, a construção implícita não pode ser realizada.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-120">In some cases, the implicit build cannot be performed.</span></span> <span data-ttu-id="9c3ea-121">Isso pode `GeneratePackageOnBuild` ocorrer quando estiver definido, para evitar uma dependência cíclica entre metas de construção e embalagem.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-121">This can occur when `GeneratePackageOnBuild` is set, to avoid a cyclic dependency between build and pack targets.</span></span> <span data-ttu-id="9c3ea-122">A compilação também pode falhar se houver um arquivo bloqueado ou outro problema.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-122">The build can also fail if there is a locked file or other issue.</span></span>

<span data-ttu-id="9c3ea-123">Você pode fornecer as propriedades de MSBuild para o comando `dotnet pack` para o processo de empacotamento.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-123">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="9c3ea-124">Para obter mais informações, consulte [Propriedades de metadados do NuGet](csproj.md#nuget-metadata-properties) e a [Referência de linha de comando MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="9c3ea-124">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="9c3ea-125">A seção [Exemplos](#examples) mostra como usar a opção -p do MSBuild para alguns cenários diferentes.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-125">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

<span data-ttu-id="9c3ea-126">Projetos da Web não são empacotáveis por padrão.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-126">Web projects aren't packable by default.</span></span> <span data-ttu-id="9c3ea-127">Para substituir o comportamento padrão, adicione a seguinte propriedade ao seu arquivo *.csproj*:</span><span class="sxs-lookup"><span data-stu-id="9c3ea-127">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

### <a name="implicit-restore"></a><span data-ttu-id="9c3ea-128">Restauração implícita</span><span class="sxs-lookup"><span data-stu-id="9c3ea-128">Implicit restore</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="9c3ea-129">Argumentos</span><span class="sxs-lookup"><span data-stu-id="9c3ea-129">Arguments</span></span>

`PROJECT | SOLUTION`

  <span data-ttu-id="9c3ea-130">O projeto ou solução para embalar.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-130">The project or solution to pack.</span></span> <span data-ttu-id="9c3ea-131">Ou é um caminho para um [arquivo csproj,](csproj.md)um arquivo de solução ou para um diretório.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-131">It's either a path to a [csproj file](csproj.md), a solution file, or to a directory.</span></span> <span data-ttu-id="9c3ea-132">Se não for especificado, o comando pesquisa o diretório atual para um arquivo de projeto ou solução.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-132">If not specified, the command searches the current directory for a project or solution file.</span></span>

## <a name="options"></a><span data-ttu-id="9c3ea-133">Opções</span><span class="sxs-lookup"><span data-stu-id="9c3ea-133">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="9c3ea-134">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-134">Defines the build configuration.</span></span> <span data-ttu-id="9c3ea-135">O padrão para `Debug`a maioria dos projetos é, mas você pode substituir as configurações de configuração de compilação em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-135">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`--force`**

  <span data-ttu-id="9c3ea-136">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-136">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="9c3ea-137">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-137">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="9c3ea-138">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-138">Prints out a short help for the command.</span></span>

- **`--include-source`**

  <span data-ttu-id="9c3ea-139">Inclui os símbolos de depuração pacotes NuGet, além dos pacotes NuGet regulares no diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-139">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span> <span data-ttu-id="9c3ea-140">Os arquivos de fontes `src` estão incluídos na pasta dentro do pacote de símbolos.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-140">The sources files are included in the `src` folder within the symbols package.</span></span>

- **`--include-symbols`**

  <span data-ttu-id="9c3ea-141">Inclui os símbolos de depuração pacotes NuGet, além dos pacotes NuGet regulares no diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-141">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span>

- **`--interactive`**

  <span data-ttu-id="9c3ea-142">Permite que o comando pare e aguarde a entrada ou uma ação do usuário (por exemplo, para concluir a autenticação).</span><span class="sxs-lookup"><span data-stu-id="9c3ea-142">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="9c3ea-143">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-build`**

  <span data-ttu-id="9c3ea-144">Não compila o projeto antes do empacotamento.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-144">Doesn't build the project before packing.</span></span> <span data-ttu-id="9c3ea-145">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-145">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="9c3ea-146">Ignora as referências projeto a projeto e só restaura o projeto raiz.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-146">Ignores project-to-project references and only restores the root project.</span></span>

- **`--no-restore`**

  <span data-ttu-id="9c3ea-147">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-147">Doesn't execute an implicit restore when running the command.</span></span>

- **`--nologo`**

  <span data-ttu-id="9c3ea-148">Não exibe a faixa de inicialização nem a mensagem de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-148">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="9c3ea-149">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-149">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="9c3ea-150">Coloca os pacotes compilados no diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-150">Places the built packages in the directory specified.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="9c3ea-151">Especifica o runtime de destino para o qual restaurar os pacotes.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-151">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="9c3ea-152">Para obter uma lista de RIDs (Identificadores de Runtime), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="9c3ea-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-s|--serviceable`**

  <span data-ttu-id="9c3ea-153">Define o sinalizador operacional no pacote.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-153">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="9c3ea-154">Para saber mais, veja [Blog do .NET: .NET 4.5.1 oferece suporte às Atualizações de segurança da Microsoft para Bibliotecas do .NET NuGet](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="9c3ea-154">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="9c3ea-155">Define o valor da propriedade do MSBuild `$(VersionSuffix)` no projeto.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-155">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="9c3ea-156">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-156">Sets the verbosity level of the command.</span></span> <span data-ttu-id="9c3ea-157">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="9c3ea-157">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="9c3ea-158">Exemplos</span><span class="sxs-lookup"><span data-stu-id="9c3ea-158">Examples</span></span>

- <span data-ttu-id="9c3ea-159">Empacota o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="9c3ea-159">Pack the project in the current directory:</span></span>

  ```dotnetcli
  dotnet pack
  ```

- <span data-ttu-id="9c3ea-160">Empacote o projeto `app1`:</span><span class="sxs-lookup"><span data-stu-id="9c3ea-160">Pack the `app1` project:</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- <span data-ttu-id="9c3ea-161">Empacote o projeto no diretório atual e coloque os pacotes resultantes na pasta`nupkgs`:</span><span class="sxs-lookup"><span data-stu-id="9c3ea-161">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- <span data-ttu-id="9c3ea-162">Empacote o projeto no diretório atual da pasta `nupkgs` e ignora a etapa de compilação:</span><span class="sxs-lookup"><span data-stu-id="9c3ea-162">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- <span data-ttu-id="9c3ea-163">Com o sufixo da versão do projeto configurado como `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` no arquivo *.csproj*, empacote o projeto atual e atualize a versão do pacote resultante com o sufixo especificado:</span><span class="sxs-lookup"><span data-stu-id="9c3ea-163">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- <span data-ttu-id="9c3ea-164">Defina a versão do pacote como `2.1.0` com a propriedade MSBuild `PackageVersion`:</span><span class="sxs-lookup"><span data-stu-id="9c3ea-164">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- <span data-ttu-id="9c3ea-165">Empacote o projeto para uma determinada [estrutura de destino](../../standard/frameworks.md):</span><span class="sxs-lookup"><span data-stu-id="9c3ea-165">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- <span data-ttu-id="9c3ea-166">Embale o projeto e use um tempo de execução específico (Windows 10) para a operação de restauração:</span><span class="sxs-lookup"><span data-stu-id="9c3ea-166">Pack the project and use a specific runtime (Windows 10) for the restore operation:</span></span>

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- <span data-ttu-id="9c3ea-167">Empacotar o projeto, usando um [arquivo .nuspec](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span><span class="sxs-lookup"><span data-stu-id="9c3ea-167">Pack the project using a [.nuspec file](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```
