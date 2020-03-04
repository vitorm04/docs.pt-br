---
title: Comando dotnet publish
description: O comando dotnet publish publica um projeto do .NET Core ou uma solução em um diretório.
ms.date: 02/24/2020
ms.openlocfilehash: cf41ee09244faad03feb8ccda19135b8c7780106
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/28/2020
ms.locfileid: "78156992"
---
# <a name="dotnet-publish"></a><span data-ttu-id="bbb13-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="bbb13-103">dotnet publish</span></span>

<span data-ttu-id="bbb13-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="bbb13-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="bbb13-105">Nome</span><span class="sxs-lookup"><span data-stu-id="bbb13-105">Name</span></span>

<span data-ttu-id="bbb13-106">`dotnet publish` – publica o aplicativo e suas dependências em uma pasta para implantação em um sistema de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="bbb13-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="bbb13-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="bbb13-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration] 
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a><span data-ttu-id="bbb13-108">DESCRIÇÃO</span><span class="sxs-lookup"><span data-stu-id="bbb13-108">Description</span></span>

<span data-ttu-id="bbb13-109">`dotnet publish` compila o aplicativo, lê suas dependências especificadas no arquivo de projeto e publica o conjunto de arquivos resultantes em um diretório.</span><span class="sxs-lookup"><span data-stu-id="bbb13-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="bbb13-110">A saída inclui os seguintes ativos:</span><span class="sxs-lookup"><span data-stu-id="bbb13-110">The output includes the following assets:</span></span>

- <span data-ttu-id="bbb13-111">Código IL (Linguagem Intermediária) em um assembly com uma extensão *dll*.</span><span class="sxs-lookup"><span data-stu-id="bbb13-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="bbb13-112">Um arquivo *. deps. JSON* que inclui todas as dependências do projeto.</span><span class="sxs-lookup"><span data-stu-id="bbb13-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="bbb13-113">Um arquivo *. runtimeconfig. JSON* que especifica o tempo de execução compartilhado que o aplicativo espera, bem como outras opções de configuração para o tempo de execução (por exemplo, tipo de coleta de lixo).</span><span class="sxs-lookup"><span data-stu-id="bbb13-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="bbb13-114">As dependências do aplicativo, que são copiadas do cache NuGet para a pasta de saída.</span><span class="sxs-lookup"><span data-stu-id="bbb13-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="bbb13-115">A saída do comando `dotnet publish` está pronta para implantação em um sistema de hospedagem (por exemplo, um servidor, um computador, um Mac, um laptop) para execução.</span><span class="sxs-lookup"><span data-stu-id="bbb13-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="bbb13-116">É a única maneira com suporte oficial de preparar o aplicativo para implantação.</span><span class="sxs-lookup"><span data-stu-id="bbb13-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="bbb13-117">Dependendo do tipo de implantação especificado pelo projeto, talvez o sistema de hospedagem não tenha o runtime compartilhado do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="bbb13-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span>

## <a name="arguments"></a><span data-ttu-id="bbb13-118">Argumentos</span><span class="sxs-lookup"><span data-stu-id="bbb13-118">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="bbb13-119">O projeto ou solução a ser publicada.</span><span class="sxs-lookup"><span data-stu-id="bbb13-119">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="bbb13-120">`PROJECT` é o caminho e o nome de [C#](csproj.md)arquivo F#de um Visual Basic de projeto, ou, ou o caminho para um diretório que C#contém F#um arquivo de projeto, ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="bbb13-120">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="bbb13-121">Se o diretório não for especificado, o padrão será o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="bbb13-121">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="bbb13-122">`SOLUTION` é o caminho e o nome do arquivo de uma solução (extensão *. sln* ) ou o caminho para um diretório que contém um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="bbb13-122">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="bbb13-123">Se o diretório não for especificado, o padrão será o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="bbb13-123">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="bbb13-124">**Disponível a partir do SDK do .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="bbb13-124">**Available starting with .NET Core 3.0 SDK.**</span></span> 

## <a name="options"></a><span data-ttu-id="bbb13-125">Opções</span><span class="sxs-lookup"><span data-stu-id="bbb13-125">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="bbb13-126">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="bbb13-126">Defines the build configuration.</span></span> <span data-ttu-id="bbb13-127">O padrão para a maioria dos projetos é `Debug`, mas você pode substituir as definições de configuração de compilação em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="bbb13-127">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="bbb13-128">Publica o aplicativo para a [estrutura de destino](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="bbb13-128">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="bbb13-129">Especifique a estrutura de destino no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="bbb13-129">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="bbb13-130">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="bbb13-130">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="bbb13-131">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="bbb13-131">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="bbb13-132">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="bbb13-132">Prints out a short help for the command.</span></span>

- <span data-ttu-id="bbb13-133">**`--interactive`** **disponível a partir do SDK do .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="bbb13-133">**`--interactive`** **Available starting with .NET Core 3.0 SDK.**</span></span>

  <span data-ttu-id="bbb13-134">Permite que o comando pare e aguarde entrada ou ação do usuário.</span><span class="sxs-lookup"><span data-stu-id="bbb13-134">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="bbb13-135">Por exemplo, para concluir a autenticação.</span><span class="sxs-lookup"><span data-stu-id="bbb13-135">For example, to complete authentication.</span></span> 

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="bbb13-136">Especifica um ou vários [manifestos de destino](../deploying/runtime-store.md) a serem usados para cortar o conjunto de pacotes publicados com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="bbb13-136">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="bbb13-137">O arquivo de manifesto faz parte da saída do [comando `dotnet store`](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="bbb13-137">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="bbb13-138">Para especificar vários manifestos, adicione uma opção `--manifest` para cada manifesto.</span><span class="sxs-lookup"><span data-stu-id="bbb13-138">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="bbb13-139">Não compila o projeto antes da publicação.</span><span class="sxs-lookup"><span data-stu-id="bbb13-139">Doesn't build the project before publishing.</span></span> <span data-ttu-id="bbb13-140">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="bbb13-140">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="bbb13-141">Ignora as referências projeto a projeto e só restaura o projeto raiz.</span><span class="sxs-lookup"><span data-stu-id="bbb13-141">Ignores project-to-project references and only restores the root project.</span></span>

- <span data-ttu-id="bbb13-142">**`--nologo`** **disponível a partir do SDK do .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="bbb13-142">**`--nologo`** **Available starting with .NET Core 3.0 SDK.**</span></span>

  <span data-ttu-id="bbb13-143">Não exibe a faixa de inicialização nem a mensagem de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="bbb13-143">Doesn't display the startup banner or the copyright message.</span></span> 

- **`--no-restore`**

  <span data-ttu-id="bbb13-144">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="bbb13-144">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="bbb13-145">Especifica o caminho para o diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="bbb13-145">Specifies the path for the output directory.</span></span> <span data-ttu-id="bbb13-146">Se não for especificado, o padrão será *./bin/[Configuration]/[Framework]/Publish/* para um executável dependente de tempo de execução e binários de plataforma cruzada.</span><span class="sxs-lookup"><span data-stu-id="bbb13-146">If not specified, it defaults to *./bin/[configuration]/[framework]/publish/* for a runtime-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="bbb13-147">O padrão é *./bin/[Configuration]/[Framework]/[Runtime]/Publish/* para um executável independente.</span><span class="sxs-lookup"><span data-stu-id="bbb13-147">It defaults to *./bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  <span data-ttu-id="bbb13-148">Se o caminho for relativo, o diretório de saída gerado será relativo ao local do arquivo de projeto, não ao diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="bbb13-148">If the path is relative, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="bbb13-149">Publica o runtime do .NET Core com seu aplicativo para que não seja necessário instalar o runtime no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="bbb13-149">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="bbb13-150">O padrão será `true` se um identificador de tempo de execução for especificado.</span><span class="sxs-lookup"><span data-stu-id="bbb13-150">Default is `true` if a runtime identifier is specified.</span></span> <span data-ttu-id="bbb13-151">Para obter mais informações, consulte [publicação de aplicativos do .NET Core](../deploying/index.md) e [publicar aplicativos .net core com o CLI do .NET Core](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="bbb13-151">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- <span data-ttu-id="bbb13-152">**`--no-self-contained`** **disponível a partir do SDK do .NET Core 3,0.**</span><span class="sxs-lookup"><span data-stu-id="bbb13-152">**`--no-self-contained`**  **Available starting with .NET Core 3.0 SDK.**</span></span>

  <span data-ttu-id="bbb13-153">Equivalente a `--self-contained false`.</span><span class="sxs-lookup"><span data-stu-id="bbb13-153">Equivalent to `--self-contained false`.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="bbb13-154">Publica o aplicativo para um determinado runtime.</span><span class="sxs-lookup"><span data-stu-id="bbb13-154">Publishes the application for a given runtime.</span></span> <span data-ttu-id="bbb13-155">Para obter uma lista de RIDs (Identificadores de Runtime), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="bbb13-155">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="bbb13-156">Para obter mais informações, consulte [publicação de aplicativos do .NET Core](../deploying/index.md) e [publicar aplicativos .net core com o CLI do .NET Core](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="bbb13-156">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="bbb13-157">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="bbb13-157">Sets the verbosity level of the command.</span></span> <span data-ttu-id="bbb13-158">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="bbb13-158">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="bbb13-159">Define o sufixo da versão para substituir o asterisco (`*`) no campo de versão do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="bbb13-159">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="bbb13-160">Exemplos</span><span class="sxs-lookup"><span data-stu-id="bbb13-160">Examples</span></span>

- <span data-ttu-id="bbb13-161">Crie um [binário de plataforma cruzada dependente de tempo de execução](../deploying/index.md#produce-a-cross-platform-binary) para o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="bbb13-161">Create a [runtime-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="bbb13-162">A partir do SDK do .NET Core 3,0, este exemplo também cria um [executável dependente de tempo de execução](../deploying/index.md#publish-runtime-dependent) para a plataforma atual.</span><span class="sxs-lookup"><span data-stu-id="bbb13-162">Starting with .NET Core 3.0 SDK, this example also creates a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the current platform.</span></span>

- <span data-ttu-id="bbb13-163">Crie um [executável independente](../deploying/index.md#publish-self-contained) para o projeto no diretório atual, para um tempo de execução específico:</span><span class="sxs-lookup"><span data-stu-id="bbb13-163">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="bbb13-164">O RID deve estar no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="bbb13-164">The RID must be in the project file.</span></span>

- <span data-ttu-id="bbb13-165">Crie um [executável dependente de tempo de execução](../deploying/index.md#publish-runtime-dependent) para o projeto no diretório atual, para uma plataforma específica:</span><span class="sxs-lookup"><span data-stu-id="bbb13-165">Create a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="bbb13-166">O RID deve estar no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="bbb13-166">The RID must be in the project file.</span></span> <span data-ttu-id="bbb13-167">Este exemplo se aplica ao SDK do .NET Core 3,0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="bbb13-167">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="bbb13-168">Publicar o projeto no diretório atual, para um tempo de execução e estrutura de destino específicos:</span><span class="sxs-lookup"><span data-stu-id="bbb13-168">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="bbb13-169">Publicar o arquivo de projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="bbb13-169">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="bbb13-170">Publicar o aplicativo atual, mas não restaurar referências ponto a projeto (P2P), apenas o projeto raiz durante a operação de restauração:</span><span class="sxs-lookup"><span data-stu-id="bbb13-170">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="bbb13-171">Confira também</span><span class="sxs-lookup"><span data-stu-id="bbb13-171">See also</span></span>

- [<span data-ttu-id="bbb13-172">Visão geral da publicação de aplicativos do .NET Core</span><span class="sxs-lookup"><span data-stu-id="bbb13-172">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="bbb13-173">Publicar aplicativos .NET Core com o CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="bbb13-173">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="bbb13-174">Estruturas de destino</span><span class="sxs-lookup"><span data-stu-id="bbb13-174">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="bbb13-175">Catálogo de RID (Identificador de Runtime)</span><span class="sxs-lookup"><span data-stu-id="bbb13-175">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- <span data-ttu-id="bbb13-176">[Trabalhando com o notarization Catalina do MacOS](../install/macos-notarization-issues.md) Para obter mais informações, consulte os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="bbb13-176">[Working with macOS Catalina Notarization](../install/macos-notarization-issues.md) For more information, see he following resources:</span></span>
- [<span data-ttu-id="bbb13-177">Estrutura de diretórios de um aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="bbb13-177">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
