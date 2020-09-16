---
title: Comando dotnet pack
description: O comando dotnet pack cria pacotes NuGet para seu projeto .NET Core.
ms.date: 04/28/2020
ms.openlocfilehash: 409b946d93cf73fec38941740a446c3ee3402490
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537817"
---
# <a name="dotnet-pack"></a><span data-ttu-id="bbcb7-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="bbcb7-103">dotnet pack</span></span>

<span data-ttu-id="bbcb7-104">**Este artigo aplica-se a:** ✔️ SDK do .NET Core 2. x e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="bbcb7-104">**This article applies to:** ✔️ .NET Core 2.x SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="bbcb7-105">Name</span><span class="sxs-lookup"><span data-stu-id="bbcb7-105">Name</span></span>

<span data-ttu-id="bbcb7-106">`dotnet pack` – Empacota o código em um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-106">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bbcb7-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="bbcb7-107">Synopsis</span></span>

```dotnetcli
dotnet pack [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [--force] [--include-source] [--include-symbols] [--interactive]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output <OUTPUT_DIRECTORY>] [--runtime <RUNTIME_IDENTIFIER>]
    [-s|--serviceable] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet pack -h|--help
```

## <a name="description"></a><span data-ttu-id="bbcb7-108">Description</span><span class="sxs-lookup"><span data-stu-id="bbcb7-108">Description</span></span>

<span data-ttu-id="bbcb7-109">O comando `dotnet pack` compila o projeto e cria pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-109">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="bbcb7-110">O resultado desse comando é um pacote NuGet (ou seja, um arquivo *. nupkg* ).</span><span class="sxs-lookup"><span data-stu-id="bbcb7-110">The result of this command is a NuGet package (that is, a *.nupkg* file).</span></span>

<span data-ttu-id="bbcb7-111">Se você quiser gerar um pacote que contém os símbolos de depuração, terá duas opções disponíveis:</span><span class="sxs-lookup"><span data-stu-id="bbcb7-111">If you want to generate a package that contains the debug symbols, you have two options available:</span></span>

- <span data-ttu-id="bbcb7-112">`--include-symbols` -Ele cria o pacote de símbolos.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-112">`--include-symbols` - it creates the symbols package.</span></span>
- <span data-ttu-id="bbcb7-113">`--include-source` -Ele cria o pacote de símbolos com uma `src` pasta dentro de contendo os arquivos de origem.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-113">`--include-source` - it creates the symbols package with a `src` folder inside containing the source files.</span></span>

<span data-ttu-id="bbcb7-114">As dependências do NuGet do projeto empacotado são adicionadas ao arquivo *.nuspec* para que possam ser resolvidas apropriadamente quando o pacote for instalado.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-114">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="bbcb7-115">As referências de projeto a projeto não são empacotadas dentro do projeto.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-115">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="bbcb7-116">No momento, você precisa ter um pacote por projeto se tiver dependências de projeto a projeto.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-116">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="bbcb7-117">Por padrão, `dotnet pack` compila primeiro o projeto.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-117">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="bbcb7-118">Se você quiser evitar esse comportamento, passe a opção `--no-build`.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-118">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="bbcb7-119">Com frequência, essa opção é útil em cenários de build de CI (integração contínua) nos quais você sabe que o código foi compilado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-119">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

> [!NOTE]
> <span data-ttu-id="bbcb7-120">Em alguns casos, a compilação implícita não pode ser executada.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-120">In some cases, the implicit build cannot be performed.</span></span> <span data-ttu-id="bbcb7-121">Isso pode ocorrer quando `GeneratePackageOnBuild` é definido, para evitar uma dependência cíclica entre destinos de compilação e de pacote.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-121">This can occur when `GeneratePackageOnBuild` is set, to avoid a cyclic dependency between build and pack targets.</span></span> <span data-ttu-id="bbcb7-122">A compilação também pode falhar se houver um arquivo bloqueado ou outro problema.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-122">The build can also fail if there is a locked file or other issue.</span></span>

<span data-ttu-id="bbcb7-123">Você pode fornecer as propriedades de MSBuild para o comando `dotnet pack` para o processo de empacotamento.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-123">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="bbcb7-124">Para obter mais informações, consulte [Propriedades de metadados do NuGet](csproj.md#nuget-metadata-properties) e a [Referência de linha de comando MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="bbcb7-124">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="bbcb7-125">A seção [Exemplos](#examples) mostra como usar a opção -p do MSBuild para alguns cenários diferentes.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-125">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

<span data-ttu-id="bbcb7-126">Projetos da Web não são empacotáveis por padrão.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-126">Web projects aren't packable by default.</span></span> <span data-ttu-id="bbcb7-127">Para substituir o comportamento padrão, adicione a seguinte propriedade ao seu arquivo *.csproj*:</span><span class="sxs-lookup"><span data-stu-id="bbcb7-127">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

### <a name="implicit-restore"></a><span data-ttu-id="bbcb7-128">Restauração implícita</span><span class="sxs-lookup"><span data-stu-id="bbcb7-128">Implicit restore</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="bbcb7-129">Argumentos</span><span class="sxs-lookup"><span data-stu-id="bbcb7-129">Arguments</span></span>

`PROJECT | SOLUTION`

  <span data-ttu-id="bbcb7-130">O projeto ou a solução a ser empacotada.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-130">The project or solution to pack.</span></span> <span data-ttu-id="bbcb7-131">É um caminho para um [arquivo csproj](csproj.md), arquivo vbproj, arquivo fsproj, um arquivo de solução ou para um diretório.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-131">It's either a path to a [csproj file](csproj.md), vbproj file, fsproj file, a solution file, or to a directory.</span></span> <span data-ttu-id="bbcb7-132">Se não for especificado, o comando pesquisará o diretório atual em busca de um arquivo de projeto ou de solução.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-132">If not specified, the command searches the current directory for a project or solution file.</span></span>

## <a name="options"></a><span data-ttu-id="bbcb7-133">Opções</span><span class="sxs-lookup"><span data-stu-id="bbcb7-133">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="bbcb7-134">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-134">Defines the build configuration.</span></span> <span data-ttu-id="bbcb7-135">O padrão para a maioria dos projetos é `Debug` , mas você pode substituir as definições de configuração de compilação em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-135">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`--force`**

  <span data-ttu-id="bbcb7-136">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-136">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="bbcb7-137">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-137">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="bbcb7-138">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-138">Prints out a short help for the command.</span></span>

- **`--include-source`**

  <span data-ttu-id="bbcb7-139">Inclui os pacotes de depuração do NuGet, além dos pacotes NuGet regulares no diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-139">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span> <span data-ttu-id="bbcb7-140">Os arquivos de origem são incluídos na `src` pasta dentro do pacote de símbolos.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-140">The sources files are included in the `src` folder within the symbols package.</span></span>

- **`--include-symbols`**

  <span data-ttu-id="bbcb7-141">Inclui os pacotes de depuração do NuGet, além dos pacotes NuGet regulares no diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-141">Includes the debug symbols NuGet packages in addition to the regular NuGet packages in the output directory.</span></span>

- **`--interactive`**

  <span data-ttu-id="bbcb7-142">Permite que o comando pare e aguarde a entrada ou uma ação do usuário (por exemplo, para concluir a autenticação).</span><span class="sxs-lookup"><span data-stu-id="bbcb7-142">Allows the command to stop and wait for user input or action (for example, to complete authentication).</span></span> <span data-ttu-id="bbcb7-143">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-build`**

  <span data-ttu-id="bbcb7-144">Não compila o projeto antes do empacotamento.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-144">Doesn't build the project before packing.</span></span> <span data-ttu-id="bbcb7-145">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-145">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="bbcb7-146">Ignora as referências projeto a projeto e só restaura o projeto raiz.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-146">Ignores project-to-project references and only restores the root project.</span></span>

- **`--no-restore`**

  <span data-ttu-id="bbcb7-147">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-147">Doesn't execute an implicit restore when running the command.</span></span>

- **`--nologo`**

  <span data-ttu-id="bbcb7-148">Não exibe a faixa de inicialização nem a mensagem de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-148">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="bbcb7-149">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-149">Available since .NET Core 3.0 SDK.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="bbcb7-150">Coloca os pacotes compilados no diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-150">Places the built packages in the directory specified.</span></span>

- **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="bbcb7-151">Especifica o runtime de destino para o qual restaurar os pacotes.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-151">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="bbcb7-152">Para obter uma lista de RIDs (Identificadores de Runtime), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="bbcb7-152">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

- **`-s|--serviceable`**

  <span data-ttu-id="bbcb7-153">Define o sinalizador operacional no pacote.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-153">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="bbcb7-154">Para saber mais, veja [Blog do .NET: .NET 4.5.1 oferece suporte às Atualizações de segurança da Microsoft para Bibliotecas do .NET NuGet](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="bbcb7-154">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="bbcb7-155">Define o valor da propriedade do MSBuild `$(VersionSuffix)` no projeto.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-155">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="bbcb7-156">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-156">Sets the verbosity level of the command.</span></span> <span data-ttu-id="bbcb7-157">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="bbcb7-157">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

## <a name="examples"></a><span data-ttu-id="bbcb7-158">Exemplos</span><span class="sxs-lookup"><span data-stu-id="bbcb7-158">Examples</span></span>

- <span data-ttu-id="bbcb7-159">Empacota o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="bbcb7-159">Pack the project in the current directory:</span></span>

  ```dotnetcli
  dotnet pack
  ```

- <span data-ttu-id="bbcb7-160">Empacote o projeto `app1`:</span><span class="sxs-lookup"><span data-stu-id="bbcb7-160">Pack the `app1` project:</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj
  ```

- <span data-ttu-id="bbcb7-161">Empacote o projeto no diretório atual e coloque os pacotes resultantes na pasta`nupkgs`:</span><span class="sxs-lookup"><span data-stu-id="bbcb7-161">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```dotnetcli
  dotnet pack --output nupkgs
  ```

- <span data-ttu-id="bbcb7-162">Empacote o projeto no diretório atual da pasta `nupkgs` e ignora a etapa de compilação:</span><span class="sxs-lookup"><span data-stu-id="bbcb7-162">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```dotnetcli
  dotnet pack --no-build --output nupkgs
  ```

- <span data-ttu-id="bbcb7-163">Com o sufixo da versão do projeto configurado como `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` no arquivo *.csproj*, empacote o projeto atual e atualize a versão do pacote resultante com o sufixo especificado:</span><span class="sxs-lookup"><span data-stu-id="bbcb7-163">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```dotnetcli
  dotnet pack --version-suffix "ci-1234"
  ```

- <span data-ttu-id="bbcb7-164">Defina a versão do pacote como `2.1.0` com a propriedade MSBuild `PackageVersion`:</span><span class="sxs-lookup"><span data-stu-id="bbcb7-164">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```dotnetcli
  dotnet pack -p:PackageVersion=2.1.0
  ```

- <span data-ttu-id="bbcb7-165">Empacote o projeto para uma determinada [estrutura de destino](../../standard/frameworks.md):</span><span class="sxs-lookup"><span data-stu-id="bbcb7-165">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```dotnetcli
  dotnet pack -p:TargetFrameworks=net45
  ```

- <span data-ttu-id="bbcb7-166">Empacotar o projeto e usar um tempo de execução específico (Windows 10) para a operação de restauração:</span><span class="sxs-lookup"><span data-stu-id="bbcb7-166">Pack the project and use a specific runtime (Windows 10) for the restore operation:</span></span>

  ```dotnetcli
  dotnet pack --runtime win10-x64
  ```

- <span data-ttu-id="bbcb7-167">Empacotar o projeto usando um arquivo *. nuspec* :</span><span class="sxs-lookup"><span data-stu-id="bbcb7-167">Pack the project using a *.nuspec* file:</span></span>

  ```dotnetcli
  dotnet pack ~/projects/app1/project.csproj -p:NuspecFile=~/projects/app1/project.nuspec -p:NuspecBasePath=~/projects/app1/nuget
  ```

  <span data-ttu-id="bbcb7-168">Para obter informações sobre como usar `NuspecFile` `NuspecBasePath` `NuspecProperties` o, o e o, consulte os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="bbcb7-168">For information about how to use `NuspecFile`, `NuspecBasePath`, and `NuspecProperties`, see the following resources:</span></span>
  
  - [<span data-ttu-id="bbcb7-169">Empacotamento usando um .nuspec</span><span class="sxs-lookup"><span data-stu-id="bbcb7-169">Packing using a .nuspec</span></span>](/nuget/reference/msbuild-targets#packing-using-a-nuspec)
  - [<span data-ttu-id="bbcb7-170">Pontos de extensão avançados para criar pacote personalizado</span><span class="sxs-lookup"><span data-stu-id="bbcb7-170">Advanced extension points to create customized package</span></span>](/nuget/reference/msbuild-targets#advanced-extension-points-to-create-customized-package)
  - [<span data-ttu-id="bbcb7-171">Propriedades globais</span><span class="sxs-lookup"><span data-stu-id="bbcb7-171">Global properties</span></span>](/visualstudio/msbuild/msbuild-properties?view=vs-2019#global-properties)
