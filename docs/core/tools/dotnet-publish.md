---
title: "Comando dotnet publish – CLI do .NET Core"
description: "O comando dotnet publish publica seu projeto .NET Core em um diretório."
author: mairaw
ms.author: mairaw
ms.date: 09/01/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload: dotnetcore
ms.openlocfilehash: e29d5269ab5e9e2c9fd08811552c09ec1c95363d
ms.sourcegitcommit: 3fd4e718d1bac9769fe0c1dd08ca1b2323ae272b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/11/2018
---
# <a name="dotnet-publish"></a><span data-ttu-id="d51af-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="d51af-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="d51af-104">Nome</span><span class="sxs-lookup"><span data-stu-id="d51af-104">Name</span></span>

<span data-ttu-id="d51af-105">`dotnet publish`- Empacota o aplicativo e suas dependências em uma pasta para implantação em um sistema de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="d51af-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d51af-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="d51af-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d51af-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="d51af-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies] [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d51af-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d51af-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="d51af-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="d51af-109">Description</span></span>

<span data-ttu-id="d51af-110">`dotnet publish` compila o aplicativo, lê suas dependências especificadas no arquivo de projeto e publica o conjunto de arquivos resultantes em um diretório.</span><span class="sxs-lookup"><span data-stu-id="d51af-110">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="d51af-111">A saída conterá o seguinte:</span><span class="sxs-lookup"><span data-stu-id="d51af-111">The output will contain the following:</span></span>

* <span data-ttu-id="d51af-112">Código IL (Linguagem Intermediária) em um assembly com uma extensão *dll*.</span><span class="sxs-lookup"><span data-stu-id="d51af-112">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
* <span data-ttu-id="d51af-113">Arquivo *.deps.json* que contém todas as dependências do projeto.</span><span class="sxs-lookup"><span data-stu-id="d51af-113">*.deps.json* file that contains all of the dependencies of the project.</span></span>
* <span data-ttu-id="d51af-114">Arquivo *.runtime.config.json* que especifica o tempo de execução compartilhado esperado pelo aplicativo, bem como outras opções de configuração para o tempo de execução (por exemplo, tipo de coleta de lixo).</span><span class="sxs-lookup"><span data-stu-id="d51af-114">*.runtime.config.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="d51af-115">As dependências do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d51af-115">The application's dependencies.</span></span> <span data-ttu-id="d51af-116">Elas são copiadas do cache NuGet para a pasta de saída.</span><span class="sxs-lookup"><span data-stu-id="d51af-116">These are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="d51af-117">A saída do comando `dotnet publish` está pronta para implantação em um sistema de hospedagem (por exemplo, um servidor, PC, Mac, laptop) para execução, e é a única maneira com suporte oficial para preparar o aplicativo para implantação.</span><span class="sxs-lookup"><span data-stu-id="d51af-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution and is the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="d51af-118">Dependendo do tipo de implantação especificado pelo projeto, talvez o sistema de hospedagem não tenha o tempo de execução compartilhado do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="d51af-118">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="d51af-119">Para saber mais, confira [Implantação de aplicativos .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="d51af-119">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="d51af-120">Para a estrutura de diretórios de um aplicativo publicado, veja [Estrutura do diretório](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="d51af-120">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

## <a name="arguments"></a><span data-ttu-id="d51af-121">Arguments</span><span class="sxs-lookup"><span data-stu-id="d51af-121">Arguments</span></span>

`PROJECT`

<span data-ttu-id="d51af-122">O projeto a ser publicado, cujo padrão será o diretório atual se não for especificado.</span><span class="sxs-lookup"><span data-stu-id="d51af-122">The project to publish, which defaults to the current directory if not specified.</span></span>

## <a name="options"></a><span data-ttu-id="d51af-123">Opções</span><span class="sxs-lookup"><span data-stu-id="d51af-123">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="d51af-124">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="d51af-124">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="d51af-125">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="d51af-125">Defines the build configuration.</span></span> <span data-ttu-id="d51af-126">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="d51af-126">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d51af-127">Publica o aplicativo para a [estrutura de destino](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="d51af-127">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="d51af-128">Especifique a estrutura de destino no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="d51af-128">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="d51af-129">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="d51af-129">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="d51af-130">Isso é equivalente a excluir o arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="d51af-130">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="d51af-131">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="d51af-131">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="d51af-132">Especifica um ou vários [manifestos de destino](../deploying/runtime-store.md) a serem usados para cortar o conjunto de pacotes publicados com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d51af-132">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="d51af-133">O arquivo de manifesto faz parte da saída do [comando `dotnet store`](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="d51af-133">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="d51af-134">Para especificar vários manifestos, adicione uma opção `--manifest` para cada manifesto.</span><span class="sxs-lookup"><span data-stu-id="d51af-134">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="d51af-135">Essa opção está disponível a partir do SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="d51af-135">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="d51af-136">Ignora as referências projeto a projeto e só restaura o projeto raiz.</span><span class="sxs-lookup"><span data-stu-id="d51af-136">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="d51af-137">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="d51af-137">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d51af-138">Especifica o caminho para o diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="d51af-138">Specifies the path for the output directory.</span></span> <span data-ttu-id="d51af-139">Se não for especificado, o padrão será *./bin/[configuração]/[estrutura]/* para uma implantação dependente da estrutura, ou *./bin/[configuração]/[estrutura]/[tempo de execução]* para implantações autocontidas.</span><span class="sxs-lookup"><span data-stu-id="d51af-139">If not specified, it defaults to *./bin/[configuration]/[framework]/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]* for a self-contained deployment.</span></span>
<span data-ttu-id="d51af-140">Se um caminho relativo for fornecido, o diretório de saída gerado será relativo ao local do arquivo de projeto, não ao diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="d51af-140">If a relative path is provided, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="d51af-141">Publica o tempo de execução do .NET Core com seu aplicativo para que não seja necessário instalar o tempo de execução no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="d51af-141">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="d51af-142">Se um identificador de tempo de execução for especificado, seu valor padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="d51af-142">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="d51af-143">Para obter mais informações sobre os diferentes tipos de implantação, consulte [Implantação de aplicativos .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="d51af-143">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="d51af-144">Publica o aplicativo para um determinado tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d51af-144">Publishes the application for a given runtime.</span></span> <span data-ttu-id="d51af-145">Isso é usado ao criar uma [implantação autocontida (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="d51af-145">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="d51af-146">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="d51af-146">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="d51af-147">O padrão é publicar uma [implantação dependente da estrutura (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="d51af-147">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d51af-148">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="d51af-148">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d51af-149">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d51af-149">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="d51af-150">Define o sufixo da versão para substituir o asterisco (`*`) no campo de versão do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="d51af-150">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="d51af-151">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="d51af-151">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="d51af-152">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="d51af-152">Defines the build configuration.</span></span> <span data-ttu-id="d51af-153">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="d51af-153">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="d51af-154">Publica o aplicativo para a [estrutura de destino](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="d51af-154">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="d51af-155">Especifique a estrutura de destino no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="d51af-155">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="d51af-156">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="d51af-156">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="d51af-157">Especifica um ou vários [manifestos de destino](../deploying/runtime-store.md) a serem usados para cortar o conjunto de pacotes publicados com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="d51af-157">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="d51af-158">O arquivo de manifesto faz parte da saída do [comando `dotnet store`](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="d51af-158">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="d51af-159">Para especificar vários manifestos, adicione uma opção `--manifest` para cada manifesto.</span><span class="sxs-lookup"><span data-stu-id="d51af-159">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="d51af-160">Essa opção está disponível a partir do SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="d51af-160">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="d51af-161">Especifica o caminho para o diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="d51af-161">Specifies the path for the output directory.</span></span> <span data-ttu-id="d51af-162">Se não for especificado, o padrão será *./bin/[configuração]/[estrutura]/* para uma implantação dependente da estrutura, ou *./bin/[configuração]/[estrutura]/[tempo de execução]* para implantações autocontidas.</span><span class="sxs-lookup"><span data-stu-id="d51af-162">If not specified, it defaults to *./bin/[configuration]/[framework]/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]* for a self-contained deployment.</span></span>
<span data-ttu-id="d51af-163">Se um caminho relativo for fornecido, o diretório de saída gerado será relativo ao local do arquivo de projeto, não ao diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="d51af-163">If a relative path is provided, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="d51af-164">Publica o aplicativo para um determinado tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="d51af-164">Publishes the application for a given runtime.</span></span> <span data-ttu-id="d51af-165">Isso é usado ao criar uma [implantação autocontida (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="d51af-165">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="d51af-166">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="d51af-166">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="d51af-167">O padrão é publicar uma [implantação dependente da estrutura (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="d51af-167">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="d51af-168">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="d51af-168">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d51af-169">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d51af-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="d51af-170">Define o sufixo da versão para substituir o asterisco (`*`) no campo de versão do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="d51af-170">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="d51af-171">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d51af-171">Examples</span></span>

<span data-ttu-id="d51af-172">Publique o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="d51af-172">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="d51af-173">Publicar o aplicativo usando o arquivo de projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="d51af-173">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`
    
<span data-ttu-id="d51af-174">Publique o projeto no diretório atual usando a estrutura `netcoreapp1.1`:</span><span class="sxs-lookup"><span data-stu-id="d51af-174">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`
    
<span data-ttu-id="d51af-175">Publique o aplicativo atual usando a estrutura `netcoreapp1.1` e o tempo de execução para `OS X 10.10` (liste este RID no arquivo de projeto).</span><span class="sxs-lookup"><span data-stu-id="d51af-175">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

## <a name="see-also"></a><span data-ttu-id="d51af-176">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d51af-176">See also</span></span>

* [<span data-ttu-id="d51af-177">Estruturas de destino</span><span class="sxs-lookup"><span data-stu-id="d51af-177">Target frameworks</span></span>](../../standard/frameworks.md)
* [<span data-ttu-id="d51af-178">Catálogo de RID (Identificador de Tempo de Execução)</span><span class="sxs-lookup"><span data-stu-id="d51af-178">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
