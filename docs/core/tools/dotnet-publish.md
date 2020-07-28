---
title: Comando dotnet publish
description: O comando dotnet publish publica um projeto do .NET Core ou uma solução em um diretório.
ms.date: 02/24/2020
ms.openlocfilehash: 59fdbfa875dad13963ae198acc6a31b537279dfe
ms.sourcegitcommit: c8c3e1c63a00b7d27f76f5e50ee6469e6bdc8987
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/28/2020
ms.locfileid: "87251173"
---
# <a name="dotnet-publish"></a><span data-ttu-id="ddd32-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="ddd32-103">dotnet publish</span></span>

<span data-ttu-id="ddd32-104">**Este artigo aplica-se a:** ✔️ SDK do .net Core 2,1 e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="ddd32-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="ddd32-105">Nome</span><span class="sxs-lookup"><span data-stu-id="ddd32-105">Name</span></span>

<span data-ttu-id="ddd32-106">`dotnet publish`– Publica o aplicativo e suas dependências em uma pasta para implantação em um sistema de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="ddd32-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="ddd32-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="ddd32-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive]
    [--manifest <PATH_TO_MANIFEST_FILE>] [--no-build] [--no-dependencies]
    [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-p:PublishReadyToRun=true] [-p:PublishSingleFile=true] [-p:PublishTrimmed=true]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [--self-contained [true|false]]
    [--no-self-contained] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet publish -h|--help
```

## <a name="description"></a><span data-ttu-id="ddd32-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="ddd32-108">Description</span></span>

<span data-ttu-id="ddd32-109">`dotnet publish` compila o aplicativo, lê suas dependências especificadas no arquivo de projeto e publica o conjunto de arquivos resultantes em um diretório.</span><span class="sxs-lookup"><span data-stu-id="ddd32-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="ddd32-110">A saída inclui os seguintes ativos:</span><span class="sxs-lookup"><span data-stu-id="ddd32-110">The output includes the following assets:</span></span>

- <span data-ttu-id="ddd32-111">Código IL (Linguagem Intermediária) em um assembly com uma extensão *dll*.</span><span class="sxs-lookup"><span data-stu-id="ddd32-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="ddd32-112">Um *.deps.jsno* arquivo que inclui todas as dependências do projeto.</span><span class="sxs-lookup"><span data-stu-id="ddd32-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="ddd32-113">Um *.runtimeconfig.jsno* arquivo que especifica o tempo de execução compartilhado que o aplicativo espera, bem como outras opções de configuração para o tempo de execução (por exemplo, tipo de coleta de lixo).</span><span class="sxs-lookup"><span data-stu-id="ddd32-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="ddd32-114">As dependências do aplicativo, que são copiadas do cache NuGet para a pasta de saída.</span><span class="sxs-lookup"><span data-stu-id="ddd32-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="ddd32-115">A saída do comando `dotnet publish` está pronta para implantação em um sistema de hospedagem (por exemplo, um servidor, um computador, um Mac, um laptop) para execução.</span><span class="sxs-lookup"><span data-stu-id="ddd32-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="ddd32-116">É a única maneira com suporte oficial de preparar o aplicativo para implantação.</span><span class="sxs-lookup"><span data-stu-id="ddd32-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="ddd32-117">Dependendo do tipo de implantação especificado pelo projeto, talvez o sistema de hospedagem não tenha o runtime compartilhado do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="ddd32-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="ddd32-118">Para obter mais informações, consulte [publicar aplicativos .NET Core com o CLI do .NET Core](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="ddd32-118">For more information, see [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

### <a name="implicit-restore"></a><span data-ttu-id="ddd32-119">Restauração implícita</span><span class="sxs-lookup"><span data-stu-id="ddd32-119">Implicit restore</span></span>

[!INCLUDE[dotnet restore note](~/includes/dotnet-restore-note.md)]

### <a name="msbuild"></a><span data-ttu-id="ddd32-120">MSBuild</span><span class="sxs-lookup"><span data-stu-id="ddd32-120">MSBuild</span></span>

<span data-ttu-id="ddd32-121">O comando `dotnet publish` chama MSBuild, que invoca o destino `Publish`.</span><span class="sxs-lookup"><span data-stu-id="ddd32-121">The `dotnet publish` command calls MSBuild, which invokes the `Publish` target.</span></span> <span data-ttu-id="ddd32-122">Quaisquer parâmetros passados para `dotnet publish` são passados para o MSBuild.</span><span class="sxs-lookup"><span data-stu-id="ddd32-122">Any parameters passed to `dotnet publish` are passed to MSBuild.</span></span> <span data-ttu-id="ddd32-123">Os parâmetros `-c` e `-o` mapeiam as propriedades `Configuration` e `PublishDir` do MSBuild, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="ddd32-123">The `-c` and `-o` parameters map to MSBuild's `Configuration` and `PublishDir` properties, respectively.</span></span>

<span data-ttu-id="ddd32-124">O `dotnet publish` comando aceita opções do MSBuild, como `-p` para configurar propriedades e `-l` definir um agente de log.</span><span class="sxs-lookup"><span data-stu-id="ddd32-124">The `dotnet publish` command accepts MSBuild options, such as `-p` for setting properties and `-l` to define a logger.</span></span> <span data-ttu-id="ddd32-125">Por exemplo, você pode definir uma propriedade do MSBuild usando o formato: `-p:<NAME>=<VALUE>` .</span><span class="sxs-lookup"><span data-stu-id="ddd32-125">For example, you can set an MSBuild property by using the format: `-p:<NAME>=<VALUE>`.</span></span> <span data-ttu-id="ddd32-126">Você também pode definir propriedades relacionadas à publicação fazendo referência a um arquivo *. pubxml* , por exemplo:</span><span class="sxs-lookup"><span data-stu-id="ddd32-126">You can also set publish-related properties by referring to a *.pubxml* file, for example:</span></span>

```dotnetcli
dotnet publish -p:PublishProfile=FolderProfile
```

<span data-ttu-id="ddd32-127">O exemplo anterior usa o arquivo *FolderProfile. pubxml* que é encontrado na pasta \* \<project_folder> /Properties/PublishProfiles\* .</span><span class="sxs-lookup"><span data-stu-id="ddd32-127">The preceding example uses the *FolderProfile.pubxml* file that is found in the *\<project_folder>/Properties/PublishProfiles* folder.</span></span> <span data-ttu-id="ddd32-128">Se você especificar um caminho e uma extensão de arquivo ao definir a `PublishProfile` propriedade, eles serão ignorados.</span><span class="sxs-lookup"><span data-stu-id="ddd32-128">If you specify a path and file extension when setting the `PublishProfile` property, they are ignored.</span></span> <span data-ttu-id="ddd32-129">Por padrão, o MSBuild procura na pasta *Properties/PublishProfiles* e assume a extensão de arquivo *pubxml* .</span><span class="sxs-lookup"><span data-stu-id="ddd32-129">MSBuild by default looks in the *Properties/PublishProfiles* folder and assumes the *pubxml* file extension.</span></span> <span data-ttu-id="ddd32-130">Para especificar o caminho e o nome de arquivo, incluindo a extensão, defina a `PublishProfileFullPath` propriedade em vez da `PublishProfile` propriedade.</span><span class="sxs-lookup"><span data-stu-id="ddd32-130">To specify the path and filename including extension, set the `PublishProfileFullPath` property instead of the `PublishProfile` property.</span></span>

<span data-ttu-id="ddd32-131">Para obter mais informações, consulte os seguintes recursos:</span><span class="sxs-lookup"><span data-stu-id="ddd32-131">For more information, see the following resources:</span></span>

- [<span data-ttu-id="ddd32-132">Referência de linha de comando do MSBuild</span><span class="sxs-lookup"><span data-stu-id="ddd32-132">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="ddd32-133">Perfis de publicação do Visual Studio (. pubxml) para implantação de aplicativo ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ddd32-133">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="ddd32-134">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="ddd32-134">dotnet msbuild</span></span>](dotnet-msbuild.md)

## <a name="arguments"></a><span data-ttu-id="ddd32-135">Argumentos</span><span class="sxs-lookup"><span data-stu-id="ddd32-135">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="ddd32-136">O projeto ou solução a ser publicada.</span><span class="sxs-lookup"><span data-stu-id="ddd32-136">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="ddd32-137">`PROJECT`é o caminho e o nome de arquivo de um Visual Basic de projeto em [c#](csproj.md), f # ou Visual Basic, ou o caminho para um diretório que contém um arquivo de projeto C#, f # ou.</span><span class="sxs-lookup"><span data-stu-id="ddd32-137">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="ddd32-138">Se o diretório não for especificado, o padrão será o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="ddd32-138">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="ddd32-139">`SOLUTION`é o caminho e o nome de arquivo de uma solução (extensão *. sln* ) ou o caminho para um diretório que contém um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="ddd32-139">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="ddd32-140">Se o diretório não for especificado, o padrão será o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="ddd32-140">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="ddd32-141">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ddd32-141">Available since .NET Core 3.0 SDK.</span></span>

## <a name="options"></a><span data-ttu-id="ddd32-142">Opções</span><span class="sxs-lookup"><span data-stu-id="ddd32-142">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="ddd32-143">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="ddd32-143">Defines the build configuration.</span></span> <span data-ttu-id="ddd32-144">O padrão para a maioria dos projetos é `Debug` , mas você pode substituir as definições de configuração de compilação em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="ddd32-144">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="ddd32-145">Publica o aplicativo para a [estrutura de destino](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="ddd32-145">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="ddd32-146">Especifique a estrutura de destino no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="ddd32-146">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="ddd32-147">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="ddd32-147">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="ddd32-148">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="ddd32-148">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="ddd32-149">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="ddd32-149">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="ddd32-150">Permite que o comando pare e aguarde entrada ou ação do usuário.</span><span class="sxs-lookup"><span data-stu-id="ddd32-150">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="ddd32-151">Por exemplo, para concluir a autenticação.</span><span class="sxs-lookup"><span data-stu-id="ddd32-151">For example, to complete authentication.</span></span> <span data-ttu-id="ddd32-152">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ddd32-152">Available since .NET Core 3.0 SDK.</span></span>

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="ddd32-153">Especifica um ou vários [manifestos de destino](../deploying/runtime-store.md) a serem usados para cortar o conjunto de pacotes publicados com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ddd32-153">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="ddd32-154">O arquivo de manifesto faz parte da saída do [ `dotnet store` comando](dotnet-store.md).</span><span class="sxs-lookup"><span data-stu-id="ddd32-154">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="ddd32-155">Para especificar vários manifestos, adicione uma opção `--manifest` para cada manifesto.</span><span class="sxs-lookup"><span data-stu-id="ddd32-155">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="ddd32-156">Não compila o projeto antes da publicação.</span><span class="sxs-lookup"><span data-stu-id="ddd32-156">Doesn't build the project before publishing.</span></span> <span data-ttu-id="ddd32-157">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="ddd32-157">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="ddd32-158">Ignora as referências projeto a projeto e só restaura o projeto raiz.</span><span class="sxs-lookup"><span data-stu-id="ddd32-158">Ignores project-to-project references and only restores the root project.</span></span>

- **`--nologo`**

  <span data-ttu-id="ddd32-159">Não exibe a faixa de inicialização nem a mensagem de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="ddd32-159">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="ddd32-160">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ddd32-160">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="ddd32-161">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="ddd32-161">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="ddd32-162">Especifica o caminho para o diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="ddd32-162">Specifies the path for the output directory.</span></span>
  
  <span data-ttu-id="ddd32-163">Se não for especificado, o padrão é *[project_file_folder]./bin/[Configuration]/[Framework]/Publish/* para um executável dependente de tempo de execução e binários de plataforma cruzada.</span><span class="sxs-lookup"><span data-stu-id="ddd32-163">If not specified, it defaults to *[project_file_folder]./bin/[configuration]/[framework]/publish/* for a runtime-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="ddd32-164">O padrão é *[project_file_folder]/bin/[Configuration]/[Framework]/[Runtime]/Publish/* para um executável independente.</span><span class="sxs-lookup"><span data-stu-id="ddd32-164">It defaults to *[project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  <span data-ttu-id="ddd32-165">Em um projeto Web, se a pasta de saída estiver na pasta do projeto, os `dotnet publish` comandos sucessivos resultarão em pastas de saída aninhadas.</span><span class="sxs-lookup"><span data-stu-id="ddd32-165">In a web project, if the output folder is in the project folder, successive `dotnet publish` commands result in nested output folders.</span></span> <span data-ttu-id="ddd32-166">Por exemplo, se a pasta do projeto *for MyProject*e a pasta de saída de publicação for *MyProject/Publish*e você `dotnet publish` executar duas vezes, a segunda execução colocará arquivos de conteúdo como arquivos *. config* e *. JSON* no *MyProject/publicar/Publish*.</span><span class="sxs-lookup"><span data-stu-id="ddd32-166">For example, if the project folder is *myproject*, and the publish output folder is *myproject/publish*, and you run `dotnet publish` twice, the second run puts content files such as *.config* and *.json* files in *myproject/publish/publish*.</span></span> <span data-ttu-id="ddd32-167">Para evitar o aninhamento de pastas de publicação, especifique uma pasta de publicação que não esteja **diretamente** sob a pasta do projeto ou exclua a pasta de publicação do projeto.</span><span class="sxs-lookup"><span data-stu-id="ddd32-167">To avoid nesting publish folders, specify a publish folder that is not **directly** under the project folder, or exclude the publish folder from the project.</span></span> <span data-ttu-id="ddd32-168">Para excluir uma pasta de publicação chamada *publishoutput*, adicione o seguinte elemento a um `PropertyGroup` elemento no arquivo *. csproj* :</span><span class="sxs-lookup"><span data-stu-id="ddd32-168">To exclude a publish folder named *publishoutput*, add the following element to a `PropertyGroup` element in the *.csproj* file:</span></span>

  ```xml
  <DefaultItemExcludes>$(DefaultItemExcludes);publishoutput**</DefaultItemExcludes>
  ```

  - <span data-ttu-id="ddd32-169">SDK do .NET Core 3. x e posterior</span><span class="sxs-lookup"><span data-stu-id="ddd32-169">.NET Core 3.x SDK and later</span></span>
  
    <span data-ttu-id="ddd32-170">Se um caminho relativo for especificado durante a publicação de um projeto, o diretório de saída gerado será relativo ao diretório de trabalho atual, não ao local do arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="ddd32-170">If a relative path is specified when publishing a project, the output directory generated is relative to the current working directory, not to the project file location.</span></span>

    <span data-ttu-id="ddd32-171">Se um caminho relativo for especificado durante a publicação de uma solução, toda a saída de todos os projetos entrará na pasta especificada em relação ao diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="ddd32-171">If a relative path is specified when publishing a solution, all output for all projects goes into the specified folder relative to the current working directory.</span></span> <span data-ttu-id="ddd32-172">Para fazer com que a saída de publicação vá para pastas separadas para cada projeto, especifique um caminho relativo usando a `PublishDir` Propriedade MSBuild em vez da `--output` opção.</span><span class="sxs-lookup"><span data-stu-id="ddd32-172">To make publish output go to separate folders for each project, specify a relative path by using the msbuild `PublishDir` property instead of the `--output` option.</span></span> <span data-ttu-id="ddd32-173">Por exemplo, `dotnet publish -p:PublishDir=.\publish` envia a saída de publicação para cada projeto em uma `publish` pasta sob a pasta que contém o arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="ddd32-173">For example, `dotnet publish -p:PublishDir=.\publish` sends publish output for each project to a `publish` folder under the folder that contains the project file.</span></span>

  - <span data-ttu-id="ddd32-174">SDK do .NET Core 2. x</span><span class="sxs-lookup"><span data-stu-id="ddd32-174">.NET Core 2.x SDK</span></span>
  
    <span data-ttu-id="ddd32-175">Se um caminho relativo for especificado durante a publicação de um projeto, o diretório de saída gerado será relativo ao local do arquivo de projeto, não ao diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="ddd32-175">If a relative path is specified when publishing a project, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

    <span data-ttu-id="ddd32-176">Se um caminho relativo for especificado durante a publicação de uma solução, a saída de cada projeto entrará em uma pasta separada relativa ao local do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="ddd32-176">If a relative path is specified when publishing a solution, each project's output goes into a separate folder relative to the project file location.</span></span> <span data-ttu-id="ddd32-177">Se um caminho absoluto for especificado durante a publicação de uma solução, toda a saída de publicação de todos os projetos vai para a pasta especificada.</span><span class="sxs-lookup"><span data-stu-id="ddd32-177">If an absolute path is specified when publishing a solution, all publish output for all projects goes into the specified folder.</span></span>

- **`-p:PublishReadyToRun=true`**

  <span data-ttu-id="ddd32-178">Compila assemblies de aplicativo como o formato ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="ddd32-178">Compiles application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="ddd32-179">R2R é uma forma de compilação antecipada (AOT).</span><span class="sxs-lookup"><span data-stu-id="ddd32-179">R2R is a form of ahead-of-time (AOT) compilation.</span></span> <span data-ttu-id="ddd32-180">Para obter mais informações, consulte [ReadyToRun images](../whats-new/dotnet-core-3-0.md#readytorun-images).</span><span class="sxs-lookup"><span data-stu-id="ddd32-180">For more information, see [ReadyToRun images](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span> <span data-ttu-id="ddd32-181">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ddd32-181">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="ddd32-182">Recomendamos que você especifique essa opção em um perfil de publicação em vez de na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="ddd32-182">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="ddd32-183">Para mais informações, consulte [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="ddd32-183">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishSingleFile=true`**

  <span data-ttu-id="ddd32-184">Empacota o aplicativo em um executável de arquivo único específico da plataforma.</span><span class="sxs-lookup"><span data-stu-id="ddd32-184">Packages the app into a platform-specific single-file executable.</span></span> <span data-ttu-id="ddd32-185">O executável é de extração automática e contém todas as dependências (incluindo as nativas) que são necessárias para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="ddd32-185">The executable is self-extracting and contains all dependencies (including native) that are required to run the app.</span></span> <span data-ttu-id="ddd32-186">Quando o aplicativo é executado pela primeira vez, o aplicativo é extraído para um diretório com base no nome do aplicativo e no identificador do build.</span><span class="sxs-lookup"><span data-stu-id="ddd32-186">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="ddd32-187">A inicialização é mais rápida quando o aplicativo é executado novamente.</span><span class="sxs-lookup"><span data-stu-id="ddd32-187">Startup is faster when the application is run again.</span></span> <span data-ttu-id="ddd32-188">O aplicativo não precisa extrair a si mesmo uma segunda vez, a menos que uma nova versão seja usada.</span><span class="sxs-lookup"><span data-stu-id="ddd32-188">The application doesn't need to extract itself a second time unless a new version is used.</span></span> <span data-ttu-id="ddd32-189">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ddd32-189">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="ddd32-190">Para obter mais informações sobre a publicação de arquivo único, consulte o [documento de design de empacotador de arquivo único](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="ddd32-190">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span></span>

  <span data-ttu-id="ddd32-191">Recomendamos que você especifique essa opção em um perfil de publicação em vez de na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="ddd32-191">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="ddd32-192">Para mais informações, consulte [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="ddd32-192">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishTrimmed=true`**

  <span data-ttu-id="ddd32-193">Apara as bibliotecas não usadas para reduzir o tamanho da implantação de um aplicativo ao publicar um executável independente.</span><span class="sxs-lookup"><span data-stu-id="ddd32-193">Trims unused libraries to reduce the deployment size of an app when publishing a self-contained executable.</span></span> <span data-ttu-id="ddd32-194">Para obter mais informações, consulte [aparar implantações e executáveis independentes](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="ddd32-194">For more information, see [Trim self-contained deployments and executables](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="ddd32-195">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ddd32-195">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="ddd32-196">Recomendamos que você especifique essa opção em um perfil de publicação em vez de na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="ddd32-196">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="ddd32-197">Para mais informações, consulte [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="ddd32-197">For more information, see [MSBuild](#msbuild).</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="ddd32-198">Publica o runtime do .NET Core com seu aplicativo para que não seja necessário instalar o runtime no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="ddd32-198">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="ddd32-199">O padrão é `true` se um identificador de tempo de execução for especificado e o projeto for um projeto executável (não um projeto de biblioteca).</span><span class="sxs-lookup"><span data-stu-id="ddd32-199">Default is `true` if a runtime identifier is specified and the project is an executable project (not a library project).</span></span> <span data-ttu-id="ddd32-200">Para obter mais informações, consulte [publicação de aplicativos do .NET Core](../deploying/index.md) e [publicar aplicativos .net core com o CLI do .NET Core](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="ddd32-200">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

  <span data-ttu-id="ddd32-201">Se essa opção for usada sem especificar `true` ou `false` , o padrão será `true` .</span><span class="sxs-lookup"><span data-stu-id="ddd32-201">If this option is used without specifying `true` or `false`, the default is `true`.</span></span> <span data-ttu-id="ddd32-202">Nesse caso, não coloque a solução ou o argumento do projeto imediatamente após `--self-contained` , porque `true` ou `false` é esperado nessa posição.</span><span class="sxs-lookup"><span data-stu-id="ddd32-202">In that case, don't put the solution or project argument immediately after `--self-contained`, because `true` or `false` is expected in that position.</span></span>

- **`--no-self-contained`**

  <span data-ttu-id="ddd32-203">Equivalente a `--self-contained false`.</span><span class="sxs-lookup"><span data-stu-id="ddd32-203">Equivalent to `--self-contained false`.</span></span> <span data-ttu-id="ddd32-204">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="ddd32-204">Available since .NET Core 3.0 SDK.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="ddd32-205">Publica o aplicativo para um determinado runtime.</span><span class="sxs-lookup"><span data-stu-id="ddd32-205">Publishes the application for a given runtime.</span></span> <span data-ttu-id="ddd32-206">Para obter uma lista de RIDs (Identificadores de Runtime), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="ddd32-206">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="ddd32-207">Para obter mais informações, consulte [publicação de aplicativos do .NET Core](../deploying/index.md) e [publicar aplicativos .net core com o CLI do .NET Core](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="ddd32-207">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="ddd32-208">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="ddd32-208">Sets the verbosity level of the command.</span></span> <span data-ttu-id="ddd32-209">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="ddd32-209">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="ddd32-210">O valor padrão é `minimal`.</span><span class="sxs-lookup"><span data-stu-id="ddd32-210">Default value is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="ddd32-211">Define o sufixo da versão para substituir o asterisco (`*`) no campo de versão do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="ddd32-211">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="ddd32-212">Exemplos</span><span class="sxs-lookup"><span data-stu-id="ddd32-212">Examples</span></span>

- <span data-ttu-id="ddd32-213">Crie um [binário de plataforma cruzada dependente de tempo de execução](../deploying/index.md#produce-a-cross-platform-binary) para o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="ddd32-213">Create a [runtime-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="ddd32-214">A partir do SDK do .NET Core 3,0, este exemplo também cria um [executável dependente de tempo de execução](../deploying/index.md#publish-runtime-dependent) para a plataforma atual.</span><span class="sxs-lookup"><span data-stu-id="ddd32-214">Starting with .NET Core 3.0 SDK, this example also creates a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the current platform.</span></span>

- <span data-ttu-id="ddd32-215">Crie um [executável independente](../deploying/index.md#publish-self-contained) para o projeto no diretório atual, para um tempo de execução específico:</span><span class="sxs-lookup"><span data-stu-id="ddd32-215">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="ddd32-216">O RID deve estar no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="ddd32-216">The RID must be in the project file.</span></span>

- <span data-ttu-id="ddd32-217">Crie um [executável dependente de tempo de execução](../deploying/index.md#publish-runtime-dependent) para o projeto no diretório atual, para uma plataforma específica:</span><span class="sxs-lookup"><span data-stu-id="ddd32-217">Create a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="ddd32-218">O RID deve estar no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="ddd32-218">The RID must be in the project file.</span></span> <span data-ttu-id="ddd32-219">Este exemplo se aplica ao SDK do .NET Core 3,0 e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="ddd32-219">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="ddd32-220">Publicar o projeto no diretório atual, para um tempo de execução e estrutura de destino específicos:</span><span class="sxs-lookup"><span data-stu-id="ddd32-220">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="ddd32-221">Publicar o arquivo de projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="ddd32-221">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="ddd32-222">Publicar o aplicativo atual, mas não restaurar referências ponto a projeto (P2P), apenas o projeto raiz durante a operação de restauração:</span><span class="sxs-lookup"><span data-stu-id="ddd32-222">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="ddd32-223">Confira também</span><span class="sxs-lookup"><span data-stu-id="ddd32-223">See also</span></span>

- [<span data-ttu-id="ddd32-224">Visão geral da publicação de aplicativos do .NET Core</span><span class="sxs-lookup"><span data-stu-id="ddd32-224">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="ddd32-225">Publicar aplicativos .NET Core com o CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="ddd32-225">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="ddd32-226">Estruturas de destino</span><span class="sxs-lookup"><span data-stu-id="ddd32-226">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="ddd32-227">Catálogo de RID (identificador de tempo de execução)</span><span class="sxs-lookup"><span data-stu-id="ddd32-227">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="ddd32-228">Trabalhando com o notarization Catalina do macOS</span><span class="sxs-lookup"><span data-stu-id="ddd32-228">Working with macOS Catalina Notarization</span></span>](../install/macos-notarization-issues.md)
- [<span data-ttu-id="ddd32-229">Estrutura de diretórios de um aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="ddd32-229">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
- [<span data-ttu-id="ddd32-230">Referência de linha de comando do MSBuild</span><span class="sxs-lookup"><span data-stu-id="ddd32-230">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="ddd32-231">Perfis de publicação do Visual Studio (. pubxml) para implantação de aplicativo ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ddd32-231">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="ddd32-232">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="ddd32-232">dotnet msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="ddd32-233">ILLInk. Tasks</span><span class="sxs-lookup"><span data-stu-id="ddd32-233">ILLInk.Tasks</span></span>](https://aka.ms/dotnet-illink)
