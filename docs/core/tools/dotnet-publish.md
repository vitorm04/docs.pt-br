---
title: "Comando dotnet publish – CLI do .NET Core"
description: "O comando dotnet publish publica seu projeto .NET Core em um diretório."
author: mairaw
ms.author: mairaw
ms.date: 03/10/2018
ms.topic: article
ms.prod: .net-core
ms.technology: dotnet-cli
ms.workload:
- dotnetcore
ms.openlocfilehash: 2aa69217e949b970b632c4fad72838b63c2a8988
ms.sourcegitcommit: 83dd5ec003e788ccb3e33f3412a7af39ae347646
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2018
---
# <a name="dotnet-publish"></a><span data-ttu-id="37333-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="37333-103">dotnet publish</span></span>

[!INCLUDE [topic-appliesto-net-core-all](../../../includes/topic-appliesto-net-core-all.md)]

## <a name="name"></a><span data-ttu-id="37333-104">Nome</span><span class="sxs-lookup"><span data-stu-id="37333-104">Name</span></span>

<span data-ttu-id="37333-105">`dotnet publish`- Empacota o aplicativo e suas dependências em uma pasta para implantação em um sistema de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="37333-105">`dotnet publish` - Packs the application and its dependencies into a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="37333-106">Sinopse</span><span class="sxs-lookup"><span data-stu-id="37333-106">Synopsis</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="37333-107">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="37333-107">.NET Core 2.x</span></span>](#tab/netcore2x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [--force] [--manifest] [--no-dependencies] [--no-restore] [-o|--output] [-r|--runtime] [--self-contained] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="37333-108">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="37333-108">.NET Core 1.x</span></span>](#tab/netcore1x)

```
dotnet publish [<PROJECT>] [-c|--configuration] [-f|--framework] [-o|--output] [-r|--runtime] [-v|--verbosity] [--version-suffix]
dotnet publish [-h|--help]
```

---

## <a name="description"></a><span data-ttu-id="37333-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="37333-109">Description</span></span>

<span data-ttu-id="37333-110">`dotnet publish` compila o aplicativo, lê suas dependências especificadas no arquivo de projeto e publica o conjunto de arquivos resultantes em um diretório.</span><span class="sxs-lookup"><span data-stu-id="37333-110">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="37333-111">A saída conterá o seguinte:</span><span class="sxs-lookup"><span data-stu-id="37333-111">The output will contain the following:</span></span>

* <span data-ttu-id="37333-112">Código IL (Linguagem Intermediária) em um assembly com uma extensão *dll*.</span><span class="sxs-lookup"><span data-stu-id="37333-112">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
* <span data-ttu-id="37333-113">Arquivo *.deps.json* que contém todas as dependências do projeto.</span><span class="sxs-lookup"><span data-stu-id="37333-113">*.deps.json* file that contains all of the dependencies of the project.</span></span>
* <span data-ttu-id="37333-114">Arquivo *.runtime.config.json* que especifica o tempo de execução compartilhado esperado pelo aplicativo, bem como outras opções de configuração para o tempo de execução (por exemplo, tipo de coleta de lixo).</span><span class="sxs-lookup"><span data-stu-id="37333-114">*.runtime.config.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
* <span data-ttu-id="37333-115">As dependências do aplicativo.</span><span class="sxs-lookup"><span data-stu-id="37333-115">The application's dependencies.</span></span> <span data-ttu-id="37333-116">Elas são copiadas do cache NuGet para a pasta de saída.</span><span class="sxs-lookup"><span data-stu-id="37333-116">These are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="37333-117">A saída do comando `dotnet publish` está pronta para implantação em um sistema de hospedagem (por exemplo, um servidor, PC, Mac, laptop) para execução, e é a única maneira com suporte oficial para preparar o aplicativo para implantação.</span><span class="sxs-lookup"><span data-stu-id="37333-117">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution and is the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="37333-118">Dependendo do tipo de implantação especificado pelo projeto, talvez o sistema de hospedagem não tenha o tempo de execução compartilhado do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="37333-118">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="37333-119">Para saber mais, confira [Implantação de aplicativos .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="37333-119">For more information, see [.NET Core Application Deployment](../deploying/index.md).</span></span> <span data-ttu-id="37333-120">Para a estrutura de diretórios de um aplicativo publicado, veja [Estrutura do diretório](/aspnet/core/hosting/directory-structure).</span><span class="sxs-lookup"><span data-stu-id="37333-120">For the directory structure of a published application, see [Directory structure](/aspnet/core/hosting/directory-structure).</span></span>

[!INCLUDE[dotnet restore note + options](~/includes/dotnet-restore-note-options.md)]

## <a name="arguments"></a><span data-ttu-id="37333-121">Arguments</span><span class="sxs-lookup"><span data-stu-id="37333-121">Arguments</span></span>

`PROJECT`

<span data-ttu-id="37333-122">O projeto a ser publicado, cujo padrão será o diretório atual se não for especificado.</span><span class="sxs-lookup"><span data-stu-id="37333-122">The project to publish, which defaults to the current directory if not specified.</span></span>

## <a name="options"></a><span data-ttu-id="37333-123">Opções</span><span class="sxs-lookup"><span data-stu-id="37333-123">Options</span></span>

# <a name="net-core-2xtabnetcore2x"></a>[<span data-ttu-id="37333-124">.NET Core 2.x</span><span class="sxs-lookup"><span data-stu-id="37333-124">.NET Core 2.x</span></span>](#tab/netcore2x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="37333-125">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="37333-125">Defines the build configuration.</span></span> <span data-ttu-id="37333-126">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="37333-126">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="37333-127">Publica o aplicativo para a [estrutura de destino](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="37333-127">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="37333-128">Especifique a estrutura de destino no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="37333-128">You must specify the target framework in the project file.</span></span>

`--force`

<span data-ttu-id="37333-129">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="37333-129">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="37333-130">Isso é equivalente a excluir o arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="37333-130">This is equivalent to deleting the *project.assets.json* file.</span></span>

`-h|--help`

<span data-ttu-id="37333-131">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="37333-131">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="37333-132">Especifica um ou vários [manifestos de destino](../deploying/runtime-store.md) a serem usados para cortar o conjunto de pacotes publicados com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="37333-132">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="37333-133">O arquivo de manifesto faz parte da saída do [comando `dotnet store`](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="37333-133">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="37333-134">Para especificar vários manifestos, adicione uma opção `--manifest` para cada manifesto.</span><span class="sxs-lookup"><span data-stu-id="37333-134">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="37333-135">Essa opção está disponível a partir do SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="37333-135">This option is available starting with .NET Core 2.0 SDK.</span></span>

`--no-dependencies`

<span data-ttu-id="37333-136">Ignora as referências projeto a projeto e só restaura o projeto raiz.</span><span class="sxs-lookup"><span data-stu-id="37333-136">Ignores project-to-project references and only restores the root project.</span></span>

`--no-restore`

<span data-ttu-id="37333-137">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="37333-137">Doesn't perform an implicit restore when running the command.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="37333-138">Especifica o caminho para o diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="37333-138">Specifies the path for the output directory.</span></span> <span data-ttu-id="37333-139">Se não for especificado, o padrão será *./bin/[configuração]/[estrutura]/* para uma implantação dependente da estrutura, ou *./bin/[configuração]/[estrutura]/[tempo de execução]* para implantações autocontidas.</span><span class="sxs-lookup"><span data-stu-id="37333-139">If not specified, it defaults to *./bin/[configuration]/[framework]/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]* for a self-contained deployment.</span></span>
<span data-ttu-id="37333-140">Se um caminho relativo for fornecido, o diretório de saída gerado será relativo ao local do arquivo de projeto, não ao diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="37333-140">If a relative path is provided, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`--self-contained`

<span data-ttu-id="37333-141">Publica o tempo de execução do .NET Core com seu aplicativo para que não seja necessário instalar o tempo de execução no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="37333-141">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="37333-142">Se um identificador de tempo de execução for especificado, seu valor padrão será `true`.</span><span class="sxs-lookup"><span data-stu-id="37333-142">If a runtime identifier is specified, its default value is `true`.</span></span> <span data-ttu-id="37333-143">Para obter mais informações sobre os diferentes tipos de implantação, consulte [Implantação de aplicativos .NET Core](../deploying/index.md).</span><span class="sxs-lookup"><span data-stu-id="37333-143">For more information about the different deployment types, see [.NET Core application deployment](../deploying/index.md).</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="37333-144">Publica o aplicativo para um determinado tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="37333-144">Publishes the application for a given runtime.</span></span> <span data-ttu-id="37333-145">Isso é usado ao criar uma [implantação autocontida (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="37333-145">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="37333-146">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="37333-146">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="37333-147">O padrão é publicar uma [implantação dependente da estrutura (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="37333-147">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="37333-148">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="37333-148">Sets the verbosity level of the command.</span></span> <span data-ttu-id="37333-149">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="37333-149">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="37333-150">Define o sufixo da versão para substituir o asterisco (`*`) no campo de versão do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="37333-150">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

# <a name="net-core-1xtabnetcore1x"></a>[<span data-ttu-id="37333-151">.NET Core 1.x</span><span class="sxs-lookup"><span data-stu-id="37333-151">.NET Core 1.x</span></span>](#tab/netcore1x)

`-c|--configuration {Debug|Release}`

<span data-ttu-id="37333-152">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="37333-152">Defines the build configuration.</span></span> <span data-ttu-id="37333-153">O valor padrão é `Debug`.</span><span class="sxs-lookup"><span data-stu-id="37333-153">The default value is `Debug`.</span></span>

`-f|--framework <FRAMEWORK>`

<span data-ttu-id="37333-154">Publica o aplicativo para a [estrutura de destino](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="37333-154">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="37333-155">Especifique a estrutura de destino no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="37333-155">You must specify the target framework in the project file.</span></span>

`-h|--help`

<span data-ttu-id="37333-156">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="37333-156">Prints out a short help for the command.</span></span>

`--manifest <PATH_TO_MANIFEST_FILE>`

<span data-ttu-id="37333-157">Especifica um ou vários [manifestos de destino](../deploying/runtime-store.md) a serem usados para cortar o conjunto de pacotes publicados com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="37333-157">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="37333-158">O arquivo de manifesto faz parte da saída do [comando `dotnet store`](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="37333-158">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="37333-159">Para especificar vários manifestos, adicione uma opção `--manifest` para cada manifesto.</span><span class="sxs-lookup"><span data-stu-id="37333-159">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span> <span data-ttu-id="37333-160">Essa opção está disponível a partir do SDK do .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="37333-160">This option is available starting with .NET Core 2.0 SDK.</span></span>

`-o|--output <OUTPUT_DIRECTORY>`

<span data-ttu-id="37333-161">Especifica o caminho para o diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="37333-161">Specifies the path for the output directory.</span></span> <span data-ttu-id="37333-162">Se não for especificado, o padrão será *./bin/[configuração]/[estrutura]/* para uma implantação dependente da estrutura, ou *./bin/[configuração]/[estrutura]/[tempo de execução]* para implantações autocontidas.</span><span class="sxs-lookup"><span data-stu-id="37333-162">If not specified, it defaults to *./bin/[configuration]/[framework]/* for a framework-dependent deployment or *./bin/[configuration]/[framework]/[runtime]* for a self-contained deployment.</span></span>
<span data-ttu-id="37333-163">Se um caminho relativo for fornecido, o diretório de saída gerado será relativo ao local do arquivo de projeto, não ao diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="37333-163">If a relative path is provided, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

`-r|--runtime <RUNTIME_IDENTIFIER>`

<span data-ttu-id="37333-164">Publica o aplicativo para um determinado tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="37333-164">Publishes the application for a given runtime.</span></span> <span data-ttu-id="37333-165">Isso é usado ao criar uma [implantação autocontida (SCD)](../deploying/index.md#self-contained-deployments-scd).</span><span class="sxs-lookup"><span data-stu-id="37333-165">This is used when creating a [self-contained deployment (SCD)](../deploying/index.md#self-contained-deployments-scd).</span></span> <span data-ttu-id="37333-166">Para obter uma lista de RIDs (Identificadores de Tempo de Execução), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="37333-166">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="37333-167">O padrão é publicar uma [implantação dependente da estrutura (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span><span class="sxs-lookup"><span data-stu-id="37333-167">Default is to publish a [framework-dependent deployment (FDD)](../deploying/index.md#framework-dependent-deployments-fdd).</span></span>

`-v|--verbosity <LEVEL>`

<span data-ttu-id="37333-168">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="37333-168">Sets the verbosity level of the command.</span></span> <span data-ttu-id="37333-169">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="37333-169">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

`--version-suffix <VERSION_SUFFIX>`

<span data-ttu-id="37333-170">Define o sufixo da versão para substituir o asterisco (`*`) no campo de versão do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="37333-170">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

---

## <a name="examples"></a><span data-ttu-id="37333-171">Exemplos</span><span class="sxs-lookup"><span data-stu-id="37333-171">Examples</span></span>

<span data-ttu-id="37333-172">Publique o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="37333-172">Publish the project in the current directory:</span></span>

`dotnet publish`

<span data-ttu-id="37333-173">Publicar o aplicativo usando o arquivo de projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="37333-173">Publish the application using the specified project file:</span></span>

`dotnet publish ~/projects/app1/app1.csproj`

<span data-ttu-id="37333-174">Publique o projeto no diretório atual usando a estrutura `netcoreapp1.1`:</span><span class="sxs-lookup"><span data-stu-id="37333-174">Publish the project in the current directory using the `netcoreapp1.1` framework:</span></span>

`dotnet publish --framework netcoreapp1.1`

<span data-ttu-id="37333-175">Publique o aplicativo atual usando a estrutura `netcoreapp1.1` e o tempo de execução para `OS X 10.10` (liste este RID no arquivo de projeto).</span><span class="sxs-lookup"><span data-stu-id="37333-175">Publish the current application using the `netcoreapp1.1` framework and the runtime for `OS X 10.10` (you must list this RID in the project file).</span></span>

`dotnet publish --framework netcoreapp1.1 --runtime osx.10.11-x64`

<span data-ttu-id="37333-176">Publique o aplicativo atual, mas não restaure as referências P2P (projeto a projeto), apenas o projeto raiz durante a operação de restauração (SDK do .NET Core 2.0 e versões posteriores):</span><span class="sxs-lookup"><span data-stu-id="37333-176">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation (.NET Core SDK 2.0 and later versions):</span></span>

`dotnet publish --no-dependencies`

## <a name="see-also"></a><span data-ttu-id="37333-177">Consulte também</span><span class="sxs-lookup"><span data-stu-id="37333-177">See also</span></span>

* [<span data-ttu-id="37333-178">Estruturas de destino</span><span class="sxs-lookup"><span data-stu-id="37333-178">Target frameworks</span></span>](../../standard/frameworks.md)
* [<span data-ttu-id="37333-179">Catálogo de RID (Identificador de Tempo de Execução)</span><span class="sxs-lookup"><span data-stu-id="37333-179">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)