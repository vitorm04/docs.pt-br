---
title: Comando dotnet restore
description: Saiba como restaurar as dependências e ferramentas específicas de projeto com o comando dotnet restore.
ms.date: 02/27/2020
ms.openlocfilehash: c5cc9adf1d77b0ab03a61cc315d42c2f38362ad9
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021781"
---
# <a name="dotnet-restore"></a><span data-ttu-id="d85bb-103">dotnet restore</span><span class="sxs-lookup"><span data-stu-id="d85bb-103">dotnet restore</span></span>

<span data-ttu-id="d85bb-104">**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="d85bb-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="d85bb-105">Nome</span><span class="sxs-lookup"><span data-stu-id="d85bb-105">Name</span></span>

<span data-ttu-id="d85bb-106">`dotnet restore` – Restaura as dependências e as ferramentas de um projeto.</span><span class="sxs-lookup"><span data-stu-id="d85bb-106">`dotnet restore` - Restores the dependencies and tools of a project.</span></span>

## <a name="synopsis"></a><span data-ttu-id="d85bb-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="d85bb-107">Synopsis</span></span>

```dotnetcli
dotnet restore [<ROOT>] [--configfile <FILE>] [--disable-parallel]
    [-f|--force] [--force-evaluate] [--ignore-failed-sources]
    [--interactive] [--lock-file-path <LOCK_FILE_PATH>] [--locked-mode]
    [--no-cache] [--no-dependencies] [--packages <PACKAGES_DIRECTORY>]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [-s|--source <SOURCE>]
    [--use-lockfile] [-v|--verbosity <LEVEL>]

dotnet restore -h|--help
```

## <a name="description"></a><span data-ttu-id="d85bb-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="d85bb-108">Description</span></span>

<span data-ttu-id="d85bb-109">O comando `dotnet restore` usa o NuGet para restaurar as dependências e ferramentas específicas de projeto especificadas no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="d85bb-109">The `dotnet restore` command uses NuGet to restore dependencies as well as project-specific tools that are specified in the project file.</span></span> <span data-ttu-id="d85bb-110">Por padrão, a restauração das dependências e as ferramentas são executadas em paralelo.</span><span class="sxs-lookup"><span data-stu-id="d85bb-110">By default, the restoration of dependencies and tools are executed in parallel.</span></span>

<span data-ttu-id="d85bb-111">Para restaurar as dependências, o NuGet precisa dos feeds nos quais os pacotes estão localizados.</span><span class="sxs-lookup"><span data-stu-id="d85bb-111">To restore the dependencies, NuGet needs the feeds where the packages are located.</span></span> <span data-ttu-id="d85bb-112">Os feeds são geralmente fornecidos por meio do arquivo de configuração *nuget.config*.</span><span class="sxs-lookup"><span data-stu-id="d85bb-112">Feeds are usually provided via the *nuget.config* configuration file.</span></span> <span data-ttu-id="d85bb-113">Um arquivo de configuração padrão é fornecido quando o .NET Core SDK é instalado.</span><span class="sxs-lookup"><span data-stu-id="d85bb-113">A default configuration file is provided when the .NET Core SDK is installed.</span></span> <span data-ttu-id="d85bb-114">Especifique mais feeds criando seu próprio arquivo *nuget.config* no diretório do projeto.</span><span class="sxs-lookup"><span data-stu-id="d85bb-114">You specify additional feeds by creating your own *nuget.config* file in the project directory.</span></span> <span data-ttu-id="d85bb-115">Você pode substituir os feeds *nuget.config* com a opção - `-s` .</span><span class="sxs-lookup"><span data-stu-id="d85bb-115">You can override the *nuget.config* feeds with the - `-s` option.</span></span>

<span data-ttu-id="d85bb-116">Para dependências, especifique onde os pacotes restaurados são colocados durante a operação de restauração usando o argumento `--packages`.</span><span class="sxs-lookup"><span data-stu-id="d85bb-116">For dependencies, you specify where the restored packages are placed during the restore operation using the `--packages` argument.</span></span> <span data-ttu-id="d85bb-117">Se não é especificado, o cache do pacote NuGet padrão é usado, o qual pode ser encontrado no diretório `.nuget/packages` do diretório base do usuário em todos os sistemas operacionais.</span><span class="sxs-lookup"><span data-stu-id="d85bb-117">If not specified, the default NuGet package cache is used, which is found in the `.nuget/packages` directory in the user's home directory on all operating systems.</span></span> <span data-ttu-id="d85bb-118">Por exemplo, */home/user1* no Linux ou *C:\Usuário\user1* no Windows.</span><span class="sxs-lookup"><span data-stu-id="d85bb-118">For example, */home/user1* on Linux or *C:\Users\user1* on Windows.</span></span>

<span data-ttu-id="d85bb-119">Para ferramentas específicas do projeto, o `dotnet restore` primeiro restaura o pacote no qual a ferramenta foi empacotada e prossegue com a restauração das dependências da ferramenta conforme especificado no seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="d85bb-119">For project-specific tooling, `dotnet restore` first restores the package in which the tool is packed, and then proceeds to restore the tool's dependencies as specified in its project file.</span></span>

### <a name="nugetconfig-differences"></a><span data-ttu-id="d85bb-120">Diferenças do nuget.config</span><span class="sxs-lookup"><span data-stu-id="d85bb-120">nuget.config differences</span></span>

<span data-ttu-id="d85bb-121">O comportamento do comando `dotnet restore` será afetado pelas configurações no arquivo *nuget.config*, se estiver presente.</span><span class="sxs-lookup"><span data-stu-id="d85bb-121">The behavior of the `dotnet restore` command is affected by the settings in the *nuget.config* file, if present.</span></span> <span data-ttu-id="d85bb-122">Por exemplo, a definição da `globalPackagesFolder` em *nuget.config* coloca os pacotes NuGet restaurados na pasta especificada.</span><span class="sxs-lookup"><span data-stu-id="d85bb-122">For example, setting the `globalPackagesFolder` in *nuget.config* places the restored NuGet packages in the specified folder.</span></span> <span data-ttu-id="d85bb-123">Essa é uma alternativa para especificar a opção `--packages` no comando `dotnet restore`.</span><span class="sxs-lookup"><span data-stu-id="d85bb-123">This is an alternative to specifying the `--packages` option on the `dotnet restore` command.</span></span> <span data-ttu-id="d85bb-124">Para obter mais informações, confira a [Referência do nuget.config](/nuget/schema/nuget-config-file).</span><span class="sxs-lookup"><span data-stu-id="d85bb-124">For more information, see the [nuget.config reference](/nuget/schema/nuget-config-file).</span></span>

<span data-ttu-id="d85bb-125">Há três configurações específicas que são ignoradas por `dotnet restore`:</span><span class="sxs-lookup"><span data-stu-id="d85bb-125">There are three specific settings that `dotnet restore` ignores:</span></span>

- [<span data-ttu-id="d85bb-126">bindingRedirects</span><span class="sxs-lookup"><span data-stu-id="d85bb-126">bindingRedirects</span></span>](/nuget/schema/nuget-config-file#bindingredirects-section)

  <span data-ttu-id="d85bb-127">Os redirecionamentos de associação não funcionam com elementos `<PackageReference>` e o .NET Core só dá suporte a elementos `<PackageReference>` em pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="d85bb-127">Binding redirects don't work with `<PackageReference>` elements and .NET Core only supports `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="d85bb-128">Solução</span><span class="sxs-lookup"><span data-stu-id="d85bb-128">solution</span></span>](/nuget/schema/nuget-config-file#solution-section)

  <span data-ttu-id="d85bb-129">Essa configuração é específica do Visual Studio e não se aplica ao .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d85bb-129">This setting is Visual Studio specific and doesn't apply to .NET Core.</span></span> <span data-ttu-id="d85bb-130">O .NET Core não usa um arquivo `packages.config` e, em vez disso, usa elementos `<PackageReference>` para pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="d85bb-130">.NET Core doesn't use a `packages.config` file and instead uses `<PackageReference>` elements for NuGet packages.</span></span>

- [<span data-ttu-id="d85bb-131">trustedSigners</span><span class="sxs-lookup"><span data-stu-id="d85bb-131">trustedSigners</span></span>](/nuget/schema/nuget-config-file#trustedsigners-section)

  <span data-ttu-id="d85bb-132">Essa configuração não é aplicável, pois o [NuGet ainda não dá suporte à verificação de multiplataforma](https://github.com/NuGet/Home/issues/7939) de pacotes confiáveis.</span><span class="sxs-lookup"><span data-stu-id="d85bb-132">This setting isn't applicable as [NuGet doesn't yet support cross-platform verification](https://github.com/NuGet/Home/issues/7939) of trusted packages.</span></span>

## <a name="implicit-restore"></a><span data-ttu-id="d85bb-133">Restauração implícita</span><span class="sxs-lookup"><span data-stu-id="d85bb-133">Implicit restore</span></span>

<span data-ttu-id="d85bb-134">O `dotnet restore` comando é executado implicitamente se necessário quando você executa os seguintes comandos:</span><span class="sxs-lookup"><span data-stu-id="d85bb-134">The `dotnet restore` command is run implicitly if necessary when you run the following commands:</span></span>

- [`dotnet new`](dotnet-new.md)
- [`dotnet build`](dotnet-build.md)
- [`dotnet build-server`](dotnet-build-server.md)
- [`dotnet run`](dotnet-run.md)
- [`dotnet test`](dotnet-test.md)
- [`dotnet publish`](dotnet-publish.md)
- [`dotnet pack`](dotnet-pack.md)

<span data-ttu-id="d85bb-135">Na maioria dos casos, você não precisa `dotnet restore` usar explicitamente o comando.</span><span class="sxs-lookup"><span data-stu-id="d85bb-135">In most cases, you don't need to explicitly use the `dotnet restore` command.</span></span>

<span data-ttu-id="d85bb-136">Às vezes, pode ser inconveniente executar `dotnet restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="d85bb-136">Sometimes, it might be inconvenient to run `dotnet restore` implicitly.</span></span> <span data-ttu-id="d85bb-137">Por exemplo, alguns sistemas automatizados, como os sistemas de compilação, precisam chamar o `dotnet restore` explicitamente para controlar o momento em que a restauração ocorre para que possam controlar o uso de rede.</span><span class="sxs-lookup"><span data-stu-id="d85bb-137">For example, some automated systems, such as build systems, need to call `dotnet restore` explicitly to control when the restore occurs so that they can control network usage.</span></span> <span data-ttu-id="d85bb-138">Para evitar que o `dotnet restore` seja executado implicitamente, use o sinalizador `--no-restore` com um desses comandos para desabilitar a restauração implícita.</span><span class="sxs-lookup"><span data-stu-id="d85bb-138">To prevent `dotnet restore` from running implicitly, you can use the `--no-restore` flag with any of these commands to disable implicit restore.</span></span>

## <a name="arguments"></a><span data-ttu-id="d85bb-139">Argumentos</span><span class="sxs-lookup"><span data-stu-id="d85bb-139">Arguments</span></span>

- **`ROOT`**

  <span data-ttu-id="d85bb-140">Caminho opcional para o arquivo de projeto a ser restaurado.</span><span class="sxs-lookup"><span data-stu-id="d85bb-140">Optional path to the project file to restore.</span></span>

## <a name="options"></a><span data-ttu-id="d85bb-141">Opções</span><span class="sxs-lookup"><span data-stu-id="d85bb-141">Options</span></span>

- **`--configfile <FILE>`**

  <span data-ttu-id="d85bb-142">O arquivo de configuração NuGet (*nuget.config*) a ser usado para a operação de restauração.</span><span class="sxs-lookup"><span data-stu-id="d85bb-142">The NuGet configuration file (*nuget.config*) to use for the restore operation.</span></span>

- **`--disable-parallel`**

  <span data-ttu-id="d85bb-143">Desabilita a restauração de vários projetos paralelamente.</span><span class="sxs-lookup"><span data-stu-id="d85bb-143">Disables restoring multiple projects in parallel.</span></span>

- **`--force`**

  <span data-ttu-id="d85bb-144">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="d85bb-144">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="d85bb-145">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="d85bb-145">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`--force-evaluate`**

  <span data-ttu-id="d85bb-146">As forças restauram para reavaliar todas as dependências, mesmo que um arquivo de bloqueio já exista.</span><span class="sxs-lookup"><span data-stu-id="d85bb-146">Forces restore to reevaluate all dependencies even if a lock file already exists.</span></span>

- **`-h|--help`**

  <span data-ttu-id="d85bb-147">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="d85bb-147">Prints out a short help for the command.</span></span>

- **`--ignore-failed-sources`**

  <span data-ttu-id="d85bb-148">Avise somente sobre fontes com falha se houver pacotes que atendem ao requisito de versão.</span><span class="sxs-lookup"><span data-stu-id="d85bb-148">Only warn about failed sources if there are packages meeting the version requirement.</span></span>

- **`--interactive`**

  <span data-ttu-id="d85bb-149">Permite que o comando pare e aguarde a entrada ou uma ação do usuário (por exemplo, para concluir a autenticação).</span><span class="sxs-lookup"><span data-stu-id="d85bb-149">Allows the command to stop and wait for user input or action (for example to complete authentication).</span></span> <span data-ttu-id="d85bb-150">A partir do .NET Core 2.1.400.</span><span class="sxs-lookup"><span data-stu-id="d85bb-150">Since .NET Core 2.1.400.</span></span>

- **`--lock-file-path <LOCK_FILE_PATH>`**

  <span data-ttu-id="d85bb-151">Local de saída onde o arquivo de bloqueio do projeto é gravado.</span><span class="sxs-lookup"><span data-stu-id="d85bb-151">Output location where project lock file is written.</span></span> <span data-ttu-id="d85bb-152">Por padrão, isso é *PROJECT_ROOT\packages.lock.json*.</span><span class="sxs-lookup"><span data-stu-id="d85bb-152">By default, this is *PROJECT_ROOT\packages.lock.json*.</span></span>

- **`--locked-mode`**

  <span data-ttu-id="d85bb-153">Não permita atualizar o arquivo de bloqueio do projeto.</span><span class="sxs-lookup"><span data-stu-id="d85bb-153">Don't allow updating project lock file.</span></span>

- **`--no-cache`**

  <span data-ttu-id="d85bb-154">Especifica para não armazenar solicitações HTTP.</span><span class="sxs-lookup"><span data-stu-id="d85bb-154">Specifies to not cache HTTP requests.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="d85bb-155">Ao restaurar um projeto com referências de P2P (projeto a projeto), restaura o projeto raiz, não as referências.</span><span class="sxs-lookup"><span data-stu-id="d85bb-155">When restoring a project with project-to-project (P2P) references, restores the root project and not the references.</span></span>

- **`--packages <PACKAGES_DIRECTORY>`**

  <span data-ttu-id="d85bb-156">Especifica o diretório para os pacotes restaurados.</span><span class="sxs-lookup"><span data-stu-id="d85bb-156">Specifies the directory for restored packages.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="d85bb-157">Especifica um runtime para a restauração do pacote.</span><span class="sxs-lookup"><span data-stu-id="d85bb-157">Specifies a runtime for the package restore.</span></span> <span data-ttu-id="d85bb-158">Isso é usado para restaurar pacotes para runtimes não listados explicitamente na marca `<RuntimeIdentifiers>` no arquivo *.csproj*.</span><span class="sxs-lookup"><span data-stu-id="d85bb-158">This is used to restore packages for runtimes not explicitly listed in the `<RuntimeIdentifiers>` tag in the *.csproj* file.</span></span> <span data-ttu-id="d85bb-159">Para obter uma lista de RIDs (Identificadores de Runtime), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="d85bb-159">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="d85bb-160">Forneça diversas RIDs especificando essa opção várias vezes.</span><span class="sxs-lookup"><span data-stu-id="d85bb-160">Provide multiple RIDs by specifying this option multiple times.</span></span>

- **`-s|--source <SOURCE>`**

  <span data-ttu-id="d85bb-161">Especifica uma origem de pacote NuGet a ser usada durante a operação de restauração.</span><span class="sxs-lookup"><span data-stu-id="d85bb-161">Specifies a NuGet package source to use during the restore operation.</span></span> <span data-ttu-id="d85bb-162">Essa configuração substitui todas as fontes especificadas nos arquivos *nuget.config*.</span><span class="sxs-lookup"><span data-stu-id="d85bb-162">This setting overrides all of the sources specified in the *nuget.config* files.</span></span> <span data-ttu-id="d85bb-163">Diversas fontes podem ser fornecidas especificando essa opção várias vezes.</span><span class="sxs-lookup"><span data-stu-id="d85bb-163">Multiple sources can be provided by specifying this option multiple times.</span></span>

- **`--use-lockfile`**

  <span data-ttu-id="d85bb-164">Permite que o arquivo de bloqueio do projeto seja gerado e usado com restauração.</span><span class="sxs-lookup"><span data-stu-id="d85bb-164">Enables project lock file to be generated and used with restore.</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="d85bb-165">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="d85bb-165">Sets the verbosity level of the command.</span></span> <span data-ttu-id="d85bb-166">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="d85bb-166">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="d85bb-167">O valor padrão é `minimal`.</span><span class="sxs-lookup"><span data-stu-id="d85bb-167">Default value is `minimal`.</span></span>

## <a name="examples"></a><span data-ttu-id="d85bb-168">Exemplos</span><span class="sxs-lookup"><span data-stu-id="d85bb-168">Examples</span></span>

- <span data-ttu-id="d85bb-169">Restaure as dependências e as ferramentas para o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="d85bb-169">Restore dependencies and tools for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet restore
  ```

- <span data-ttu-id="d85bb-170">Restaurar dependências e `app1` ferramentas para o projeto encontrado no caminho dado:</span><span class="sxs-lookup"><span data-stu-id="d85bb-170">Restore dependencies and tools for the `app1` project found in the   given path:</span></span>

  ```dotnetcli
  dotnet restore ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="d85bb-171">Restaurar as dependências e ferramentas para o projeto no diretório atual usando o caminho do arquivo fornecido como fonte:</span><span class="sxs-lookup"><span data-stu-id="d85bb-171">Restore the dependencies and tools for the project in the current   directory using the file path provided as the source:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages
  ```

- <span data-ttu-id="d85bb-172">Restaurar as dependências e ferramentas para o projeto no diretório atual usando os dois caminhos de arquivo fornecidos como fontes:</span><span class="sxs-lookup"><span data-stu-id="d85bb-172">Restore the dependencies and tools for the project in the current   directory using the two file paths provided as sources:</span></span>

  ```dotnetcli
  dotnet restore -s c:\packages\mypackages -s c:\packages\myotherpackages
  ```

- <span data-ttu-id="d85bb-173">Restaurar dependências e ferramentas para o projeto no diretório atual mostrando saída detalhada:</span><span class="sxs-lookup"><span data-stu-id="d85bb-173">Restore dependencies and tools for the project in the current directory   showing detailed output:</span></span>

  ```dotnetcli
  dotnet restore --verbosity detailed
  ```
