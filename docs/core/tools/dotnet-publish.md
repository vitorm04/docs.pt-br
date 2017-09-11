---
title: "Comando dotnet publish – CLI do .NET Core"
description: "O comando dotnet publish publica seu projeto .NET Core em um diretório."
keywords: dotnet-publish, CLI, comando da CLI, .NET Core
author: blackdwarf
ms.author: mairaw
ms.date: 08/12/2017
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.devlang: dotnet
ms.assetid: f2ef275a-7c5e-430a-8c30-65f52af62771
ms.translationtype: HT
ms.sourcegitcommit: a19ab54a6cc44bd7acd1e40a4ca94da52bf14297
ms.openlocfilehash: db6e527a6132be0b6362c68945bb68884f5ad619
ms.contentlocale: pt-br
ms.lasthandoff: 08/14/2017

---
# <a name="dotnet-publish"></a><span data-ttu-id="4c37c-104">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="4c37c-104">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="4c37c-105">Nome</span><span class="sxs-lookup"><span data-stu-id="4c37c-105">Name</span></span>

<span data-ttu-id="4c37c-106">`dotnet publish`- Empacota o aplicativo e suas dependências em uma pasta para implantação em um sistema de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="4c37c-106">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="4c37c-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="4c37c-107">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="4c37c-108">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="4c37c-108">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [no-dependencies] [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4c37c-109">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4c37c-109">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="4c37c-110">Descrição</span><span class="sxs-lookup"><span data-stu-id="4c37c-110">Description</span></span>

<span data-ttu-id="4c37c-111">`dotnet publish` compila o aplicativo, lê suas dependências especificadas no arquivo de projeto e publica o conjunto de arquivos resultantes em um diretório.</span><span class="sxs-lookup"><span data-stu-id="4c37c-111">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="4c37c-112">A saída conterá o seguinte:</span><span class="sxs-lookup"><span data-stu-id="4c37c-112">The output will contain the following:</span></span>

* <span data-ttu-id="4c37c-113">Código IL (Linguagem Intermediária) em um assembly com uma extensão *dll*.</span><span class="sxs-lookup"><span data-stu-id="4c37c-113">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
* <span data-ttu-id="4c37c-114">Arquivo *.deps.json* que contém todas as dependências do projeto.</span><span class="sxs-lookup"><span data-stu-id="4c37c-114">*.deps.json* file that contains all of the dependencies of the project.</span></span>
* <span data-ttu-id="4c37c-115">Arquivo *.runtime.config.json* que especifica o tempo de execução compartilhado esperado pelo aplicativo, bem como outras opções de configuração para o tempo de execução (por exemplo, tipo de coleta de lixo).</span><span class="sxs-lookup"><span data-stu-id="4c37c-115">*.runtime.config.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="4c37c-116">As dependências do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4c37c-116">The application's dependencies.</span></span> <span data-ttu-id="4c37c-117">Elas são copiadas do cache NuGet para a pasta de saída.</span><span class="sxs-lookup"><span data-stu-id="4c37c-117">These are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="4c37c-118">A saída do comando `dotnet publish` está pronta para implantação em um sistema de hospedagem (por exemplo, um servidor, PC, Mac, laptop) para execução, e é a única maneira com suporte oficial para preparar o aplicativo para implantação.</span><span class="sxs-lookup"><span data-stu-id="4c37c-118">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution and is the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="4c37c-119">Dependendo do tipo de implantação especificado pelo projeto, talvez o sistema de hospedagem não tenha o tempo de execução compartilhado do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="4c37c-119">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="4c37c-120">Para saber mais, confira [Implantação de aplicativos .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="4c37c-120">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="4c37c-121">Para a estrutura de diretórios de um aplicativo publicado, veja [Estrutura do diretório](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="4c37c-121">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

## <a name="arguments"></a><span data-ttu-id="4c37c-122">Arguments</span><span class="sxs-lookup"><span data-stu-id="4c37c-122">Arguments</span></span>

`PROJECT`

<span data-ttu-id="4c37c-123">O projeto a ser publicado, cujo padrão será o diretório atual se não for especificado.</span><span class="sxs-lookup"><span data-stu-id="4c37c-123">The project to publish, which defaults to the current directory if not specified.</span></span>

## <a name="options"></a><span data-ttu-id="4c37c-124">Opções</span><span class="sxs-lookup"><span data-stu-id="4c37c-124">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="4c37c-125">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="4c37c-125">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="4c37c-126">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="4c37c-126">Defines the build configuration.</span></span> <span data-ttu-id="4c37c-127">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="4c37c-127">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="4c37c-128">Publica o aplicativo para a [estrutura de destino](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="4c37c-128">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="4c37c-129">Especifique a estrutura de destino no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="4c37c-129">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="4c37c-130">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="4c37c-130">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="4c37c-131">Isso é equivalente a excluir o arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="4c37c-131">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="4c37c-132">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="4c37c-132">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="4c37c-133">Especifica um ou vários [manifestos de destino](../deploying/runtime-store.md) a serem usados para cortar o conjunto de pacotes publicados com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4c37c-133">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="4c37c-134">O arquivo de manifesto faz parte da saída do [comando `dotnet store`](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="4c37c-134">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="4c37c-135">Para especificar vários manifestos, adicione uma opção `--manifest` para cada manifesto.</span><span class="sxs-lookup"><span data-stu-id="4c37c-135">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="4c37c-136">Essa opção está disponível a partir do SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="4c37c-136">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="4c37c-137">Ignora as referências projeto a projeto e só restaura o projeto raiz.</span><span class="sxs-lookup"><span data-stu-id="4c37c-137">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="4c37c-138">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="4c37c-138">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4c37c-139">Especifica o caminho para o diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="4c37c-139">Specifies the path for the output directory.</span></span> <span data-ttu-id="4c37c-140">Se não for especificado, o padrão será *./bin/[configuração]/[estrutura]/* para uma implantação dependente da estrutura, ou *./bin/[configuração]/[estrutura]/[tempo de execução]* para implantações autocontidas.</span><span class="sxs-lookup"><span data-stu-id="4c37c-140">If not specified, it defaults to *./bin/[configuration]/[framework]/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]* for a self-contained deployment.</span></span>

`--self-contained`

<span data-ttu-id="4c37c-141">Publica o tempo de execução do .NET Core com seu aplicativo para que não seja necessário instalar o tempo de execução no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="4c37c-141">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="4c37c-142">Se um identificador de tempo de execução for especificado, seu valor padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="4c37c-142">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="4c37c-143">Para obter mais informações sobre os diferentes tipos de implantação, consulte [.NET Core application deployment](../deploying/index.md) (Implantação de aplicativos .NET Core).</span><span class="sxs-lookup"><span data-stu-id="4c37c-143">For more infomation about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="4c37c-144">Publica o aplicativo para um determinado tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4c37c-144">Publishes the application for a given runtime.</span></span> <span data-ttu-id="4c37c-145">Isso é usado ao criar uma [implantação autocontida (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="4c37c-145">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="4c37c-146">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="4c37c-146">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="4c37c-147">O padrão é publicar uma [implantação dependente da estrutura (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="4c37c-147">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="4c37c-148">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="4c37c-148">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4c37c-149">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="4c37c-149">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="4c37c-150">Define o sufixo da versão para substituir o asterisco (`*`) no campo de versão do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="4c37c-150">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="4c37c-151">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="4c37c-151">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="4c37c-152">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="4c37c-152">Defines the build configuration.</span></span> <span data-ttu-id="4c37c-153">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="4c37c-153">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="4c37c-154">Publica o aplicativo para a [estrutura de destino](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="4c37c-154">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="4c37c-155">Especifique a estrutura de destino no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="4c37c-155">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="4c37c-156">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="4c37c-156">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="4c37c-157">Especifica um ou vários [manifestos de destino](../deploying/runtime-store.md) a serem usados para cortar o conjunto de pacotes publicados com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="4c37c-157">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="4c37c-158">O arquivo de manifesto faz parte da saída do [comando `dotnet store`](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="4c37c-158">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="4c37c-159">Para especificar vários manifestos, adicione uma opção `--manifest` para cada manifesto.</span><span class="sxs-lookup"><span data-stu-id="4c37c-159">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="4c37c-160">Essa opção está disponível a partir do SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="4c37c-160">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="4c37c-161">Especifica o caminho para o diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="4c37c-161">Specifies the path for the output directory.</span></span> <span data-ttu-id="4c37c-162">Se não for especificado, o padrão será *./bin/[configuração]/[estrutura]/* para uma implantação dependente da estrutura, ou *./bin/[configuração]/[estrutura]/[tempo de execução]* para implantações autocontidas.</span><span class="sxs-lookup"><span data-stu-id="4c37c-162">If not specified, it defaults to *./bin/[configuration]/[framework]/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]* for a self-contained deployment.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="4c37c-163">Publica o aplicativo para um determinado tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="4c37c-163">Publishes the application for a given runtime.</span></span> <span data-ttu-id="4c37c-164">Isso é usado ao criar uma [implantação autocontida (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="4c37c-164">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="4c37c-165">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="4c37c-165">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="4c37c-166">O padrão é publicar uma [implantação dependente da estrutura (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="4c37c-166">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="4c37c-167">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="4c37c-167">Sets the verbosity level of the command.</span></span> <span data-ttu-id="4c37c-168">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="4c37c-168">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="4c37c-169">Define o sufixo da versão para substituir o asterisco (`*`) no campo de versão do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="4c37c-169">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="4c37c-170">Exemplos</span><span class="sxs-lookup"><span data-stu-id="4c37c-170">Examples</span></span>

<span data-ttu-id="4c37c-171">Publique o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="4c37c-171">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="4c37c-172">Publicar o aplicativo usando o arquivo de projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="4c37c-172">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`
    
<span data-ttu-id="4c37c-173">Publique o projeto no diretório atual usando a estrutura `netcoreapp1.1`:</span><span class="sxs-lookup"><span data-stu-id="4c37c-173">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`
    
<span data-ttu-id="4c37c-174">Publique o aplicativo atual usando a estrutura `netcoreapp1.1` e o tempo de execução para `OS X 10.10` (liste este RID no arquivo de projeto).</span><span class="sxs-lookup"><span data-stu-id="4c37c-174">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

## <a name="see-also"></a><span data-ttu-id="4c37c-175">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4c37c-175">See also</span></span>

* [<span data-ttu-id="4c37c-176">Estruturas de destino</span><span class="sxs-lookup"><span data-stu-id="4c37c-176">Target frameworks</span></span>](../../standard/frameworks.md)
* [<span data-ttu-id="4c37c-177">Catálogo de RID (Identificador de Tempo de Execução)</span><span class="sxs-lookup"><span data-stu-id="4c37c-177">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)

