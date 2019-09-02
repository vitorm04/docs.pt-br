---
title: Comando dotnet pack
description: O comando dotnet pack cria pacotes NuGet para seu projeto .NET Core.
ms.date: 12/04/2018
ms.openlocfilehash: c5c00f3bb06e5bc5579c0d3d6bdd39fbdf3db656
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202847"
---
# <a name="dotnet-pack"></a><span data-ttu-id="68fbe-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="68fbe-103">dotnet pack</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="68fbe-104">Nome</span><span class="sxs-lookup"><span data-stu-id="68fbe-104">Name</span></span>

<span data-ttu-id="68fbe-105">`dotnet pack` – Empacota o código em um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="68fbe-105">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="68fbe-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="68fbe-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="68fbe-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="68fbe-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```console
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="68fbe-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="68fbe-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```console
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output]
    [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="68fbe-109">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="68fbe-109">Description</span></span>

<span data-ttu-id="68fbe-110">O comando `dotnet pack` compila o projeto e cria pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="68fbe-110">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="68fbe-111">O resultado desse comando é um pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="68fbe-111">The result of this command is a NuGet package.</span></span> <span data-ttu-id="68fbe-112">Se a opção `--include-symbols` estiver presente, outro pacote que contém os símbolos de depuração será criado.</span><span class="sxs-lookup"><span data-stu-id="68fbe-112">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span>

<span data-ttu-id="68fbe-113">As dependências do NuGet do projeto empacotado são adicionadas ao arquivo *.nuspec* para que possam ser resolvidas apropriadamente quando o pacote for instalado.</span><span class="sxs-lookup"><span data-stu-id="68fbe-113">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="68fbe-114">As referências de projeto a projeto não são empacotadas dentro do projeto.</span><span class="sxs-lookup"><span data-stu-id="68fbe-114">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="68fbe-115">No momento, você precisa ter um pacote por projeto se tiver dependências de projeto a projeto.</span><span class="sxs-lookup"><span data-stu-id="68fbe-115">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="68fbe-116">Por padrão, `dotnet pack` compila primeiro o projeto.</span><span class="sxs-lookup"><span data-stu-id="68fbe-116">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="68fbe-117">Se você quiser evitar esse comportamento, passe a opção `--no-build`.</span><span class="sxs-lookup"><span data-stu-id="68fbe-117">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="68fbe-118">Com frequência, essa opção é útil em cenários de build de CI (integração contínua) nos quais você sabe que o código foi compilado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="68fbe-118">This option is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="68fbe-119">Você pode fornecer as propriedades de MSBuild para o comando `dotnet pack` para o processo de empacotamento.</span><span class="sxs-lookup"><span data-stu-id="68fbe-119">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="68fbe-120">Para obter mais informações, consulte [Propriedades de metadados do NuGet](csproj.md#nuget-metadata-properties) e a [Referência de linha de comando MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="68fbe-120">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="68fbe-121">A seção [Exemplos](#examples) mostra como usar a opção -p do MSBuild para alguns cenários diferentes.</span><span class="sxs-lookup"><span data-stu-id="68fbe-121">The [Examples](#examples) section shows how to use the MSBuild -p switch for a couple of different scenarios.</span></span>

<span data-ttu-id="68fbe-122">Projetos da Web não são empacotáveis por padrão.</span><span class="sxs-lookup"><span data-stu-id="68fbe-122">Web projects aren't packable by default.</span></span> <span data-ttu-id="68fbe-123">Para substituir o comportamento padrão, adicione a seguinte propriedade ao seu arquivo *.csproj*:</span><span class="sxs-lookup"><span data-stu-id="68fbe-123">To override the default behavior, add the following property to your *.csproj* file:</span></span>

```xml
<PropertyGroup>
   <IsPackable>true</IsPackable>
</PropertyGroup>
```

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="68fbe-124">Arguments</span><span class="sxs-lookup"><span data-stu-id="68fbe-124">Arguments</span></span>

* **`PROJECT`**

  <span data-ttu-id="68fbe-125">O projeto a ser empacotado.</span><span class="sxs-lookup"><span data-stu-id="68fbe-125">The project to pack.</span></span> <span data-ttu-id="68fbe-126">Pode ser um caminho para um [arquivo csproj](csproj.md) ou para um diretório.</span><span class="sxs-lookup"><span data-stu-id="68fbe-126">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="68fbe-127">Se não é especificado, ele usa como padrão o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="68fbe-127">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="68fbe-128">Opções</span><span class="sxs-lookup"><span data-stu-id="68fbe-128">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="68fbe-129">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="68fbe-129">.NET Core 2.x</span></span>](#tab/netcore2x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="68fbe-130">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="68fbe-130">Defines the build configuration.</span></span> <span data-ttu-id="68fbe-131">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="68fbe-131">The default value is `Debug`.</span></span>

* **`--force`**

  <span data-ttu-id="68fbe-132">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="68fbe-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="68fbe-133">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="68fbe-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

* **`-h|--help`**

  <span data-ttu-id="68fbe-134">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="68fbe-134">Prints out a short help for the command.</span></span>

* **`--include-source`**

  <span data-ttu-id="68fbe-135">Inclui os arquivos de origem no pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="68fbe-135">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="68fbe-136">Os arquivos de origem são incluídos na pasta `src` dentro de `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="68fbe-136">The sources files are included in the `src` folder within the `nupkg`.</span></span>

* **`--include-symbols`**

  <span data-ttu-id="68fbe-137">Gera os símbolos `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="68fbe-137">Generates the symbols `nupkg`.</span></span>

* **`--no-build`**

  <span data-ttu-id="68fbe-138">Não compila o projeto antes do empacotamento.</span><span class="sxs-lookup"><span data-stu-id="68fbe-138">Doesn't build the project before packing.</span></span> <span data-ttu-id="68fbe-139">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="68fbe-139">It also implicitly sets the `--no-restore` flag.</span></span>

* **`--no-dependencies`**

  <span data-ttu-id="68fbe-140">Ignora as referências projeto a projeto e só restaura o projeto raiz.</span><span class="sxs-lookup"><span data-stu-id="68fbe-140">Ignores project-to-project references and only restores the root project.</span></span>

* **`--no-restore`**

  <span data-ttu-id="68fbe-141">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="68fbe-141">Doesn't execute an implicit restore when running the command.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="68fbe-142">Coloca os pacotes compilados no diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="68fbe-142">Places the built packages in the directory specified.</span></span>

* **`--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="68fbe-143">Especifica o tempo de execução de destino para o qual restaurar os pacotes.</span><span class="sxs-lookup"><span data-stu-id="68fbe-143">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="68fbe-144">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="68fbe-144">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

* **`-s|--serviceable`**

  <span data-ttu-id="68fbe-145">Define o sinalizador operacional no pacote.</span><span class="sxs-lookup"><span data-stu-id="68fbe-145">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="68fbe-146">Para saber mais, veja [Blog do .NET: .NET 4.5.1 oferece suporte às Atualizações de segurança da Microsoft para Bibliotecas do .NET NuGet](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="68fbe-146">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="68fbe-147">Define o valor da propriedade do MSBuild `$(VersionSuffix)` no projeto.</span><span class="sxs-lookup"><span data-stu-id="68fbe-147">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="68fbe-148">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="68fbe-148">Sets the verbosity level of the command.</span></span> <span data-ttu-id="68fbe-149">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="68fbe-149">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="68fbe-150">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="68fbe-150">.NET Core 1.x</span></span>](#tab/netcore1x)

* **`-c|--configuration {Debug|Release}`**

  <span data-ttu-id="68fbe-151">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="68fbe-151">Defines the build configuration.</span></span> <span data-ttu-id="68fbe-152">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="68fbe-152">The default value is `Debug`.</span></span>

* **`-h|--help`**

  <span data-ttu-id="68fbe-153">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="68fbe-153">Prints out a short help for the command.</span></span>

* **`--include-source`**

  <span data-ttu-id="68fbe-154">Inclui os arquivos de origem no pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="68fbe-154">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="68fbe-155">Os arquivos de origem são incluídos na pasta `src` dentro de `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="68fbe-155">The sources files are included in the `src` folder within the `nupkg`.</span></span>

* **`--include-symbols`**

  <span data-ttu-id="68fbe-156">Gera os símbolos `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="68fbe-156">Generates the symbols `nupkg`.</span></span>

* **`--no-build`**

  <span data-ttu-id="68fbe-157">Não compila o projeto antes do empacotamento.</span><span class="sxs-lookup"><span data-stu-id="68fbe-157">Doesn't build the project before packing.</span></span>

* **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="68fbe-158">Coloca os pacotes compilados no diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="68fbe-158">Places the built packages in the directory specified.</span></span>

* **`-s|--serviceable`**

  <span data-ttu-id="68fbe-159">Define o sinalizador operacional no pacote.</span><span class="sxs-lookup"><span data-stu-id="68fbe-159">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="68fbe-160">Para saber mais, veja [Blog do .NET: .NET 4.5.1 oferece suporte às Atualizações de segurança da Microsoft para Bibliotecas do .NET NuGet](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="68fbe-160">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

* **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="68fbe-161">Define o valor da propriedade do MSBuild `$(VersionSuffix)` no projeto.</span><span class="sxs-lookup"><span data-stu-id="68fbe-161">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

* **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="68fbe-162">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="68fbe-162">Sets the verbosity level of the command.</span></span> <span data-ttu-id="68fbe-163">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="68fbe-163">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="68fbe-164">Exemplos</span><span class="sxs-lookup"><span data-stu-id="68fbe-164">Examples</span></span>

* <span data-ttu-id="68fbe-165">Empacota o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="68fbe-165">Pack the project in the current directory:</span></span>

  ```console
  dotnet pack
  ```

* <span data-ttu-id="68fbe-166">Empacote o projeto `app1`:</span><span class="sxs-lookup"><span data-stu-id="68fbe-166">Pack the `app1` project:</span></span>

  ```console
  dotnet pack ~/projects/app1/project.csproj
  ```

* <span data-ttu-id="68fbe-167">Empacote o projeto no diretório atual e coloque os pacotes resultantes na pasta`nupkgs`:</span><span class="sxs-lookup"><span data-stu-id="68fbe-167">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

  ```console
  dotnet pack --output nupkgs
  ```

* <span data-ttu-id="68fbe-168">Empacote o projeto no diretório atual da pasta `nupkgs` e ignora a etapa de compilação:</span><span class="sxs-lookup"><span data-stu-id="68fbe-168">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

  ```console
  dotnet pack --no-build --output nupkgs
  ```

* <span data-ttu-id="68fbe-169">Com o sufixo da versão do projeto configurado como `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` no arquivo *.csproj*, empacote o projeto atual e atualize a versão do pacote resultante com o sufixo especificado:</span><span class="sxs-lookup"><span data-stu-id="68fbe-169">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

  ```console
  dotnet pack --version-suffix "ci-1234"
  ```

* <span data-ttu-id="68fbe-170">Defina a versão do pacote como `2.1.0` com a propriedade MSBuild `PackageVersion`:</span><span class="sxs-lookup"><span data-stu-id="68fbe-170">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

  ```console
  dotnet pack -p:PackageVersion=2.1.0
  ```

* <span data-ttu-id="68fbe-171">Empacote o projeto para uma determinada [estrutura de destino](../../standard/frameworks.md):</span><span class="sxs-lookup"><span data-stu-id="68fbe-171">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

  ```console
  dotnet pack -p:TargetFrameworks=net45
  ```

* <span data-ttu-id="68fbe-172">Empacote o projeto e use um tempo de execução específico (Windows 10) para a operação de restauração (SDK do .NET Core 2.0 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="68fbe-172">Pack the project and use a specific runtime (Windows 10) for the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

  ```console
  dotnet pack --runtime win10-x64
  ```

* <span data-ttu-id="68fbe-173">Empacotar o projeto, usando um [arquivo .nuspec](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span><span class="sxs-lookup"><span data-stu-id="68fbe-173">Pack the project using a [.nuspec file](https://docs.microsoft.com/nuget/reference/msbuild-targets#packing-using-a-nuspec):</span></span>

  ```console
  dotnet pack ~/projects/app1/project.csproj /p:NuspecFile=~/projects/app1/project.nuspec /p:NuspecBasePath=~/projects/app1/nuget
  ```
