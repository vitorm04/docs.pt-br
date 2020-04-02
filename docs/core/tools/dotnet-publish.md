---
title: Comando dotnet publish
description: O comando dotnet publish publica um projeto ou solução .NET Core para um diretório.
ms.date: 02/24/2020
ms.openlocfilehash: 0e18220443f3713c86c257fcf401b98ddd716ebc
ms.sourcegitcommit: 961ec21c22d2f1d55c9cc8a7edf2ade1d1fd92e3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/02/2020
ms.locfileid: "80588277"
---
# <a name="dotnet-publish"></a><span data-ttu-id="242e7-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="242e7-103">dotnet publish</span></span>

<span data-ttu-id="242e7-104">**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="242e7-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="242e7-105">Nome</span><span class="sxs-lookup"><span data-stu-id="242e7-105">Name</span></span>

<span data-ttu-id="242e7-106">`dotnet publish`- Publica o aplicativo e suas dependências para uma pasta para implantação em um sistema de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="242e7-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="242e7-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="242e7-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration]
    [-f|--framework] [--force] [--interactive] [--manifest]
    [--no-build] [--no-dependencies] [--no-restore] [--nologo]
    [-o|--output] [-r|--runtime] [--self-contained]
    [--no-self-contained] [-v|--verbosity] [--version-suffix]

dotnet publish [-h|--help]
```

## <a name="description"></a><span data-ttu-id="242e7-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="242e7-108">Description</span></span>

<span data-ttu-id="242e7-109">`dotnet publish` compila o aplicativo, lê suas dependências especificadas no arquivo de projeto e publica o conjunto de arquivos resultantes em um diretório.</span><span class="sxs-lookup"><span data-stu-id="242e7-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="242e7-110">A saída inclui os seguintes ativos:</span><span class="sxs-lookup"><span data-stu-id="242e7-110">The output includes the following assets:</span></span>

- <span data-ttu-id="242e7-111">Código IL (Linguagem Intermediária) em um assembly com uma extensão *dll*.</span><span class="sxs-lookup"><span data-stu-id="242e7-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="242e7-112">Um arquivo *.deps.json* que inclui todas as dependências do projeto.</span><span class="sxs-lookup"><span data-stu-id="242e7-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="242e7-113">Um arquivo *.runtimeconfig.json* que especifica o tempo de execução compartilhado que o aplicativo espera, bem como outras opções de configuração para o tempo de execução (por exemplo, tipo de coleta de lixo).</span><span class="sxs-lookup"><span data-stu-id="242e7-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="242e7-114">As dependências do aplicativo, que são copiadas do cache NuGet para a pasta de saída.</span><span class="sxs-lookup"><span data-stu-id="242e7-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="242e7-115">A saída do comando `dotnet publish` está pronta para implantação em um sistema de hospedagem (por exemplo, um servidor, um computador, um Mac, um laptop) para execução.</span><span class="sxs-lookup"><span data-stu-id="242e7-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="242e7-116">É a única maneira com suporte oficial de preparar o aplicativo para implantação.</span><span class="sxs-lookup"><span data-stu-id="242e7-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="242e7-117">Dependendo do tipo de implantação especificado pelo projeto, talvez o sistema de hospedagem não tenha o runtime compartilhado do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="242e7-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="242e7-118">Para obter mais informações, consulte [Publicar os aplicativos .NET Core com o .NET Core CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="242e7-118">For more information, see [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

### <a name="msbuild"></a><span data-ttu-id="242e7-119">MSBuild</span><span class="sxs-lookup"><span data-stu-id="242e7-119">MSBuild</span></span>

<span data-ttu-id="242e7-120">O comando `dotnet publish` chama MSBuild, que invoca o destino `Publish`.</span><span class="sxs-lookup"><span data-stu-id="242e7-120">The `dotnet publish` command calls MSBuild, which invokes the `Publish` target.</span></span> <span data-ttu-id="242e7-121">Quaisquer parâmetros passados para `dotnet publish` são passados para o MSBuild.</span><span class="sxs-lookup"><span data-stu-id="242e7-121">Any parameters passed to `dotnet publish` are passed to MSBuild.</span></span> <span data-ttu-id="242e7-122">Os parâmetros `-c` e `-o` mapeiam as propriedades `Configuration` e `OutputPath` do MSBuild, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="242e7-122">The `-c` and `-o` parameters map to MSBuild's `Configuration` and `OutputPath` properties, respectively.</span></span>

<span data-ttu-id="242e7-123">O `dotnet publish` comando aceita opções de `-p` MSBuild, `-l` como para definir propriedades e definir um logger.</span><span class="sxs-lookup"><span data-stu-id="242e7-123">The `dotnet publish` command accepts MSBuild options, such as `-p` for setting properties and `-l` to define a logger.</span></span> <span data-ttu-id="242e7-124">Por exemplo, você pode definir uma propriedade MSBuild usando o formato: `-p:<NAME>=<VALUE>`.</span><span class="sxs-lookup"><span data-stu-id="242e7-124">For example, you can set an MSBuild property by using the format: `-p:<NAME>=<VALUE>`.</span></span> <span data-ttu-id="242e7-125">Você também pode definir propriedades relacionadas à publicação referindo-se a um arquivo *.pubxml,* por exemplo:</span><span class="sxs-lookup"><span data-stu-id="242e7-125">You can also set publish-related properties by referring to a *.pubxml* file, for example:</span></span>

```dotnetcli
dotnet publish -p:PublishProfile=Properties\PublishProfiles\FolderProfile.pubxml
```

<span data-ttu-id="242e7-126">Para saber mais, consulte os recursos a seguir:</span><span class="sxs-lookup"><span data-stu-id="242e7-126">For more information, see the following resources:</span></span>

- [<span data-ttu-id="242e7-127">Referência de linha de comando MSBuild</span><span class="sxs-lookup"><span data-stu-id="242e7-127">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="242e7-128">Visual Studio publica perfis (.pubxml) para implantação de aplicativos ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="242e7-128">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="242e7-129">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="242e7-129">dotnet msbuild</span></span>](dotnet-msbuild.md)

## <a name="arguments"></a><span data-ttu-id="242e7-130">Argumentos</span><span class="sxs-lookup"><span data-stu-id="242e7-130">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="242e7-131">O projeto ou solução para publicar.</span><span class="sxs-lookup"><span data-stu-id="242e7-131">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="242e7-132">`PROJECT`é o caminho e o nome de arquivo de um arquivo de projeto [C#,](csproj.md)F#ou Visual Basic, ou o caminho para um diretório que contém um arquivo de projeto C#, F#ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="242e7-132">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="242e7-133">Se o diretório não for especificado, ele será padrão para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="242e7-133">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="242e7-134">`SOLUTION`é o caminho e o nome de arquivo de um arquivo de solução (extensão *.sln)* ou o caminho para um diretório que contém um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="242e7-134">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="242e7-135">Se o diretório não for especificado, ele será padrão para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="242e7-135">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="242e7-136">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="242e7-136">Available since .NET Core 3.0 SDK.</span></span>

## <a name="options"></a><span data-ttu-id="242e7-137">Opções</span><span class="sxs-lookup"><span data-stu-id="242e7-137">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="242e7-138">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="242e7-138">Defines the build configuration.</span></span> <span data-ttu-id="242e7-139">O padrão para `Debug`a maioria dos projetos é, mas você pode substituir as configurações de configuração de compilação em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="242e7-139">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="242e7-140">Publica o aplicativo para a [estrutura de destino](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="242e7-140">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="242e7-141">Especifique a estrutura de destino no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="242e7-141">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="242e7-142">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="242e7-142">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="242e7-143">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="242e7-143">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="242e7-144">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="242e7-144">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="242e7-145">Permite que o comando pare e aguarde entrada ou ação do usuário.</span><span class="sxs-lookup"><span data-stu-id="242e7-145">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="242e7-146">Por exemplo, para concluir a autenticação.</span><span class="sxs-lookup"><span data-stu-id="242e7-146">For example, to complete authentication.</span></span> <span data-ttu-id="242e7-147">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="242e7-147">Available since .NET Core 3.0 SDK.</span></span>

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="242e7-148">Especifica um ou vários [manifestos de destino](../deploying/runtime-store.md) a serem usados para cortar o conjunto de pacotes publicados com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="242e7-148">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="242e7-149">O arquivo manifesto faz parte [ `dotnet store` ](dotnet-store.md)da saída do comando .</span><span class="sxs-lookup"><span data-stu-id="242e7-149">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="242e7-150">Para especificar vários manifestos, adicione uma opção `--manifest` para cada manifesto.</span><span class="sxs-lookup"><span data-stu-id="242e7-150">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="242e7-151">Não compila o projeto antes da publicação.</span><span class="sxs-lookup"><span data-stu-id="242e7-151">Doesn't build the project before publishing.</span></span> <span data-ttu-id="242e7-152">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="242e7-152">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="242e7-153">Ignora as referências projeto a projeto e só restaura o projeto raiz.</span><span class="sxs-lookup"><span data-stu-id="242e7-153">Ignores project-to-project references and only restores the root project.</span></span>

- **`--nologo`**

  <span data-ttu-id="242e7-154">Não exibe a faixa de inicialização nem a mensagem de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="242e7-154">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="242e7-155">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="242e7-155">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="242e7-156">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="242e7-156">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="242e7-157">Especifica o caminho para o diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="242e7-157">Specifies the path for the output directory.</span></span>
  
  <span data-ttu-id="242e7-158">Se não especificado, ele é padrão para *[project_file_folder]./bin/[configuração]/[framework]/publish/* para binários executáveis e multiplataformas dependentes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="242e7-158">If not specified, it defaults to *[project_file_folder]./bin/[configuration]/[framework]/publish/* for a runtime-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="242e7-159">Ele é padrão para *[project_file_folder]/bin/[configuração]/[framework]/[runtime]/publish/* para um executável independente.</span><span class="sxs-lookup"><span data-stu-id="242e7-159">It defaults to *[project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  - <span data-ttu-id="242e7-160">.NET Core 3.x SDK e posterior</span><span class="sxs-lookup"><span data-stu-id="242e7-160">.NET Core 3.x SDK and later</span></span>
  
    <span data-ttu-id="242e7-161">Se um caminho relativo for especificado ao publicar um projeto, o diretório de saída gerado será relativo ao diretório de trabalho atual, não à localização do arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="242e7-161">If a relative path is specified when publishing a project, the output directory generated is relative to the current working directory, not to the project file location.</span></span>

    <span data-ttu-id="242e7-162">Se um caminho relativo for especificado ao publicar uma solução, toda a saída para todos os projetos entrará na pasta especificada em relação ao diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="242e7-162">If a relative path is specified when publishing a solution, all output for all projects go into the specified folder relative to the current working directory.</span></span> <span data-ttu-id="242e7-163">Para fazer a saída de publicação ir para pastas separadas para `PublishDir` cada projeto, especifique um caminho relativo usando a propriedade msbuild em vez da `--output` opção.</span><span class="sxs-lookup"><span data-stu-id="242e7-163">To make publish output go to separate folders for each project, specify a relative path by using the msbuild `PublishDir` property instead of the `--output` option.</span></span> <span data-ttu-id="242e7-164">Por exemplo, `dotnet publish -p:PublishDir=.\publish` envia a saída `publish` de publicação de cada projeto para uma pasta sob a pasta que contém o arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="242e7-164">For example, `dotnet publish -p:PublishDir=.\publish` sends publish output for each project to a `publish` folder under the folder that contains the project file.</span></span>

  - <span data-ttu-id="242e7-165">.NET Core 2.x SDK</span><span class="sxs-lookup"><span data-stu-id="242e7-165">.NET Core 2.x SDK</span></span>
  
    <span data-ttu-id="242e7-166">Se um caminho relativo for especificado ao publicar um projeto, o diretório de saída gerado será relativo à localização do arquivo do projeto, não ao diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="242e7-166">If a relative path is specified when publishing a project, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

    <span data-ttu-id="242e7-167">Se um caminho relativo for especificado ao publicar uma solução, a saída de cada projeto será colocada em uma pasta separada em relação ao local do arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="242e7-167">If a relative path is specified when publishing a solution, each project's output goes into a separate folder relative to the project file location.</span></span> <span data-ttu-id="242e7-168">Se um caminho absoluto for especificado ao publicar uma solução, todas as saídas de publicação para todos os projetos serão colocadas na pasta especificada.</span><span class="sxs-lookup"><span data-stu-id="242e7-168">If an absolute path is specified when publishing a solution, all publish output for all projects goes into the specified folder.</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="242e7-169">Publica o runtime do .NET Core com seu aplicativo para que não seja necessário instalar o runtime no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="242e7-169">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="242e7-170">O `true` padrão é se um identificador de tempo de execução for especificado e o projeto for um projeto executável (não um projeto de biblioteca).</span><span class="sxs-lookup"><span data-stu-id="242e7-170">Default is `true` if a runtime identifier is specified and the project is an executable project (not a library project).</span></span> <span data-ttu-id="242e7-171">Para obter mais informações, consulte [a publicação do aplicativo .NET Core](../deploying/index.md) e publique os aplicativos [.NET Core com o .NET Core CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="242e7-171">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

  <span data-ttu-id="242e7-172">Se essa opção for `true` usada `false`sem `true`especificar ou, o padrão será .</span><span class="sxs-lookup"><span data-stu-id="242e7-172">If this option is used without specifying `true` or `false`, the default is `true`.</span></span> <span data-ttu-id="242e7-173">Nesse caso, não coloque a solução ou o `--self-contained`argumento `true` `false` do projeto imediatamente depois, porque ou é esperado nessa posição.</span><span class="sxs-lookup"><span data-stu-id="242e7-173">In that case, don't put the solution or project argument immediately after `--self-contained`, because `true` or `false` is expected in that position.</span></span>

- **`--no-self-contained`**

  <span data-ttu-id="242e7-174">Equivalente a `--self-contained false`.</span><span class="sxs-lookup"><span data-stu-id="242e7-174">Equivalent to `--self-contained false`.</span></span> <span data-ttu-id="242e7-175">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="242e7-175">Available since .NET Core 3.0 SDK.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="242e7-176">Publica o aplicativo para um determinado runtime.</span><span class="sxs-lookup"><span data-stu-id="242e7-176">Publishes the application for a given runtime.</span></span> <span data-ttu-id="242e7-177">Para obter uma lista de RIDs (Identificadores de Runtime), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="242e7-177">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="242e7-178">Para obter mais informações, consulte [a publicação do aplicativo .NET Core](../deploying/index.md) e publique os aplicativos [.NET Core com o .NET Core CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="242e7-178">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="242e7-179">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="242e7-179">Sets the verbosity level of the command.</span></span> <span data-ttu-id="242e7-180">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="242e7-180">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="242e7-181">O valor padrão é `minimal`.</span><span class="sxs-lookup"><span data-stu-id="242e7-181">Default value is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="242e7-182">Define o sufixo da versão para substituir o asterisco (`*`) no campo de versão do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="242e7-182">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="242e7-183">Exemplos</span><span class="sxs-lookup"><span data-stu-id="242e7-183">Examples</span></span>

- <span data-ttu-id="242e7-184">Crie um [binário multiplataforma dependente de tempo de execução](../deploying/index.md#produce-a-cross-platform-binary) para o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="242e7-184">Create a [runtime-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="242e7-185">Começando com o .NET Core 3.0 SDK, este exemplo também cria um [executável dependente de tempo de execução](../deploying/index.md#publish-runtime-dependent) para a plataforma atual.</span><span class="sxs-lookup"><span data-stu-id="242e7-185">Starting with .NET Core 3.0 SDK, this example also creates a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the current platform.</span></span>

- <span data-ttu-id="242e7-186">Crie um [executável independente](../deploying/index.md#publish-self-contained) para o projeto no diretório atual, por um tempo de execução específico:</span><span class="sxs-lookup"><span data-stu-id="242e7-186">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="242e7-187">O RID deve estar no arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="242e7-187">The RID must be in the project file.</span></span>

- <span data-ttu-id="242e7-188">Crie um [executável dependente de tempo de execução](../deploying/index.md#publish-runtime-dependent) para o projeto no diretório atual, para uma plataforma específica:</span><span class="sxs-lookup"><span data-stu-id="242e7-188">Create a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="242e7-189">O RID deve estar no arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="242e7-189">The RID must be in the project file.</span></span> <span data-ttu-id="242e7-190">Este exemplo se aplica ao .NET Core 3.0 SDK e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="242e7-190">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="242e7-191">Publique o projeto no diretório atual, para obter um tempo de execução específico e uma estrutura de destino:</span><span class="sxs-lookup"><span data-stu-id="242e7-191">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="242e7-192">Publicar o arquivo de projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="242e7-192">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="242e7-193">Publique o aplicativo atual, mas não restaure as referências p2P (project-to-project), apenas o projeto raiz durante a operação de restauração:</span><span class="sxs-lookup"><span data-stu-id="242e7-193">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="242e7-194">Confira também</span><span class="sxs-lookup"><span data-stu-id="242e7-194">See also</span></span>

- [<span data-ttu-id="242e7-195">Visão geral da publicação de aplicativos .NET Core</span><span class="sxs-lookup"><span data-stu-id="242e7-195">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="242e7-196">Publique os aplicativos .NET Core com o .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="242e7-196">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="242e7-197">Estruturas de destino</span><span class="sxs-lookup"><span data-stu-id="242e7-197">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="242e7-198">Catálogo de identificadores de execução (RID)</span><span class="sxs-lookup"><span data-stu-id="242e7-198">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="242e7-199">Trabalhando com nota nota notardo pelo macOS Catalina</span><span class="sxs-lookup"><span data-stu-id="242e7-199">Working with macOS Catalina Notarization</span></span>](../install/macos-notarization-issues.md)
- [<span data-ttu-id="242e7-200">Estrutura do diretório de um aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="242e7-200">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
- [<span data-ttu-id="242e7-201">Referência de linha de comando MSBuild</span><span class="sxs-lookup"><span data-stu-id="242e7-201">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="242e7-202">Visual Studio publica perfis (.pubxml) para implantação de aplicativos ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="242e7-202">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="242e7-203">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="242e7-203">dotnet msbuild</span></span>](dotnet-msbuild.md)
