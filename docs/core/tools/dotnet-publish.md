---
title: Comando dotnet publish
description: O comando dotnet publish publica seu projeto .NET Core em um diretório.
ms.date: 05/29/2018
ms.openlocfilehash: 4612c8cd1f63550905ef7c6d94af050892b1620c
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117618"
---
# <a name="dotnet-publish"></a><span data-ttu-id="98f4e-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="98f4e-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="98f4e-104">Nome</span><span class="sxs-lookup"><span data-stu-id="98f4e-104">Name</span></span>

<span data-ttu-id="98f4e-105">`dotnet publish`- Empacota o aplicativo e suas dependências em uma pasta para implantação em um sistema de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="98f4e-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="98f4e-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="98f4e-106">Synopsis</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="98f4e-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="98f4e-107">.NET Core 2.1</span></span>](#tab/netcore21)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="98f4e-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="98f4e-108">.NET Core 2.0</span></span>](#tab/netcore20)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="98f4e-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="98f4e-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```dotnetcli
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="98f4e-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="98f4e-110">Description</span></span>

<span data-ttu-id="98f4e-111">`dotnet publish` compila o aplicativo, lê suas dependências especificadas no arquivo de projeto e publica o conjunto de arquivos resultantes em um diretório.</span><span class="sxs-lookup"><span data-stu-id="98f4e-111">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="98f4e-112">A saída inclui os seguintes ativos:</span><span class="sxs-lookup"><span data-stu-id="98f4e-112">The output includes the following assets:</span></span>

- <span data-ttu-id="98f4e-113">Código IL (Linguagem Intermediária) em um assembly com uma extensão *dll*.</span><span class="sxs-lookup"><span data-stu-id="98f4e-113">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="98f4e-114">Arquivo *.deps.json* que inclui todas as dependências do projeto.</span><span class="sxs-lookup"><span data-stu-id="98f4e-114">*.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="98f4e-115">O arquivo *.runtimeconfig.json* que especifica o tempo de execução compartilhado esperado pelo aplicativo, bem como outras opções de configuração para o tempo de execução (por exemplo, tipo de coleta de lixo).</span><span class="sxs-lookup"><span data-stu-id="98f4e-115">*.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="98f4e-116">As dependências do aplicativo, que são copiadas do cache NuGet para a pasta de saída.</span><span class="sxs-lookup"><span data-stu-id="98f4e-116">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="98f4e-117">A saída do comando `dotnet publish` está pronta para implantação em um sistema de hospedagem (por exemplo, um servidor, um computador, um Mac, um laptop) para execução.</span><span class="sxs-lookup"><span data-stu-id="98f4e-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="98f4e-118">É a única maneira com suporte oficial de preparar o aplicativo para implantação.</span><span class="sxs-lookup"><span data-stu-id="98f4e-118">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="98f4e-119">Dependendo do tipo de implantação especificado pelo projeto, talvez o sistema de hospedagem não tenha o tempo de execução compartilhado do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="98f4e-119">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="98f4e-120">Para saber mais, confira [Implantação de aplicativos .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="98f4e-120">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="98f4e-121">Para a estrutura de diretórios de um aplicativo publicado, veja [Estrutura do diretório](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="98f4e-121">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="98f4e-122">Arguments</span><span class="sxs-lookup"><span data-stu-id="98f4e-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="98f4e-123">O projeto a ser publicado.</span><span class="sxs-lookup"><span data-stu-id="98f4e-123">The project to publish.</span></span> <span data-ttu-id="98f4e-124">É o caminho e o nome de arquivo de um arquivo de projeto [C#](csproj.md), F# ou do Visual Basic ou o caminho para um diretório que contém um arquivo de projeto C#, F# ou do Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="98f4e-124">It's either the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="98f4e-125">Se não é especificado, ele usa como padrão o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="98f4e-125">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="98f4e-126">Opções</span><span class="sxs-lookup"><span data-stu-id="98f4e-126">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="98f4e-127">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="98f4e-127">.NET Core 2.1</span></span>](#tab/netcore21)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="98f4e-128">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="98f4e-128">Defines the build configuration.</span></span> <span data-ttu-id="98f4e-129">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="98f4e-129">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="98f4e-130">Publica o aplicativo para a [estrutura de destino](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="98f4e-130">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="98f4e-131">Especifique a estrutura de destino no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="98f4e-131">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="98f4e-132">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="98f4e-132">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="98f4e-133">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="98f4e-133">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="98f4e-134">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="98f4e-134">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="98f4e-135">Especifica um ou vários [manifestos de destino](../deploying/runtime-store.md) a serem usados para cortar o conjunto de pacotes publicados com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="98f4e-135">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="98f4e-136">O arquivo de manifesto faz parte da saída do [comando `dotnet store`](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="98f4e-136">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="98f4e-137">Para especificar vários manifestos, adicione uma opção `--manifest` para cada manifesto.</span><span class="sxs-lookup"><span data-stu-id="98f4e-137">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="98f4e-138">Essa opção está disponível a partir do SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="98f4e-138">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-build`

<span data-ttu-id="98f4e-139">Não compila o projeto antes da publicação.</span><span class="sxs-lookup"><span data-stu-id="98f4e-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="98f4e-140">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="98f4e-140">It also implicitly sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="98f4e-141">Ignora as referências projeto a projeto e só restaura o projeto raiz.</span><span class="sxs-lookup"><span data-stu-id="98f4e-141">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="98f4e-142">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="98f4e-142">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="98f4e-143">Especifica o caminho para o diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="98f4e-143">Specifies the path for the output directory.</span></span> <span data-ttu-id="98f4e-144">Se não for especificado, o padrão será *./bin/[configuration]/[framework]/publish/* para uma implantação dependente da estrutura ou *./bin/[configuration]/[framework]/[runtime]/publish/* para implantações autocontidas.</span><span class="sxs-lookup"><span data-stu-id="98f4e-144">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="98f4e-145">Se o caminho for relativo, o diretório de saída gerado será relativo ao local do arquivo de projeto, não ao diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="98f4e-145">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="98f4e-146">Publica o tempo de execução do .NET Core com seu aplicativo para que não seja necessário instalar o tempo de execução no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="98f4e-146">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="98f4e-147">Se um identificador de tempo de execução for especificado, seu valor padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="98f4e-147">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="98f4e-148">Para obter mais informações sobre os diferentes tipos de implantação, consulte [Implantação de aplicativos .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="98f4e-148">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="98f4e-149">Publica o aplicativo para um determinado tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="98f4e-149">Publishes the application for a given runtime.</span></span> <span data-ttu-id="98f4e-150">Isso é usado ao criar uma [implantação autocontida (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="98f4e-150">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="98f4e-151">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="98f4e-151">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="98f4e-152">O padrão é publicar uma [implantação dependente da estrutura (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="98f4e-152">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="98f4e-153">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="98f4e-153">Sets the verbosity level of the command.</span></span> <span data-ttu-id="98f4e-154">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="98f4e-154">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="98f4e-155">Define o sufixo da versão para substituir o asterisco (`*`) no campo de versão do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="98f4e-155">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="98f4e-156">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="98f4e-156">.NET Core 2.0</span></span>](#tab/netcore20)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="98f4e-157">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="98f4e-157">Defines the build configuration.</span></span> <span data-ttu-id="98f4e-158">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="98f4e-158">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="98f4e-159">Publica o aplicativo para a [estrutura de destino](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="98f4e-159">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="98f4e-160">Especifique a estrutura de destino no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="98f4e-160">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="98f4e-161">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="98f4e-161">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="98f4e-162">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="98f4e-162">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="98f4e-163">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="98f4e-163">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="98f4e-164">Especifica um ou vários [manifestos de destino](../deploying/runtime-store.md) a serem usados para cortar o conjunto de pacotes publicados com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="98f4e-164">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="98f4e-165">O arquivo de manifesto faz parte da saída do [comando `dotnet store`](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="98f4e-165">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="98f4e-166">Para especificar vários manifestos, adicione uma opção `--manifest` para cada manifesto.</span><span class="sxs-lookup"><span data-stu-id="98f4e-166">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="98f4e-167">Essa opção está disponível a partir do SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="98f4e-167">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="98f4e-168">Ignora as referências projeto a projeto e só restaura o projeto raiz.</span><span class="sxs-lookup"><span data-stu-id="98f4e-168">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="98f4e-169">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="98f4e-169">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="98f4e-170">Especifica o caminho para o diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="98f4e-170">Specifies the path for the output directory.</span></span> <span data-ttu-id="98f4e-171">Se não for especificado, o padrão será *./bin/[configuration]/[framework]/publish/* para uma implantação dependente da estrutura ou *./bin/[configuration]/[framework]/[runtime]/publish/* para implantações autocontidas.</span><span class="sxs-lookup"><span data-stu-id="98f4e-171">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="98f4e-172">Se o caminho for relativo, o diretório de saída gerado será relativo ao local do arquivo de projeto, não ao diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="98f4e-172">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="98f4e-173">Publica o tempo de execução do .NET Core com seu aplicativo para que não seja necessário instalar o tempo de execução no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="98f4e-173">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="98f4e-174">Se um identificador de tempo de execução for especificado, seu valor padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="98f4e-174">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="98f4e-175">Para obter mais informações sobre os diferentes tipos de implantação, consulte [Implantação de aplicativos .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="98f4e-175">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="98f4e-176">Publica o aplicativo para um determinado tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="98f4e-176">Publishes the application for a given runtime.</span></span> <span data-ttu-id="98f4e-177">Isso é usado ao criar uma [implantação autocontida (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="98f4e-177">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="98f4e-178">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="98f4e-178">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="98f4e-179">O padrão é publicar uma [implantação dependente da estrutura (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="98f4e-179">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="98f4e-180">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="98f4e-180">Sets the verbosity level of the command.</span></span> <span data-ttu-id="98f4e-181">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="98f4e-181">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="98f4e-182">Define o sufixo da versão para substituir o asterisco (`*`) no campo de versão do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="98f4e-182">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="98f4e-183">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="98f4e-183">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="98f4e-184">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="98f4e-184">Defines the build configuration.</span></span> <span data-ttu-id="98f4e-185">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="98f4e-185">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="98f4e-186">Publica o aplicativo para a [estrutura de destino](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="98f4e-186">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="98f4e-187">Especifique a estrutura de destino no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="98f4e-187">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="98f4e-188">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="98f4e-188">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="98f4e-189">Especifica um ou vários [manifestos de destino](../deploying/runtime-store.md) a serem usados para cortar o conjunto de pacotes publicados com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="98f4e-189">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="98f4e-190">O arquivo de manifesto faz parte da saída do [comando `dotnet store`](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="98f4e-190">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="98f4e-191">Para especificar vários manifestos, adicione uma opção `--manifest` para cada manifesto.</span><span class="sxs-lookup"><span data-stu-id="98f4e-191">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="98f4e-192">Essa opção está disponível a partir do SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="98f4e-192">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="98f4e-193">Especifica o caminho para o diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="98f4e-193">Specifies the path for the output directory.</span></span> <span data-ttu-id="98f4e-194">Se não for especificado, o padrão será *./bin/[configuration]/[framework]/publish/* para uma implantação dependente da estrutura ou *./bin/[configuration]/[framework]/[runtime]/publish/* para implantações autocontidas.</span><span class="sxs-lookup"><span data-stu-id="98f4e-194">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="98f4e-195">Se o caminho for relativo, o diretório de saída gerado será relativo ao local do arquivo de projeto, não ao diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="98f4e-195">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="98f4e-196">Publica o aplicativo para um determinado tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="98f4e-196">Publishes the application for a given runtime.</span></span> <span data-ttu-id="98f4e-197">Isso é usado ao criar uma [implantação autocontida (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="98f4e-197">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="98f4e-198">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="98f4e-198">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="98f4e-199">O padrão é publicar uma [implantação dependente da estrutura (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="98f4e-199">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="98f4e-200">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="98f4e-200">Sets the verbosity level of the command.</span></span> <span data-ttu-id="98f4e-201">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="98f4e-201">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="98f4e-202">Define o sufixo da versão para substituir o asterisco (`*`) no campo de versão do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="98f4e-202">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="98f4e-203">Exemplos</span><span class="sxs-lookup"><span data-stu-id="98f4e-203">Examples</span></span>

<span data-ttu-id="98f4e-204">Publique o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="98f4e-204">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="98f4e-205">Publicar o aplicativo usando o arquivo de projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="98f4e-205">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="98f4e-206">Publique o projeto no diretório atual usando a estrutura `netcoreapp1.1`:</span><span class="sxs-lookup"><span data-stu-id="98f4e-206">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="98f4e-207">Publique o aplicativo atual usando a estrutura `netcoreapp1.1` e o tempo de execução para `OS X 10.10` (liste este RID no arquivo de projeto).</span><span class="sxs-lookup"><span data-stu-id="98f4e-207">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="98f4e-208">Publique o aplicativo atual, mas não restaure as referências P2P (projeto a projeto), apenas o projeto raiz durante a operação de restauração (SDK do .NET Core 2.0 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="98f4e-208">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="98f4e-209">Consulte também</span><span class="sxs-lookup"><span data-stu-id="98f4e-209">See also</span></span>

- [<span data-ttu-id="98f4e-210">Estruturas de destino</span><span class="sxs-lookup"><span data-stu-id="98f4e-210">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="98f4e-211">Catálogo de RID (Identificador de Tempo de Execução)</span><span class="sxs-lookup"><span data-stu-id="98f4e-211">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
