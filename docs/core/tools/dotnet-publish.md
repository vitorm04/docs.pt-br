---
title: Comando dotnet publish – CLI do .NET Core
description: O comando dotnet publish publica seu projeto .NET Core em um diretório.
author: mairaw
ms.author: mairaw
ms.date: 05/29/2018
ms.openlocfilehash: 38224aa8472f99df107e523667e18892384a20b0
ms.sourcegitcommit: f6343b070f3c66877338a05c8bfb0be9985255e2
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/24/2018
ms.locfileid: "39220666"
---
# <a name="dotnet-publish"></a><span data-ttu-id="177db-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="177db-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="177db-104">Nome</span><span class="sxs-lookup"><span data-stu-id="177db-104">Name</span></span>

<span data-ttu-id="177db-105">`dotnet publish`- Empacota o aplicativo e suas dependências em uma pasta para implantação em um sistema de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="177db-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="177db-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="177db-106">Synopsis</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="177db-107">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="177db-107">.NET Core 2.1</span></span>](#tab/netcore21)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-build] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="177db-108">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="177db-108">.NET Core 2.0</span></span>](#tab/netcore20)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies]
    [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```
# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="177db-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="177db-109">.NET Core 1.x</span></span>](#tab/netcore1x)
```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity]
    [--version-suffix]
dotnet publish [-h|--help]
```
---

## <a name="description"></a><span data-ttu-id="177db-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="177db-110">Description</span></span>

<span data-ttu-id="177db-111">`dotnet publish` compila o aplicativo, lê suas dependências especificadas no arquivo de projeto e publica o conjunto de arquivos resultantes em um diretório.</span><span class="sxs-lookup"><span data-stu-id="177db-111">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="177db-112">A saída inclui os seguintes ativos:</span><span class="sxs-lookup"><span data-stu-id="177db-112">The output includes the following assets:</span></span>

* <span data-ttu-id="177db-113">Código IL (Linguagem Intermediária) em um assembly com uma extensão *dll*.</span><span class="sxs-lookup"><span data-stu-id="177db-113">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
* <span data-ttu-id="177db-114">Arquivo *.deps.json* que inclui todas as dependências do projeto.</span><span class="sxs-lookup"><span data-stu-id="177db-114">*.deps.json* file that includes all of the dependencies of the project.</span></span>
* <span data-ttu-id="177db-115">Arquivo *.runtime.config.json* que especifica o tempo de execução compartilhado esperado pelo aplicativo, bem como outras opções de configuração para o tempo de execução (por exemplo, tipo de coleta de lixo).</span><span class="sxs-lookup"><span data-stu-id="177db-115">*.runtime.config.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="177db-116">As dependências do aplicativo, que são copiadas do cache NuGet para a pasta de saída.</span><span class="sxs-lookup"><span data-stu-id="177db-116">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="177db-117">A saída do comando `dotnet publish` está pronta para implantação em um sistema de hospedagem (por exemplo, um servidor, um computador, um Mac, um laptop) para execução.</span><span class="sxs-lookup"><span data-stu-id="177db-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="177db-118">É a única maneira com suporte oficial de preparar o aplicativo para implantação.</span><span class="sxs-lookup"><span data-stu-id="177db-118">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="177db-119">Dependendo do tipo de implantação especificado pelo projeto, talvez o sistema de hospedagem não tenha o tempo de execução compartilhado do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="177db-119">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="177db-120">Para saber mais, confira [Implantação de aplicativos .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="177db-120">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="177db-121">Para a estrutura de diretórios de um aplicativo publicado, veja [Estrutura do diretório](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="177db-121">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="177db-122">Arguments</span><span class="sxs-lookup"><span data-stu-id="177db-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="177db-123">O projeto a ser publicado.</span><span class="sxs-lookup"><span data-stu-id="177db-123">The project to publish.</span></span> <span data-ttu-id="177db-124">Se não é especificado, ele usa como padrão o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="177db-124">If not specified, it defaults to the current directory.</span></span>

## <a name="options"></a><span data-ttu-id="177db-125">Opções</span><span class="sxs-lookup"><span data-stu-id="177db-125">Options</span></span>

# <a name="net-core-21tabnetcore21"></a>[<span data-ttu-id="177db-126">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="177db-126">.NET Core 2.1</span></span>](#tab/netcore21)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="177db-127">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="177db-127">Defines the build configuration.</span></span> <span data-ttu-id="177db-128">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="177db-128">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="177db-129">Publica o aplicativo para a [estrutura de destino](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="177db-129">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="177db-130">Especifique a estrutura de destino no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="177db-130">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="177db-131">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="177db-131">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="177db-132">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="177db-132">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="177db-133">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="177db-133">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="177db-134">Especifica um ou vários [manifestos de destino](../deploying/runtime-store.md) a serem usados para cortar o conjunto de pacotes publicados com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="177db-134">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="177db-135">O arquivo de manifesto faz parte da saída do [comando `dotnet store`](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="177db-135">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="177db-136">Para especificar vários manifestos, adicione uma opção `--manifest` para cada manifesto.</span><span class="sxs-lookup"><span data-stu-id="177db-136">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="177db-137">Essa opção está disponível a partir do SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="177db-137">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-build`

<span data-ttu-id="177db-138">Não compila o projeto antes da publicação.</span><span class="sxs-lookup"><span data-stu-id="177db-138">Doesn't build the project before publishing.</span></span> <span data-ttu-id="177db-139">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="177db-139">It also implicit sets the `--no-restore` flag.</span></span>

`--no-dependencies`

<span data-ttu-id="177db-140">Ignora as referências projeto a projeto e só restaura o projeto raiz.</span><span class="sxs-lookup"><span data-stu-id="177db-140">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="177db-141">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="177db-141">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="177db-142">Especifica o caminho para o diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="177db-142">Specifies the path for the output directory.</span></span> <span data-ttu-id="177db-143">Se não for especificado, o padrão será *./bin/[configuration]/[framework]/publish/* para uma implantação dependente da estrutura ou *./bin/[configuration]/[framework]/[runtime]/publish/* para implantações autocontidas.</span><span class="sxs-lookup"><span data-stu-id="177db-143">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="177db-144">Se o caminho for relativo, o diretório de saída gerado será relativo ao local do arquivo de projeto, não ao diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="177db-144">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="177db-145">Publica o tempo de execução do .NET Core com seu aplicativo para que não seja necessário instalar o tempo de execução no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="177db-145">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="177db-146">Se um identificador de tempo de execução for especificado, seu valor padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="177db-146">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="177db-147">Para obter mais informações sobre os diferentes tipos de implantação, consulte [Implantação de aplicativos .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="177db-147">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="177db-148">Publica o aplicativo para um determinado tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="177db-148">Publishes the application for a given runtime.</span></span> <span data-ttu-id="177db-149">Isso é usado ao criar uma [implantação autocontida (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="177db-149">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="177db-150">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="177db-150">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="177db-151">O padrão é publicar uma [implantação dependente da estrutura (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="177db-151">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="177db-152">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="177db-152">Sets the verbosity level of the command.</span></span> <span data-ttu-id="177db-153">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="177db-153">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="177db-154">Define o sufixo da versão para substituir o asterisco (`*`) no campo de versão do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="177db-154">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-20tabnetcore20"></a>[<span data-ttu-id="177db-155">.NET Core 2.0</span><span class="sxs-lookup"><span data-stu-id="177db-155">.NET Core 2.0</span></span>](#tab/netcore20)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="177db-156">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="177db-156">Defines the build configuration.</span></span> <span data-ttu-id="177db-157">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="177db-157">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="177db-158">Publica o aplicativo para a [estrutura de destino](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="177db-158">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="177db-159">Especifique a estrutura de destino no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="177db-159">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="177db-160">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="177db-160">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="177db-161">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="177db-161">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="177db-162">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="177db-162">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="177db-163">Especifica um ou vários [manifestos de destino](../deploying/runtime-store.md) a serem usados para cortar o conjunto de pacotes publicados com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="177db-163">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="177db-164">O arquivo de manifesto faz parte da saída do [comando `dotnet store`](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="177db-164">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="177db-165">Para especificar vários manifestos, adicione uma opção `--manifest` para cada manifesto.</span><span class="sxs-lookup"><span data-stu-id="177db-165">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="177db-166">Essa opção está disponível a partir do SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="177db-166">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="177db-167">Ignora as referências projeto a projeto e só restaura o projeto raiz.</span><span class="sxs-lookup"><span data-stu-id="177db-167">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="177db-168">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="177db-168">Doesn't execute an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="177db-169">Especifica o caminho para o diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="177db-169">Specifies the path for the output directory.</span></span> <span data-ttu-id="177db-170">Se não for especificado, o padrão será *./bin/[configuration]/[framework]/publish/* para uma implantação dependente da estrutura ou *./bin/[configuration]/[framework]/[runtime]/publish/* para implantações autocontidas.</span><span class="sxs-lookup"><span data-stu-id="177db-170">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="177db-171">Se o caminho for relativo, o diretório de saída gerado será relativo ao local do arquivo de projeto, não ao diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="177db-171">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="177db-172">Publica o tempo de execução do .NET Core com seu aplicativo para que não seja necessário instalar o tempo de execução no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="177db-172">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="177db-173">Se um identificador de tempo de execução for especificado, seu valor padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="177db-173">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="177db-174">Para obter mais informações sobre os diferentes tipos de implantação, consulte [Implantação de aplicativos .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="177db-174">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="177db-175">Publica o aplicativo para um determinado tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="177db-175">Publishes the application for a given runtime.</span></span> <span data-ttu-id="177db-176">Isso é usado ao criar uma [implantação autocontida (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="177db-176">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="177db-177">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="177db-177">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="177db-178">O padrão é publicar uma [implantação dependente da estrutura (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="177db-178">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="177db-179">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="177db-179">Sets the verbosity level of the command.</span></span> <span data-ttu-id="177db-180">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="177db-180">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="177db-181">Define o sufixo da versão para substituir o asterisco (`*`) no campo de versão do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="177db-181">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="177db-182">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="177db-182">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="177db-183">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="177db-183">Defines the build configuration.</span></span> <span data-ttu-id="177db-184">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="177db-184">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="177db-185">Publica o aplicativo para a [estrutura de destino](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="177db-185">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="177db-186">Especifique a estrutura de destino no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="177db-186">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="177db-187">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="177db-187">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="177db-188">Especifica um ou vários [manifestos de destino](../deploying/runtime-store.md) a serem usados para cortar o conjunto de pacotes publicados com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="177db-188">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="177db-189">O arquivo de manifesto faz parte da saída do [comando `dotnet store`](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="177db-189">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="177db-190">Para especificar vários manifestos, adicione uma opção `--manifest` para cada manifesto.</span><span class="sxs-lookup"><span data-stu-id="177db-190">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="177db-191">Essa opção está disponível a partir do SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="177db-191">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="177db-192">Especifica o caminho para o diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="177db-192">Specifies the path for the output directory.</span></span> <span data-ttu-id="177db-193">Se não for especificado, o padrão será *./bin/[configuration]/[framework]/publish/* para uma implantação dependente da estrutura ou *./bin/[configuration]/[framework]/[runtime]/publish/* para implantações autocontidas.</span><span class="sxs-lookup"><span data-stu-id="177db-193">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained deployment.</span></span>
<span data-ttu-id="177db-194">Se o caminho for relativo, o diretório de saída gerado será relativo ao local do arquivo de projeto, não ao diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="177db-194">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="177db-195">Publica o aplicativo para um determinado tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="177db-195">Publishes the application for a given runtime.</span></span> <span data-ttu-id="177db-196">Isso é usado ao criar uma [implantação autocontida (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="177db-196">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="177db-197">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="177db-197">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="177db-198">O padrão é publicar uma [implantação dependente da estrutura (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="177db-198">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="177db-199">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="177db-199">Sets the verbosity level of the command.</span></span> <span data-ttu-id="177db-200">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="177db-200">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="177db-201">Define o sufixo da versão para substituir o asterisco (`*`) no campo de versão do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="177db-201">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="177db-202">Exemplos</span><span class="sxs-lookup"><span data-stu-id="177db-202">Examples</span></span>

<span data-ttu-id="177db-203">Publique o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="177db-203">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="177db-204">Publicar o aplicativo usando o arquivo de projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="177db-204">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="177db-205">Publique o projeto no diretório atual usando a estrutura `netcoreapp1.1`:</span><span class="sxs-lookup"><span data-stu-id="177db-205">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="177db-206">Publique o aplicativo atual usando a estrutura `netcoreapp1.1` e o tempo de execução para `OS X 10.10` (liste este RID no arquivo de projeto).</span><span class="sxs-lookup"><span data-stu-id="177db-206">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="177db-207">Publique o aplicativo atual, mas não restaure as referências P2P (projeto a projeto), apenas o projeto raiz durante a operação de restauração (SDK do .NET Core 2.0 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="177db-207">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="177db-208">Consulte também</span><span class="sxs-lookup"><span data-stu-id="177db-208">See also</span></span>

* [<span data-ttu-id="177db-209">Estruturas de destino</span><span class="sxs-lookup"><span data-stu-id="177db-209">Target frameworks</span></span>](../../standard/frameworks.md)
* [<span data-ttu-id="177db-210">Catálogo de RID (Identificador de Tempo de Execução)</span><span class="sxs-lookup"><span data-stu-id="177db-210">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
