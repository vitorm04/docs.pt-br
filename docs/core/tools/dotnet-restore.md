---
title: Comando dotnet restore
description: Saiba como restaurar as dependências e ferramentas específicas de projeto com o comando dotnet restore.
ms.date: 02/27/2020
ms.openlocfilehash: 3deef68a9bcee389a52291c72e7e1a1019a739fd
ms.sourcegitcommit: 73aa9653547a1cd70ee6586221f79cc29b588ebd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2020
ms.locfileid: "82102782"
---
# <a name="dotnet-restore"></a><span data-ttu-id="df339-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="df339-103">dotnet restore</span></span>

<span data-ttu-id="df339-104">**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="df339-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="df339-105">Nome</span><span class="sxs-lookup"><span data-stu-id="df339-105">Name</span></span>

<span data-ttu-id="df339-106">`dotnet restore` – Restaura as dependências e as ferramentas de um projeto.</span><span class="sxs-lookup"><span data-stu-id="df339-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="df339-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="df339-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lockfile] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a><span data-ttu-id="df339-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="df339-108">Description</span></span>

<span data-ttu-id="df339-109">O comando `dotnet restore` usa o NuGet para restaurar as dependências e ferramentas específicas de projeto especificadas no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="df339-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="df339-110">Por padrão, a restauração das dependências e as ferramentas são executadas em paralelo.</span><span class="sxs-lookup"><span data-stu-id="df339-110">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

### <a name="specify-feeds"></a><span data-ttu-id="df339-111">Especificar feeds</span><span class="sxs-lookup"><span data-stu-id="df339-111">Specify feeds</span></span>

<span data-ttu-id="df339-112">Para restaurar as dependências, o NuGet precisa dos feeds nos quais os pacotes estão localizados.</span><span class="sxs-lookup"><span data-stu-id="df339-112">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="df339-113">Os feeds são geralmente fornecidos por meio do arquivo de configuração *nuget.config*.</span><span class="sxs-lookup"><span data-stu-id="df339-113">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="df339-114">Um arquivo de configuração padrão é fornecido quando o .NET Core SDK é instalado.</span><span class="sxs-lookup"><span data-stu-id="df339-114">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="df339-115">Para especificar feeds adicionais, faça um dos seguintes:</span><span class="sxs-lookup"><span data-stu-id="df339-115">To specify additional feeds, do one of the following:</span></span>

- <span data-ttu-id="df339-116">Crie seu próprio arquivo *nuget.config* no diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="df339-116">Create your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="df339-117">Para obter mais informações, consulte [configurações comuns do NuGet](/nuget/consume-packages/configuring-nuget-behavior) e [diferenças de nuget.config](#nugetconfig-differences) mais tarde neste artigo.</span><span class="sxs-lookup"><span data-stu-id="df339-117">For more information, see [Common NuGet configurations](/nuget/consume-packages/configuring-nuget-behavior) and [nuget.config differences](#nugetconfig-differences) later in this article.</span></span>
- <span data-ttu-id="df339-118">Use `dotnet nuget` comandos [`dotnet nuget add source`](dotnet-nuget-add-source.md)como .</span><span class="sxs-lookup"><span data-stu-id="df339-118">Use `dotnet nuget` commands such as [`dotnet nuget add source`](dotnet-nuget-add-source.md).</span></span>

<span data-ttu-id="df339-119">Você pode substituir os feeds *nuget.config* com a `-s` opção.</span><span class="sxs-lookup"><span data-stu-id="df339-119">You can override the *nuget.config* feeds with the `-s` option.</span></span>

<span data-ttu-id="df339-120">Para obter informações sobre como usar feeds autenticados, consulte [Consumir pacotes de feeds autenticados](/nuget/consume-packages/consuming-packages-authenticated-feeds).</span><span class="sxs-lookup"><span data-stu-id="df339-120">For information about how to use authenticated feeds, see [Consuming packages from authenticated feeds](/nuget/consume-packages/consuming-packages-authenticated-feeds).</span></span>

### <a name="package-cache"></a><span data-ttu-id="df339-121">Cache do pacote</span><span class="sxs-lookup"><span data-stu-id="df339-121">Package cache</span></span>

<span data-ttu-id="df339-122">Para dependências, especifique onde os pacotes restaurados são colocados durante a operação de restauração usando o argumento `--packages`.</span><span class="sxs-lookup"><span data-stu-id="df339-122">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="df339-123">Se não é especificado, o cache do pacote NuGet padrão é usado, o qual pode ser encontrado no diretório `.nuget/packages` do diretório base do usuário em todos os sistemas operacionais.</span><span class="sxs-lookup"><span data-stu-id="df339-123">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="df339-124">Por exemplo, */home/user1* no Linux ou *C:\Usuário\user1* no Windows.</span><span class="sxs-lookup"><span data-stu-id="df339-124">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

### <a name="project-specific-tooling"></a><span data-ttu-id="df339-125">Ferramentas específicas do projeto</span><span class="sxs-lookup"><span data-stu-id="df339-125">Project-specific tooling</span></span>

<span data-ttu-id="df339-126">Para ferramentas específicas do projeto, o `dotnet restore` primeiro restaura o pacote no qual a ferramenta foi empacotada e prossegue com a restauração das dependências da ferramenta conforme especificado no seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="df339-126">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="df339-127">Diferenças do nuget.config</span><span class="sxs-lookup"><span data-stu-id="df339-127">nuget.config differences</span></span>

<span data-ttu-id="df339-128">O comportamento do comando `dotnet restore` será afetado pelas configurações no arquivo *nuget.config*, se estiver presente.</span><span class="sxs-lookup"><span data-stu-id="df339-128">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="df339-129">Por exemplo, a definição da `globalPackagesFolder` em *nuget.config* coloca os pacotes NuGet restaurados na pasta especificada.</span><span class="sxs-lookup"><span data-stu-id="df339-129">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="df339-130">Essa é uma alternativa para especificar a opção `--packages` no comando `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="df339-130">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="df339-131">Para obter mais informações, confira a [Referência do nuget.config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="df339-131">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="df339-132">Há três configurações específicas que são ignoradas por `dotnet restore`:</span><span class="sxs-lookup"><span data-stu-id="df339-132">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="df339-133">bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="df339-133">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="df339-134">Os redirecionamentos de associação não funcionam com elementos `<PackageReference>` e o .NET Core só dá suporte a elementos `<PackageReference>` em pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="df339-134">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="df339-135">Solução</span><span class="sxs-lookup"><span data-stu-id="df339-135">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="df339-136">Essa configuração é específica do Visual Studio e não se aplica ao .NET Core.</span><span class="sxs-lookup"><span data-stu-id="df339-136">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="df339-137">O .NET Core não usa um arquivo `packages.config` e, em vez disso, usa elementos `<PackageReference>` para pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="df339-137">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="df339-138">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="df339-138">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="df339-139">Essa configuração não é aplicável, pois o [NuGet ainda não dá suporte à verificação de multiplataforma](https://github.com/NuGet/Home/issues/7939) de pacotes confiáveis.</span><span class="sxs-lookup"><span data-stu-id="df339-139">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="implicit-restore"></a><span data-ttu-id="df339-140">Restauração implícita</span><span class="sxs-lookup"><span data-stu-id="df339-140">Implicit restore</span></span>

<span data-ttu-id="df339-141">O `dotnet restore` comando é executado implicitamente se necessário quando você executa os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="df339-141">The `dotnet restore` command is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="df339-142">Na maioria dos casos, você não precisa `dotnet restore` usar explicitamente o comando.</span><span class="sxs-lookup"><span data-stu-id="df339-142">In most cases, you don't need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="df339-143">Às vezes, pode ser inconveniente executar `dotnet restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="df339-143">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="df339-144">Por exemplo, alguns sistemas automatizados, como os sistemas de compilação, precisam chamar o `dotnet restore` explicitamente para controlar o momento em que a restauração ocorre para que possam controlar o uso de rede.</span><span class="sxs-lookup"><span data-stu-id="df339-144">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="df339-145">Para evitar que o `dotnet restore` seja executado implicitamente, use o sinalizador `--no-restore` com um desses comandos para desabilitar a restauração implícita.</span><span class="sxs-lookup"><span data-stu-id="df339-145">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="df339-146">Argumentos</span><span class="sxs-lookup"><span data-stu-id="df339-146">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="df339-147">Caminho opcional para o arquivo de projeto a ser restaurado.</span><span class="sxs-lookup"><span data-stu-id="df339-147">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="df339-148">Opções</span><span class="sxs-lookup"><span data-stu-id="df339-148">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="df339-149">O arquivo de configuração NuGet (*nuget.config*) a ser usado para a operação de restauração.</span><span class="sxs-lookup"><span data-stu-id="df339-149">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="df339-150">Desabilita a restauração de vários projetos paralelamente.</span><span class="sxs-lookup"><span data-stu-id="df339-150">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="df339-151">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="df339-151">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="df339-152">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="df339-152">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`--force-evaluate`**

  <span data-ttu-id="df339-153">As forças restauram para reavaliar todas as dependências, mesmo que um arquivo de bloqueio já exista.</span><span class="sxs-lookup"><span data-stu-id="df339-153">Forces restore to reevaluate all dependencies even if a lock file already exists.</span></span>

- **`-h|--help`**

  <span data-ttu-id="df339-154">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="df339-154">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="df339-155">Avise somente sobre fontes com falha se houver pacotes que atendem ao requisito de versão.</span><span class="sxs-lookup"><span data-stu-id="df339-155">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--interactive`**

  <span data-ttu-id="df339-156">Permite que o comando pare e aguarde a entrada ou uma ação do usuário (por exemplo, para concluir a autenticação).</span><span class="sxs-lookup"><span data-stu-id="df339-156">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="df339-157">A partir do .NET Core 2.1.400.</span><span class="sxs-lookup"><span data-stu-id="df339-157">Since .NET Core 2.1.400.</span></span>

- **`--lock-file-path <LOCK_FILE_PATH>`**

  <span data-ttu-id="df339-158">Local de saída onde o arquivo de bloqueio do projeto é gravado.</span><span class="sxs-lookup"><span data-stu-id="df339-158">Output location where project lock file is written.</span></span> <span data-ttu-id="df339-159">Por padrão, isso é *PROJECT_ROOT\packages.lock.json*.</span><span class="sxs-lookup"><span data-stu-id="df339-159">By default, this is *PROJECT_ROOT\packages.lock.json*.</span></span>

- **`--locked-mode`**

  <span data-ttu-id="df339-160">Não permita atualizar o arquivo de bloqueio do projeto.</span><span class="sxs-lookup"><span data-stu-id="df339-160">Don't allow updating project lock file.</span></span>

- **`--no-cache`**

  <span data-ttu-id="df339-161">Especifica para não armazenar solicitações HTTP.</span><span class="sxs-lookup"><span data-stu-id="df339-161">Specifies to not cache HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="df339-162">Ao restaurar um projeto com referências de P2P (projeto a projeto), restaura o projeto raiz, não as referências.</span><span class="sxs-lookup"><span data-stu-id="df339-162">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="df339-163">Especifica o diretório para os pacotes restaurados.</span><span class="sxs-lookup"><span data-stu-id="df339-163">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="df339-164">Especifica um runtime para a restauração do pacote.</span><span class="sxs-lookup"><span data-stu-id="df339-164">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="df339-165">Isso é usado para restaurar pacotes para runtimes não listados explicitamente na marca `<RuntimeIdentifiers>` no arquivo *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="df339-165">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="df339-166">Para obter uma lista de RIDs (Identificadores de Runtime), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="df339-166">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="df339-167">Forneça diversas RIDs especificando essa opção várias vezes.</span><span class="sxs-lookup"><span data-stu-id="df339-167">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="df339-168">Especifica uma origem de pacote NuGet a ser usada durante a operação de restauração.</span><span class="sxs-lookup"><span data-stu-id="df339-168">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="df339-169">Essa configuração substitui todas as fontes especificadas nos arquivos *nuget.config*.</span><span class="sxs-lookup"><span data-stu-id="df339-169">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="df339-170">Diversas fontes podem ser fornecidas especificando essa opção várias vezes.</span><span class="sxs-lookup"><span data-stu-id="df339-170">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--use-lockfile`**

  <span data-ttu-id="df339-171">Permite que o arquivo de bloqueio do projeto seja gerado e usado com restauração.</span><span class="sxs-lookup"><span data-stu-id="df339-171">Enables project lock file to be generated and used with restore.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="df339-172">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="df339-172">Sets the verbosity level of the command.</span></span> <span data-ttu-id="df339-173">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="df339-173">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="df339-174">O valor padrão é `minimal`.</span><span class="sxs-lookup"><span data-stu-id="df339-174">Default value is `minimal`.</span></span>

## <a name="examples"></a><span data-ttu-id="df339-175">Exemplos</span><span class="sxs-lookup"><span data-stu-id="df339-175">Examples</span></span>

- <span data-ttu-id="df339-176">Restaure as dependências e as ferramentas para o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="df339-176">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="df339-177">Restaurar dependências e `app1` ferramentas para o projeto encontrado no caminho dado:</span><span class="sxs-lookup"><span data-stu-id="df339-177">Restore dependencies and tools for the `app1` project found in the   given path:</span></span>

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="df339-178">Restaurar as dependências e ferramentas para o projeto no diretório atual usando o caminho do arquivo fornecido como fonte:</span><span class="sxs-lookup"><span data-stu-id="df339-178">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="df339-179">Restaurar as dependências e ferramentas para o projeto no diretório atual usando os dois caminhos de arquivo fornecidos como fontes:</span><span class="sxs-lookup"><span data-stu-id="df339-179">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="df339-180">Restaurar dependências e ferramentas para o projeto no diretório atual mostrando saída detalhada:</span><span class="sxs-lookup"><span data-stu-id="df339-180">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
