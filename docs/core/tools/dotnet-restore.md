---
title: Comando dotnet restore
description: Saiba como restaurar as dependências e ferramentas específicas de projeto com o comando dotnet restore.
ms.date: 02/27/2020
ms.openlocfilehash: 276fad896a6a8a647ed05a9de8c582d463d9ab8f
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/27/2020
ms.locfileid: "84005304"
---
# <a name="dotnet-restore"></a><span data-ttu-id="f6dfc-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="f6dfc-103">dotnet restore</span></span>

<span data-ttu-id="f6dfc-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="f6dfc-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="f6dfc-105">Name</span><span class="sxs-lookup"><span data-stu-id="f6dfc-105">Name</span></span>

<span data-ttu-id="f6dfc-106">`dotnet restore` – Restaura as dependências e as ferramentas de um projeto.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="f6dfc-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="f6dfc-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lock-file] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a><span data-ttu-id="f6dfc-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="f6dfc-108">Description</span></span>

<span data-ttu-id="f6dfc-109">O comando `dotnet restore` usa o NuGet para restaurar as dependências e ferramentas específicas de projeto especificadas no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span>  <span data-ttu-id="f6dfc-110">Na maioria dos casos, você não precisa usar o `dotnet restore` comando explicitamente, uma vez que uma restauração do NuGet é executada implicitamente, se necessário, quando você executa os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="f6dfc-110">In most cases, you don't need to explicitly use the `dotnet restore` command, since a NuGet restore is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="f6dfc-111">Às vezes, pode ser inconveniente executar a restauração implícita do NuGet com estes comandos.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-111">Sometimes, it might be inconvenient to run the implicit NuGet restore with these commands.</span></span> <span data-ttu-id="f6dfc-112">Por exemplo, alguns sistemas automatizados, como os sistemas de compilação, precisam chamar o `dotnet restore` explicitamente para controlar o momento em que a restauração ocorre para que possam controlar o uso de rede.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-112">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="f6dfc-113">Para evitar a restauração implícita do NuGet, você pode usar o `--no-restore` sinalizador com qualquer um desses comandos para desabilitar a restauração implícita.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-113">To prevent the implicit NuGet restore, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

### <a name="specify-feeds"></a><span data-ttu-id="f6dfc-114">Especificar feeds</span><span class="sxs-lookup"><span data-stu-id="f6dfc-114">Specify feeds</span></span>

<span data-ttu-id="f6dfc-115">Para restaurar as dependências, o NuGet precisa dos feeds nos quais os pacotes estão localizados.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-115">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="f6dfc-116">Os feeds são geralmente fornecidos por meio do arquivo de configuração *nuget.config*.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-116">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="f6dfc-117">Um arquivo de configuração padrão é fornecido quando o SDK do .NET Core é instalado.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-117">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="f6dfc-118">Para especificar Feeds adicionais, siga um destes procedimentos:</span><span class="sxs-lookup"><span data-stu-id="f6dfc-118">To specify additional feeds, do one of the following:</span></span>

- <span data-ttu-id="f6dfc-119">Crie seu próprio arquivo *NuGet. config* no diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-119">Create your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="f6dfc-120">Para obter mais informações, consulte [as configurações comuns do NuGet e as](/nuget/consume-packages/configuring-nuget-behavior) diferenças de [NuGet. config](#nugetconfig-differences) mais adiante neste artigo.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-120">For more information, see [Common NuGet configurations](/nuget/consume-packages/configuring-nuget-behavior) and [nuget.config differences](#nugetconfig-differences) later in this article.</span></span>
- <span data-ttu-id="f6dfc-121">Use `dotnet nuget` comandos como [`dotnet nuget add source`](dotnet-nuget-add-source.md) .</span><span class="sxs-lookup"><span data-stu-id="f6dfc-121">Use `dotnet nuget` commands such as [`dotnet nuget add source`](dotnet-nuget-add-source.md).</span></span>

<span data-ttu-id="f6dfc-122">Você pode substituir os feeds *NuGet. config* pela `-s` opção.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-122">You can override the *nuget.config* feeds with the `-s` option.</span></span>

<span data-ttu-id="f6dfc-123">Para obter informações sobre como usar feeds autenticados, consulte [consumindo pacotes de feeds autenticados](/nuget/consume-packages/consuming-packages-authenticated-feeds).</span><span class="sxs-lookup"><span data-stu-id="f6dfc-123">For information about how to use authenticated feeds, see [Consuming packages from authenticated feeds](/nuget/consume-packages/consuming-packages-authenticated-feeds).</span></span>

### <a name="global-packages-folder"></a><span data-ttu-id="f6dfc-124">Pasta de pacotes globais</span><span class="sxs-lookup"><span data-stu-id="f6dfc-124">Global packages folder</span></span>

<span data-ttu-id="f6dfc-125">Para dependências, você pode especificar onde os pacotes restaurados são colocados durante a operação de restauração usando o argumento `--packages`.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-125">For dependencies, you can specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="f6dfc-126">Se não é especificado, o cache do pacote NuGet padrão é usado, o qual pode ser encontrado no diretório `.nuget/packages` do diretório base do usuário em todos os sistemas operacionais.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-126">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="f6dfc-127">Por exemplo, */home/user1* no Linux ou *C:\Usuário\user1* no Windows.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-127">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

### <a name="project-specific-tooling"></a><span data-ttu-id="f6dfc-128">Ferramentas específicas do projeto</span><span class="sxs-lookup"><span data-stu-id="f6dfc-128">Project-specific tooling</span></span>

<span data-ttu-id="f6dfc-129">Para ferramentas específicas do projeto, o `dotnet restore` primeiro restaura o pacote no qual a ferramenta foi empacotada e prossegue com a restauração das dependências da ferramenta conforme especificado no seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-129">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="f6dfc-130">Diferenças do nuget.config</span><span class="sxs-lookup"><span data-stu-id="f6dfc-130">nuget.config differences</span></span>

<span data-ttu-id="f6dfc-131">O comportamento do comando `dotnet restore` será afetado pelas configurações no arquivo *nuget.config*, se estiver presente.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-131">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="f6dfc-132">Por exemplo, a definição da `globalPackagesFolder` em *nuget.config* coloca os pacotes NuGet restaurados na pasta especificada.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-132">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="f6dfc-133">Essa é uma alternativa para especificar a opção `--packages` no comando `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-133">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="f6dfc-134">Para obter mais informações, confira a [Referência do nuget.config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="f6dfc-134">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="f6dfc-135">Há três configurações específicas que são ignoradas por `dotnet restore`:</span><span class="sxs-lookup"><span data-stu-id="f6dfc-135">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="f6dfc-136">bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="f6dfc-136">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="f6dfc-137">Os redirecionamentos de associação não funcionam com elementos `<PackageReference>` e o .NET Core só dá suporte a elementos `<PackageReference>` em pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-137">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="f6dfc-138">soluções</span><span class="sxs-lookup"><span data-stu-id="f6dfc-138">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="f6dfc-139">Essa configuração é específica do Visual Studio e não se aplica ao .NET Core.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-139">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="f6dfc-140">O .NET Core não usa um arquivo `packages.config` e, em vez disso, usa elementos `<PackageReference>` para pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-140">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="f6dfc-141">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="f6dfc-141">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="f6dfc-142">Essa configuração não é aplicável, pois o [NuGet ainda não dá suporte à verificação de multiplataforma](https://github.com/NuGet/Home/issues/7939) de pacotes confiáveis.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-142">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="arguments"></a><span data-ttu-id="f6dfc-143">Argumentos</span><span class="sxs-lookup"><span data-stu-id="f6dfc-143">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="f6dfc-144">Caminho opcional para o arquivo de projeto a ser restaurado.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-144">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="f6dfc-145">Opções</span><span class="sxs-lookup"><span data-stu-id="f6dfc-145">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="f6dfc-146">O arquivo de configuração NuGet (*nuget.config*) a ser usado para a operação de restauração.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-146">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="f6dfc-147">Desabilita a restauração de vários projetos paralelamente.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-147">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="f6dfc-148">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-148">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="f6dfc-149">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-149">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`--force-evaluate`**

  <span data-ttu-id="f6dfc-150">Força a restauração a reavaliar todas as dependências mesmo se um arquivo de bloqueio já existir.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-150">Forces restore to reevaluate all dependencies even if a lock file already exists.</span></span>

- **`-h|--help`**

  <span data-ttu-id="f6dfc-151">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-151">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="f6dfc-152">Avise somente sobre fontes com falha se houver pacotes que atendem ao requisito de versão.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-152">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--interactive`**

  <span data-ttu-id="f6dfc-153">Permite que o comando pare e aguarde a entrada ou uma ação do usuário (por exemplo, para concluir a autenticação).</span><span class="sxs-lookup"><span data-stu-id="f6dfc-153">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="f6dfc-154">A partir do .NET Core 2.1.400.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-154">Since .NET Core 2.1.400.</span></span>

- **`--lock-file-path <LOCK_FILE_PATH>`**

  <span data-ttu-id="f6dfc-155">Local de saída onde o arquivo de bloqueio do projeto é gravado.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-155">Output location where project lock file is written.</span></span> <span data-ttu-id="f6dfc-156">Por padrão, isso é *PROJECT_ROOT \Packages.Lock.JSON*.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-156">By default, this is *PROJECT_ROOT\packages.lock.json*.</span></span>

- **`--locked-mode`**

  <span data-ttu-id="f6dfc-157">Não permitir atualização do arquivo de bloqueio do projeto.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-157">Don't allow updating project lock file.</span></span>

- **`--no-cache`**

  <span data-ttu-id="f6dfc-158">Especifica para não armazenar em cache solicitações HTTP.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-158">Specifies to not cache HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="f6dfc-159">Ao restaurar um projeto com referências de P2P (projeto a projeto), restaura o projeto raiz, não as referências.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-159">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="f6dfc-160">Especifica o diretório para os pacotes restaurados.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-160">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="f6dfc-161">Especifica um runtime para a restauração do pacote.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-161">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="f6dfc-162">Isso é usado para restaurar pacotes para runtimes não listados explicitamente na marca `<RuntimeIdentifiers>` no arquivo *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-162">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="f6dfc-163">Para obter uma lista de RIDs (Identificadores de Runtime), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="f6dfc-163">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="f6dfc-164">Forneça diversas RIDs especificando essa opção várias vezes.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-164">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="f6dfc-165">Especifica o URI da origem do pacote NuGet a ser usado durante a operação de restauração.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-165">Specifies the URI of the NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="f6dfc-166">Essa configuração substitui todas as fontes especificadas nos arquivos *nuget.config*.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-166">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="f6dfc-167">Diversas fontes podem ser fornecidas especificando essa opção várias vezes.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-167">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--use-lock-file`**

  <span data-ttu-id="f6dfc-168">Habilita o arquivo de bloqueio do projeto a ser gerado e usado com a restauração.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-168">Enables project lock file to be generated and used with restore.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="f6dfc-169">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-169">Sets the verbosity level of the command.</span></span> <span data-ttu-id="f6dfc-170">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-170">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="f6dfc-171">O valor padrão é `minimal`.</span><span class="sxs-lookup"><span data-stu-id="f6dfc-171">Default value is `minimal`.</span></span>

## <a name="examples"></a><span data-ttu-id="f6dfc-172">Exemplos</span><span class="sxs-lookup"><span data-stu-id="f6dfc-172">Examples</span></span>

- <span data-ttu-id="f6dfc-173">Restaure as dependências e as ferramentas para o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="f6dfc-173">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="f6dfc-174">Restaure as dependências e as ferramentas do `app1` projeto encontradas no caminho fornecido:</span><span class="sxs-lookup"><span data-stu-id="f6dfc-174">Restore dependencies and tools for the `app1` project found in the   given path:</span></span>

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="f6dfc-175">Restaure as dependências e as ferramentas para o projeto no diretório atual usando o caminho de arquivo fornecido como a origem:</span><span class="sxs-lookup"><span data-stu-id="f6dfc-175">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="f6dfc-176">Restaure as dependências e as ferramentas para o projeto no diretório atual usando os dois caminhos de arquivo fornecidos como fontes:</span><span class="sxs-lookup"><span data-stu-id="f6dfc-176">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="f6dfc-177">Restaure as dependências e as ferramentas para o projeto no diretório atual mostrando a saída detalhada:</span><span class="sxs-lookup"><span data-stu-id="f6dfc-177">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
