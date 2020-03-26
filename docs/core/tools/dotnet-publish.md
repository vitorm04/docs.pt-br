---
title: Comando dotnet publish
description: O comando dotnet publish publica um projeto ou solução .NET Core para um diretório.
ms.date: 02/24/2020
ms.openlocfilehash: ed5b87b3343210ca81486ef4b9a9d70d1b534464
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/21/2020
ms.locfileid: "80110965"
---
# <a name="dotnet-publish"></a><span data-ttu-id="73631-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="73631-103">dotnet publish</span></span>

<span data-ttu-id="73631-104">**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="73631-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="73631-105">Nome</span><span class="sxs-lookup"><span data-stu-id="73631-105">Name</span></span>

<span data-ttu-id="73631-106">`dotnet publish`- Publica o aplicativo e suas dependências para uma pasta para implantação em um sistema de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="73631-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="73631-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="73631-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration]
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a><span data-ttu-id="73631-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="73631-108">Description</span></span>

<span data-ttu-id="73631-109">`dotnet publish` compila o aplicativo, lê suas dependências especificadas no arquivo de projeto e publica o conjunto de arquivos resultantes em um diretório.</span><span class="sxs-lookup"><span data-stu-id="73631-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="73631-110">A saída inclui os seguintes ativos:</span><span class="sxs-lookup"><span data-stu-id="73631-110">The output includes the following assets:</span></span>

- <span data-ttu-id="73631-111">Código IL (Linguagem Intermediária) em um assembly com uma extensão *dll*.</span><span class="sxs-lookup"><span data-stu-id="73631-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="73631-112">Um arquivo *.deps.json* que inclui todas as dependências do projeto.</span><span class="sxs-lookup"><span data-stu-id="73631-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="73631-113">Um arquivo *.runtimeconfig.json* que especifica o tempo de execução compartilhado que o aplicativo espera, bem como outras opções de configuração para o tempo de execução (por exemplo, tipo de coleta de lixo).</span><span class="sxs-lookup"><span data-stu-id="73631-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="73631-114">As dependências do aplicativo, que são copiadas do cache NuGet para a pasta de saída.</span><span class="sxs-lookup"><span data-stu-id="73631-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="73631-115">A saída do comando `dotnet publish` está pronta para implantação em um sistema de hospedagem (por exemplo, um servidor, um computador, um Mac, um laptop) para execução.</span><span class="sxs-lookup"><span data-stu-id="73631-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="73631-116">É a única maneira com suporte oficial de preparar o aplicativo para implantação.</span><span class="sxs-lookup"><span data-stu-id="73631-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="73631-117">Dependendo do tipo de implantação especificado pelo projeto, talvez o sistema de hospedagem não tenha o runtime compartilhado do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="73631-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span>

## <a name="arguments"></a><span data-ttu-id="73631-118">Argumentos</span><span class="sxs-lookup"><span data-stu-id="73631-118">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="73631-119">O projeto ou solução para publicar.</span><span class="sxs-lookup"><span data-stu-id="73631-119">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="73631-120">`PROJECT`é o caminho e o nome de arquivo de um arquivo de projeto [C#,](csproj.md)F#ou Visual Basic, ou o caminho para um diretório que contém um arquivo de projeto C#, F#ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="73631-120">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="73631-121">Se o diretório não for especificado, ele será padrão para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="73631-121">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="73631-122">`SOLUTION`é o caminho e o nome de arquivo de um arquivo de solução (extensão *.sln)* ou o caminho para um diretório que contém um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="73631-122">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="73631-123">Se o diretório não for especificado, ele será padrão para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="73631-123">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="73631-124">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="73631-124">Available since .NET Core 3.0 SDK.</span></span>

## <a name="options"></a><span data-ttu-id="73631-125">Opções</span><span class="sxs-lookup"><span data-stu-id="73631-125">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="73631-126">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="73631-126">Defines the build configuration.</span></span> <span data-ttu-id="73631-127">O padrão para `Debug`a maioria dos projetos é, mas você pode substituir as configurações de configuração de compilação em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="73631-127">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="73631-128">Publica o aplicativo para a [estrutura de destino](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="73631-128">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="73631-129">Especifique a estrutura de destino no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="73631-129">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="73631-130">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="73631-130">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="73631-131">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="73631-131">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="73631-132">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="73631-132">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="73631-133">Permite que o comando pare e aguarde entrada ou ação do usuário.</span><span class="sxs-lookup"><span data-stu-id="73631-133">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="73631-134">Por exemplo, para concluir a autenticação.</span><span class="sxs-lookup"><span data-stu-id="73631-134">For example, to complete authentication.</span></span> <span data-ttu-id="73631-135">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="73631-135">Available since .NET Core 3.0 SDK.</span></span>

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="73631-136">Especifica um ou vários [manifestos de destino](../deploying/runtime-store.md) a serem usados para cortar o conjunto de pacotes publicados com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="73631-136">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="73631-137">O arquivo manifesto faz parte [ `dotnet store` ](dotnet-store.md)da saída do comando .</span><span class="sxs-lookup"><span data-stu-id="73631-137">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="73631-138">Para especificar vários manifestos, adicione uma opção `--manifest` para cada manifesto.</span><span class="sxs-lookup"><span data-stu-id="73631-138">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="73631-139">Não compila o projeto antes da publicação.</span><span class="sxs-lookup"><span data-stu-id="73631-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="73631-140">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="73631-140">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="73631-141">Ignora as referências projeto a projeto e só restaura o projeto raiz.</span><span class="sxs-lookup"><span data-stu-id="73631-141">Ignores project-to-project references and only restores the root project.</span></span>

- **`--nologo`**

  <span data-ttu-id="73631-142">Não exibe a faixa de inicialização nem a mensagem de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="73631-142">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="73631-143">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="73631-143">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="73631-144">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="73631-144">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="73631-145">Especifica o caminho para o diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="73631-145">Specifies the path for the output directory.</span></span> <span data-ttu-id="73631-146">Se não especificado, ele é padrão para *./bin/[configuração]/[framework]/publish/* para binários executáveis e multiplataformas dependentes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="73631-146">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a runtime-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="73631-147">Ele é padrão para *./bin/[configuração]/[framework]/[runtime]/publish/* para um executável independente.</span><span class="sxs-lookup"><span data-stu-id="73631-147">It defaults to *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  <span data-ttu-id="73631-148">Se o caminho for relativo, o diretório de saída gerado será relativo ao local do arquivo de projeto, não ao diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="73631-148">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="73631-149">Publica o runtime do .NET Core com seu aplicativo para que não seja necessário instalar o runtime no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="73631-149">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="73631-150">O `true` padrão é se um identificador de tempo de execução for especificado.</span><span class="sxs-lookup"><span data-stu-id="73631-150">Default is `true` if a runtime identifier is specified.</span></span> <span data-ttu-id="73631-151">Para obter mais informações, consulte [a publicação do aplicativo .NET Core](../deploying/index.md) e publique os aplicativos [.NET Core com o .NET Core CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="73631-151">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`--no-self-contained`**

  <span data-ttu-id="73631-152">Equivalente a `--self-contained false`.</span><span class="sxs-lookup"><span data-stu-id="73631-152">Equivalent to `--self-contained false`.</span></span> <span data-ttu-id="73631-153">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="73631-153">Available since .NET Core 3.0 SDK.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="73631-154">Publica o aplicativo para um determinado runtime.</span><span class="sxs-lookup"><span data-stu-id="73631-154">Publishes the application for a given runtime.</span></span> <span data-ttu-id="73631-155">Para obter uma lista de RIDs (Identificadores de Runtime), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="73631-155">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="73631-156">Para obter mais informações, consulte [a publicação do aplicativo .NET Core](../deploying/index.md) e publique os aplicativos [.NET Core com o .NET Core CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="73631-156">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="73631-157">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="73631-157">Sets the verbosity level of the command.</span></span> <span data-ttu-id="73631-158">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="73631-158">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="73631-159">O valor padrão é `minimal`.</span><span class="sxs-lookup"><span data-stu-id="73631-159">Default value is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="73631-160">Define o sufixo da versão para substituir o asterisco (`*`) no campo de versão do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="73631-160">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="73631-161">Exemplos</span><span class="sxs-lookup"><span data-stu-id="73631-161">Examples</span></span>

- <span data-ttu-id="73631-162">Crie um [binário multiplataforma dependente de tempo de execução](../deploying/index.md#produce-a-cross-platform-binary) para o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="73631-162">Create a [runtime-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="73631-163">Começando com o .NET Core 3.0 SDK, este exemplo também cria um [executável dependente de tempo de execução](../deploying/index.md#publish-runtime-dependent) para a plataforma atual.</span><span class="sxs-lookup"><span data-stu-id="73631-163">Starting with .NET Core 3.0 SDK, this example also creates a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the current platform.</span></span>

- <span data-ttu-id="73631-164">Crie um [executável independente](../deploying/index.md#publish-self-contained) para o projeto no diretório atual, por um tempo de execução específico:</span><span class="sxs-lookup"><span data-stu-id="73631-164">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="73631-165">O RID deve estar no arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="73631-165">The RID must be in the project file.</span></span>

- <span data-ttu-id="73631-166">Crie um [executável dependente de tempo de execução](../deploying/index.md#publish-runtime-dependent) para o projeto no diretório atual, para uma plataforma específica:</span><span class="sxs-lookup"><span data-stu-id="73631-166">Create a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="73631-167">O RID deve estar no arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="73631-167">The RID must be in the project file.</span></span> <span data-ttu-id="73631-168">Este exemplo se aplica ao .NET Core 3.0 SDK e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="73631-168">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="73631-169">Publique o projeto no diretório atual, para obter um tempo de execução específico e uma estrutura de destino:</span><span class="sxs-lookup"><span data-stu-id="73631-169">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="73631-170">Publicar o arquivo de projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="73631-170">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="73631-171">Publique o aplicativo atual, mas não restaure as referências p2P (project-to-project), apenas o projeto raiz durante a operação de restauração:</span><span class="sxs-lookup"><span data-stu-id="73631-171">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="73631-172">Confira também</span><span class="sxs-lookup"><span data-stu-id="73631-172">See also</span></span>

- [<span data-ttu-id="73631-173">Visão geral da publicação de aplicativos .NET Core</span><span class="sxs-lookup"><span data-stu-id="73631-173">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="73631-174">Publique os aplicativos .NET Core com o .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="73631-174">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="73631-175">Estruturas de destino</span><span class="sxs-lookup"><span data-stu-id="73631-175">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="73631-176">Catálogo de identificadores de execução (RID)</span><span class="sxs-lookup"><span data-stu-id="73631-176">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="73631-177">Trabalhando com nota nota notardo pelo macOS Catalina</span><span class="sxs-lookup"><span data-stu-id="73631-177">Working with macOS Catalina Notarization</span></span>](../install/macos-notarization-issues.md)
- [<span data-ttu-id="73631-178">Estrutura do diretório de um aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="73631-178">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
