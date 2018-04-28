---
title: Comando dotnet pack – CLI do .NET Core
description: O comando dotnet pack cria pacotes NuGet para seu projeto .NET Core.
author: mairaw
ms.author: mairaw
ms.date: 03/10/2018
ms.topic: conceptual
ms.prod: dotnet-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: fdbf3b23813f09ad9902f6b0457f176139b405a4
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="dotnet-pack"></a><span data-ttu-id="a08d4-103">dotnet pack</span><span class="sxs-lookup"><span data-stu-id="a08d4-103">dotnet pack</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="a08d4-104">Nome</span><span class="sxs-lookup"><span data-stu-id="a08d4-104">Name</span></span>

<span data-ttu-id="a08d4-105">`dotnet pack` – Empacota o código em um pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="a08d4-105">`dotnet pack` - Packs the code into a NuGet package.</span></span>

## <a name="synopsis"></a><span data-ttu-id="a08d4-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="a08d4-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="a08d4-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="a08d4-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet pack [<PROJECT>] [-c|--configuration] [--force] [--include-source] [--include-symbols] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [--runtime] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a08d4-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a08d4-108">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet pack [<PROJECT>] [-c|--configuration] [--include-source] [--include-symbols] [--no-build] [-o|--output] [-s|--serviceable] [-v|--verbosity] [--version-suffix]
dotnet pack [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="a08d4-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="a08d4-109">Description</span></span>

<span data-ttu-id="a08d4-110">O comando `dotnet pack` compila o projeto e cria pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="a08d4-110">The `dotnet pack` command builds the project and creates NuGet packages.</span></span> <span data-ttu-id="a08d4-111">O resultado desse comando é um pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="a08d4-111">The result of this command is a NuGet package.</span></span> <span data-ttu-id="a08d4-112">Se a opção `--include-symbols` estiver presente, outro pacote que contém os símbolos de depuração será criado.</span><span class="sxs-lookup"><span data-stu-id="a08d4-112">If the `--include-symbols` option is present, another package containing the debug symbols is created.</span></span>

<span data-ttu-id="a08d4-113">As dependências do NuGet do projeto empacotado são adicionadas ao arquivo *.nuspec* para que possam ser resolvidas apropriadamente quando o pacote for instalado.</span><span class="sxs-lookup"><span data-stu-id="a08d4-113">NuGet dependencies of the packed project are added to the *.nuspec* file, so they're properly resolved when the package is installed.</span></span> <span data-ttu-id="a08d4-114">As referências de projeto a projeto não são empacotadas dentro do projeto.</span><span class="sxs-lookup"><span data-stu-id="a08d4-114">Project-to-project references aren't packaged inside the project.</span></span> <span data-ttu-id="a08d4-115">No momento, você precisa ter um pacote por projeto se tiver dependências de projeto a projeto.</span><span class="sxs-lookup"><span data-stu-id="a08d4-115">Currently, you must have a package per project if you have project-to-project dependencies.</span></span>

<span data-ttu-id="a08d4-116">Por padrão, `dotnet pack` compila primeiro o projeto.</span><span class="sxs-lookup"><span data-stu-id="a08d4-116">By default, `dotnet pack` builds the project first.</span></span> <span data-ttu-id="a08d4-117">Se você quiser evitar esse comportamento, passe a opção `--no-build`.</span><span class="sxs-lookup"><span data-stu-id="a08d4-117">If you wish to avoid this behavior, pass the `--no-build` option.</span></span> <span data-ttu-id="a08d4-118">Com frequência, isso é útil em cenários de criação de CI (Integração Contínua) nos quais você sabe que o código foi compilado anteriormente.</span><span class="sxs-lookup"><span data-stu-id="a08d4-118">This is often useful in Continuous Integration (CI) build scenarios where you know the code was previously built.</span></span>

<span data-ttu-id="a08d4-119">Você pode fornecer as propriedades de MSBuild para o comando `dotnet pack` para o processo de empacotamento.</span><span class="sxs-lookup"><span data-stu-id="a08d4-119">You can provide MSBuild properties to the `dotnet pack` command for the packing process.</span></span> <span data-ttu-id="a08d4-120">Para obter mais informações, consulte [Propriedades de metadados do NuGet](csproj.md#nuget-metadata-properties) e a [Referência de linha de comando MSBuild](/visualstudio/msbuild/msbuild-command-line-reference).</span><span class="sxs-lookup"><span data-stu-id="a08d4-120">For more information, see [NuGet metadata properties](csproj.md#nuget-metadata-properties) and the [MSBuild Command-Line Reference](/visualstudio/msbuild/msbuild-command-line-reference).</span></span> <span data-ttu-id="a08d4-121">A seção [Exemplos](#examples) mostra como usar a opção /p do MSBuild para alguns cenários diferentes.</span><span class="sxs-lookup"><span data-stu-id="a08d4-121">The [Examples](#examples) section shows how to use the MSBuild /p switch for a couple of different scenarios.</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="a08d4-122">Arguments</span><span class="sxs-lookup"><span data-stu-id="a08d4-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="a08d4-123">O projeto a ser empacotado.</span><span class="sxs-lookup"><span data-stu-id="a08d4-123">The project to pack.</span></span> <span data-ttu-id="a08d4-124">Pode ser um caminho para um [arquivo csproj](csproj.md) ou para um diretório.</span><span class="sxs-lookup"><span data-stu-id="a08d4-124">It's either a path to a [csproj file](csproj.md) or to a directory.</span></span> <span data-ttu-id="a08d4-125">Se for omitido, o padrão será o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="a08d4-125">If omitted, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="a08d4-126">Opções</span><span class="sxs-lookup"><span data-stu-id="a08d4-126">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="a08d4-127">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="a08d4-127">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="a08d4-128">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="a08d4-128">Defines the build configuration.</span></span> <span data-ttu-id="a08d4-129">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="a08d4-129">The default value is `Debug`.</span></span>

<span data-ttu-id="a08d4-130">`--force` Forçará todas as dependências a serem resolvidas mesmo se a última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="a08d4-130">`--force` Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="a08d4-131">Isso é equivalente a excluir o arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="a08d4-131">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="a08d4-132">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="a08d4-132">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="a08d4-133">Inclui os arquivos de origem no pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="a08d4-133">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="a08d4-134">Os arquivos de origem são incluídos na pasta `src` dentro de `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="a08d4-134">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="a08d4-135">Gera os símbolos `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="a08d4-135">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="a08d4-136">Não compila o projeto antes do empacotamento.</span><span class="sxs-lookup"><span data-stu-id="a08d4-136">Doesn't build the project before packing.</span></span>

`--no-dependencies`

<span data-ttu-id="a08d4-137">Ignora as referências projeto a projeto e só restaura o projeto raiz.</span><span class="sxs-lookup"><span data-stu-id="a08d4-137">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="a08d4-138">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="a08d4-138">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="a08d4-139">Coloca os pacotes compilados no diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="a08d4-139">Places the built packages in the directory specified.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="a08d4-140">Especifica o tempo de execução de destino para o qual restaurar os pacotes.</span><span class="sxs-lookup"><span data-stu-id="a08d4-140">Specifies the target runtime to restore packages for.</span></span> <span data-ttu-id="a08d4-141">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="a08d4-141">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span>

`-s|--serviceable`

<span data-ttu-id="a08d4-142">Define o sinalizador operacional no pacote.</span><span class="sxs-lookup"><span data-stu-id="a08d4-142">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="a08d4-143">Para saber mais, veja [Blog do .NET: .NET 4.5.1 oferece suporte às Atualizações de segurança da Microsoft para Bibliotecas do .NET NuGet](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="a08d4-143">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="a08d4-144">Define o valor da propriedade do MSBuild `$(VersionSuffix)` no projeto.</span><span class="sxs-lookup"><span data-stu-id="a08d4-144">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a08d4-145">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="a08d4-145">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a08d4-146">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a08d4-146">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="a08d4-147">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="a08d4-147">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="a08d4-148">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="a08d4-148">Defines the build configuration.</span></span> <span data-ttu-id="a08d4-149">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="a08d4-149">The default value is `Debug`.</span></span>

`-h|--help`

<span data-ttu-id="a08d4-150">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="a08d4-150">Prints out a short help for the command.</span></span>

`--include-source`

<span data-ttu-id="a08d4-151">Inclui os arquivos de origem no pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="a08d4-151">Includes the source files in the NuGet package.</span></span> <span data-ttu-id="a08d4-152">Os arquivos de origem são incluídos na pasta `src` dentro de `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="a08d4-152">The sources files are included in the `src` folder within the `nupkg`.</span></span>

`--include-symbols`

<span data-ttu-id="a08d4-153">Gera os símbolos `nupkg`.</span><span class="sxs-lookup"><span data-stu-id="a08d4-153">Generates the symbols `nupkg`.</span></span>

`--no-build`

<span data-ttu-id="a08d4-154">Não compila o projeto antes do empacotamento.</span><span class="sxs-lookup"><span data-stu-id="a08d4-154">Doesn't build the project before packing.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="a08d4-155">Coloca os pacotes compilados no diretório especificado.</span><span class="sxs-lookup"><span data-stu-id="a08d4-155">Places the built packages in the directory specified.</span></span>

`-s|--serviceable`

<span data-ttu-id="a08d4-156">Define o sinalizador operacional no pacote.</span><span class="sxs-lookup"><span data-stu-id="a08d4-156">Sets the serviceable flag in the package.</span></span> <span data-ttu-id="a08d4-157">Para saber mais, veja [Blog do .NET: .NET 4.5.1 oferece suporte às Atualizações de segurança da Microsoft para Bibliotecas do .NET NuGet](https://aka.ms/nupkgservicing).</span><span class="sxs-lookup"><span data-stu-id="a08d4-157">For more information, see [.NET Blog: .NET 4.5.1 Supports Microsoft Security Updates for .NET NuGet Libraries](https://aka.ms/nupkgservicing).</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="a08d4-158">Define o valor da propriedade do MSBuild `$(VersionSuffix)` no projeto.</span><span class="sxs-lookup"><span data-stu-id="a08d4-158">Defines the value for the `$(VersionSuffix)` MSBuild property in the project.</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="a08d4-159">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="a08d4-159">Sets the verbosity level of the command.</span></span> <span data-ttu-id="a08d4-160">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="a08d4-160">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

---

## <a name="examples"></a><span data-ttu-id="a08d4-161">Exemplos</span><span class="sxs-lookup"><span data-stu-id="a08d4-161">Examples</span></span>

<span data-ttu-id="a08d4-162">Empacota o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="a08d4-162">Pack the project in the current directory:</span></span>

`dotnet pack`

<span data-ttu-id="a08d4-163">Empacote o projeto `app1`:</span><span class="sxs-lookup"><span data-stu-id="a08d4-163">Pack the `app1` project:</span></span>

`dotnet pack ~/projects/app1/project.csproj`

<span data-ttu-id="a08d4-164">Empacote o projeto no diretório atual e coloque os pacotes resultantes na pasta`nupkgs`:</span><span class="sxs-lookup"><span data-stu-id="a08d4-164">Pack the project in the current directory and place the resulting packages into the `nupkgs` folder:</span></span>

`dotnet pack --output nupkgs`

<span data-ttu-id="a08d4-165">Empacote o projeto no diretório atual da pasta `nupkgs` e ignora a etapa de compilação:</span><span class="sxs-lookup"><span data-stu-id="a08d4-165">Pack the project in the current directory into the `nupkgs` folder and skip the build step:</span></span>

`dotnet pack --no-build --output nupkgs`

<span data-ttu-id="a08d4-166">Com o sufixo da versão do projeto configurado como `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` no arquivo *.csproj*, empacote o projeto atual e atualize a versão do pacote resultante com o sufixo especificado:</span><span class="sxs-lookup"><span data-stu-id="a08d4-166">With the project's version suffix configured as `<VersionSuffix>$(VersionSuffix)</VersionSuffix>` in the *.csproj* file, pack the current project and update the resulting package version with the given suffix:</span></span>

`dotnet pack --version-suffix "ci-1234"`

<span data-ttu-id="a08d4-167">Defina a versão do pacote como `2.1.0` com a propriedade MSBuild `PackageVersion`:</span><span class="sxs-lookup"><span data-stu-id="a08d4-167">Set the package version to `2.1.0` with the `PackageVersion` MSBuild property:</span></span>

`dotnet pack /p:PackageVersion=2.1.0`

<span data-ttu-id="a08d4-168">Empacote o projeto para uma determinada [estrutura de destino](../../standard/frameworks.md):</span><span class="sxs-lookup"><span data-stu-id="a08d4-168">Pack the project for a specific [target framework](../../standard/frameworks.md):</span></span>

`dotnet pack /p:TargetFrameworks=net45`

<span data-ttu-id="a08d4-169">Empacote o projeto e use um tempo de execução específico (Windows 10) para a operação de restauração (SDK do .NET Core 2.0 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="a08d4-169">Pack the project and use a specific runtime (Windows 10) for the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet pack --runtime win10-x64`