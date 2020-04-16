---
title: Comando dotnet publish
description: O comando dotnet publish publica um projeto ou solução .NET Core para um diretório.
ms.date: 02/24/2020
ms.openlocfilehash: ca6b6bd0151674a81e0beee7798dc6bde9c088f0
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463465"
---
# <a name="dotnet-publish"></a><span data-ttu-id="567c4-103">dotnet publish</span><span class="sxs-lookup"><span data-stu-id="567c4-103">dotnet publish</span></span>

<span data-ttu-id="567c4-104">**Este artigo se aplica a:** ✔️ .NET Core 2.1 SDK e versões posteriores</span><span class="sxs-lookup"><span data-stu-id="567c4-104">**This article applies to:** ✔️ .NET Core 2.1 SDK and later versions</span></span>

## <a name="name"></a><span data-ttu-id="567c4-105">Nome</span><span class="sxs-lookup"><span data-stu-id="567c4-105">Name</span></span>

<span data-ttu-id="567c4-106">`dotnet publish`- Publica o aplicativo e suas dependências para uma pasta para implantação em um sistema de hospedagem.</span><span class="sxs-lookup"><span data-stu-id="567c4-106">`dotnet publish` - Publishes the application and its dependencies to a folder for deployment to a hosting system.</span></span>

## <a name="synopsis"></a><span data-ttu-id="567c4-107">Sinopse</span><span class="sxs-lookup"><span data-stu-id="567c4-107">Synopsis</span></span>

```dotnetcli
dotnet publish [<PROJECT>|<SOLUTION>] [-c|--configuration <CONFIGURATION>]
    [-f|--framework <FRAMEWORK>] [--force] [--interactive]
    [--manifest <PATH_TO_MANIFEST_FILE>] [--no-build] [--no-dependencies]
    [--no-restore] [--nologo] [-o|--output <OUTPUT_DIRECTORY>]
    [-p:PublishReadyToRun] [-p:PublishSingleFile] [-p:PublishTrimmed]
    [-r|--runtime <RUNTIME_IDENTIFIER>] [--self-contained [true|false]]
    [--no-self-contained] [-v|--verbosity <LEVEL>]
    [--version-suffix <VERSION_SUFFIX>]

dotnet publish -h|--help
```

## <a name="description"></a><span data-ttu-id="567c4-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="567c4-108">Description</span></span>

<span data-ttu-id="567c4-109">`dotnet publish` compila o aplicativo, lê suas dependências especificadas no arquivo de projeto e publica o conjunto de arquivos resultantes em um diretório.</span><span class="sxs-lookup"><span data-stu-id="567c4-109">`dotnet publish` compiles the application, reads through its dependencies specified in the project file, and publishes the resulting set of files to a directory.</span></span> <span data-ttu-id="567c4-110">A saída inclui os seguintes ativos:</span><span class="sxs-lookup"><span data-stu-id="567c4-110">The output includes the following assets:</span></span>

- <span data-ttu-id="567c4-111">Código IL (Linguagem Intermediária) em um assembly com uma extensão *dll*.</span><span class="sxs-lookup"><span data-stu-id="567c4-111">Intermediate Language (IL) code in an assembly with a *dll* extension.</span></span>
- <span data-ttu-id="567c4-112">Um arquivo *.deps.json* que inclui todas as dependências do projeto.</span><span class="sxs-lookup"><span data-stu-id="567c4-112">A *.deps.json* file that includes all of the dependencies of the project.</span></span>
- <span data-ttu-id="567c4-113">Um arquivo *.runtimeconfig.json* que especifica o tempo de execução compartilhado que o aplicativo espera, bem como outras opções de configuração para o tempo de execução (por exemplo, tipo de coleta de lixo).</span><span class="sxs-lookup"><span data-stu-id="567c4-113">A *.runtimeconfig.json* file that specifies the shared runtime that the application expects, as well as other configuration options for the runtime (for example, garbage collection type).</span></span>
- <span data-ttu-id="567c4-114">As dependências do aplicativo, que são copiadas do cache NuGet para a pasta de saída.</span><span class="sxs-lookup"><span data-stu-id="567c4-114">The application's dependencies, which are copied from the NuGet cache into the output folder.</span></span>

<span data-ttu-id="567c4-115">A saída do comando `dotnet publish` está pronta para implantação em um sistema de hospedagem (por exemplo, um servidor, um computador, um Mac, um laptop) para execução.</span><span class="sxs-lookup"><span data-stu-id="567c4-115">The `dotnet publish` command's output is ready for deployment to a hosting system (for example, a server, PC, Mac, laptop) for execution.</span></span> <span data-ttu-id="567c4-116">É a única maneira com suporte oficial de preparar o aplicativo para implantação.</span><span class="sxs-lookup"><span data-stu-id="567c4-116">It's the only officially supported way to prepare the application for deployment.</span></span> <span data-ttu-id="567c4-117">Dependendo do tipo de implantação especificado pelo projeto, talvez o sistema de hospedagem não tenha o runtime compartilhado do .NET Core instalado.</span><span class="sxs-lookup"><span data-stu-id="567c4-117">Depending on the type of deployment that the project specifies, the hosting system may or may not have the .NET Core shared runtime installed on it.</span></span> <span data-ttu-id="567c4-118">Para obter mais informações, consulte [Publicar os aplicativos .NET Core com o .NET Core CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="567c4-118">For more information, see [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

### <a name="msbuild"></a><span data-ttu-id="567c4-119">MSBuild</span><span class="sxs-lookup"><span data-stu-id="567c4-119">MSBuild</span></span>

<span data-ttu-id="567c4-120">O comando `dotnet publish` chama MSBuild, que invoca o destino `Publish`.</span><span class="sxs-lookup"><span data-stu-id="567c4-120">The `dotnet publish` command calls MSBuild, which invokes the `Publish` target.</span></span> <span data-ttu-id="567c4-121">Quaisquer parâmetros passados para `dotnet publish` são passados para o MSBuild.</span><span class="sxs-lookup"><span data-stu-id="567c4-121">Any parameters passed to `dotnet publish` are passed to MSBuild.</span></span> <span data-ttu-id="567c4-122">Os parâmetros `-c` e `-o` mapeiam as propriedades `Configuration` e `OutputPath` do MSBuild, respectivamente.</span><span class="sxs-lookup"><span data-stu-id="567c4-122">The `-c` and `-o` parameters map to MSBuild's `Configuration` and `OutputPath` properties, respectively.</span></span>

<span data-ttu-id="567c4-123">O `dotnet publish` comando aceita opções de `-p` MSBuild, `-l` como para definir propriedades e definir um logger.</span><span class="sxs-lookup"><span data-stu-id="567c4-123">The `dotnet publish` command accepts MSBuild options, such as `-p` for setting properties and `-l` to define a logger.</span></span> <span data-ttu-id="567c4-124">Por exemplo, você pode definir uma propriedade MSBuild usando o formato: `-p:<NAME>=<VALUE>`.</span><span class="sxs-lookup"><span data-stu-id="567c4-124">For example, you can set an MSBuild property by using the format: `-p:<NAME>=<VALUE>`.</span></span> <span data-ttu-id="567c4-125">Você também pode definir propriedades relacionadas à publicação referindo-se a um arquivo *.pubxml,* por exemplo:</span><span class="sxs-lookup"><span data-stu-id="567c4-125">You can also set publish-related properties by referring to a *.pubxml* file, for example:</span></span>

```dotnetcli
dotnet publish -p:PublishProfile=Properties\PublishProfiles\FolderProfile.pubxml
```

<span data-ttu-id="567c4-126">Para saber mais, consulte os recursos a seguir:</span><span class="sxs-lookup"><span data-stu-id="567c4-126">For more information, see the following resources:</span></span>

- [<span data-ttu-id="567c4-127">Referência de linha de comando MSBuild</span><span class="sxs-lookup"><span data-stu-id="567c4-127">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="567c4-128">Visual Studio publica perfis (.pubxml) para implantação de aplicativos ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="567c4-128">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="567c4-129">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="567c4-129">dotnet msbuild</span></span>](dotnet-msbuild.md)

## <a name="arguments"></a><span data-ttu-id="567c4-130">Argumentos</span><span class="sxs-lookup"><span data-stu-id="567c4-130">Arguments</span></span>

- **`PROJECT|SOLUTION`**

  <span data-ttu-id="567c4-131">O projeto ou solução para publicar.</span><span class="sxs-lookup"><span data-stu-id="567c4-131">The project or solution to publish.</span></span>
  
  * <span data-ttu-id="567c4-132">`PROJECT`é o caminho e o nome de arquivo de um arquivo de projeto [C#,](csproj.md)F#ou Visual Basic, ou o caminho para um diretório que contém um arquivo de projeto C#, F#ou Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="567c4-132">`PROJECT` is the path and filename of a [C#](csproj.md), F#, or Visual Basic project file, or the path to a directory that contains a C#, F#, or Visual Basic project file.</span></span> <span data-ttu-id="567c4-133">Se o diretório não for especificado, ele será padrão para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="567c4-133">If the directory is not specified, it defaults to the current directory.</span></span>

  * <span data-ttu-id="567c4-134">`SOLUTION`é o caminho e o nome de arquivo de um arquivo de solução (extensão *.sln)* ou o caminho para um diretório que contém um arquivo de solução.</span><span class="sxs-lookup"><span data-stu-id="567c4-134">`SOLUTION` is the path and filename of a solution file (*.sln* extension), or the path to a directory that contains a solution file.</span></span> <span data-ttu-id="567c4-135">Se o diretório não for especificado, ele será padrão para o diretório atual.</span><span class="sxs-lookup"><span data-stu-id="567c4-135">If the directory is not specified, it defaults to the current directory.</span></span> <span data-ttu-id="567c4-136">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="567c4-136">Available since .NET Core 3.0 SDK.</span></span>

## <a name="options"></a><span data-ttu-id="567c4-137">Opções</span><span class="sxs-lookup"><span data-stu-id="567c4-137">Options</span></span>

- **`-c|--configuration <CONFIGURATION>`**

  <span data-ttu-id="567c4-138">Define a configuração da compilação.</span><span class="sxs-lookup"><span data-stu-id="567c4-138">Defines the build configuration.</span></span> <span data-ttu-id="567c4-139">O padrão para `Debug`a maioria dos projetos é, mas você pode substituir as configurações de configuração de compilação em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="567c4-139">The default for most projects is `Debug`, but you can override the build configuration settings in your project.</span></span>

- **`-f|--framework <FRAMEWORK>`**

  <span data-ttu-id="567c4-140">Publica o aplicativo para a [estrutura de destino](../../standard/frameworks.md) especificada.</span><span class="sxs-lookup"><span data-stu-id="567c4-140">Publishes the application for the specified [target framework](../../standard/frameworks.md).</span></span> <span data-ttu-id="567c4-141">Especifique a estrutura de destino no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="567c4-141">You must specify the target framework in the project file.</span></span>

- **`--force`**

  <span data-ttu-id="567c4-142">Forçará todas as dependências a serem resolvidas mesmo se última restauração tiver sido bem-sucedida.</span><span class="sxs-lookup"><span data-stu-id="567c4-142">Forces all dependencies to be resolved even if the last restore was successful.</span></span> <span data-ttu-id="567c4-143">A especificação desse sinalizador é o mesmo que a exclusão do arquivo *project.assets.json*.</span><span class="sxs-lookup"><span data-stu-id="567c4-143">Specifying this flag is the same as deleting the *project.assets.json* file.</span></span>

- **`-h|--help`**

  <span data-ttu-id="567c4-144">Imprime uma ajuda breve para o comando.</span><span class="sxs-lookup"><span data-stu-id="567c4-144">Prints out a short help for the command.</span></span>

- **`--interactive`**

  <span data-ttu-id="567c4-145">Permite que o comando pare e aguarde entrada ou ação do usuário.</span><span class="sxs-lookup"><span data-stu-id="567c4-145">Allows the command to stop and wait for user input or action.</span></span> <span data-ttu-id="567c4-146">Por exemplo, para concluir a autenticação.</span><span class="sxs-lookup"><span data-stu-id="567c4-146">For example, to complete authentication.</span></span> <span data-ttu-id="567c4-147">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="567c4-147">Available since .NET Core 3.0 SDK.</span></span>

- **`--manifest <PATH_TO_MANIFEST_FILE>`**

  <span data-ttu-id="567c4-148">Especifica um ou vários [manifestos de destino](../deploying/runtime-store.md) a serem usados para cortar o conjunto de pacotes publicados com o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="567c4-148">Specifies one or several [target manifests](../deploying/runtime-store.md) to use to trim the set of packages published with the app.</span></span> <span data-ttu-id="567c4-149">O arquivo manifesto faz parte [ `dotnet store` ](dotnet-store.md)da saída do comando .</span><span class="sxs-lookup"><span data-stu-id="567c4-149">The manifest file is part of the output of the [`dotnet store` command](dotnet-store.md).</span></span> <span data-ttu-id="567c4-150">Para especificar vários manifestos, adicione uma opção `--manifest` para cada manifesto.</span><span class="sxs-lookup"><span data-stu-id="567c4-150">To specify multiple manifests, add a `--manifest` option for each manifest.</span></span>

- **`--no-build`**

  <span data-ttu-id="567c4-151">Não compila o projeto antes da publicação.</span><span class="sxs-lookup"><span data-stu-id="567c4-151">Doesn't build the project before publishing.</span></span> <span data-ttu-id="567c4-152">Também define o sinalizador `--no-restore` implicitamente.</span><span class="sxs-lookup"><span data-stu-id="567c4-152">It also implicitly sets the `--no-restore` flag.</span></span>

- **`--no-dependencies`**

  <span data-ttu-id="567c4-153">Ignora as referências projeto a projeto e só restaura o projeto raiz.</span><span class="sxs-lookup"><span data-stu-id="567c4-153">Ignores project-to-project references and only restores the root project.</span></span>

- **`--nologo`**

  <span data-ttu-id="567c4-154">Não exibe a faixa de inicialização nem a mensagem de direitos autorais.</span><span class="sxs-lookup"><span data-stu-id="567c4-154">Doesn't display the startup banner or the copyright message.</span></span> <span data-ttu-id="567c4-155">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="567c4-155">Available since .NET Core 3.0 SDK.</span></span>

- **`--no-restore`**

  <span data-ttu-id="567c4-156">Não executa uma restauração implícita ao executar o comando.</span><span class="sxs-lookup"><span data-stu-id="567c4-156">Doesn't execute an implicit restore when running the command.</span></span>

- **`-o|--output <OUTPUT_DIRECTORY>`**

  <span data-ttu-id="567c4-157">Especifica o caminho para o diretório de saída.</span><span class="sxs-lookup"><span data-stu-id="567c4-157">Specifies the path for the output directory.</span></span>
  
  <span data-ttu-id="567c4-158">Se não especificado, ele é padrão para *[project_file_folder]./bin/[configuração]/[framework]/publish/* para binários executáveis e multiplataformas dependentes de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="567c4-158">If not specified, it defaults to *[project_file_folder]./bin/[configuration]/[framework]/publish/* for a runtime-dependent executable and cross-platform binaries.</span></span> <span data-ttu-id="567c4-159">Ele é padrão para *[project_file_folder]/bin/[configuração]/[framework]/[runtime]/publish/* para um executável independente.</span><span class="sxs-lookup"><span data-stu-id="567c4-159">It defaults to *[project_file_folder]/bin/[configuration]/[framework]/[runtime]/publish/* for a self-contained executable.</span></span>

  <span data-ttu-id="567c4-160">Em um projeto web, se a pasta de `dotnet publish` saída estiver na pasta do projeto, comandos sucessivos resultarão em pastas de saída aninhadas.</span><span class="sxs-lookup"><span data-stu-id="567c4-160">In a web project, if the output folder is in the project folder, successive `dotnet publish` commands result in nested output folders.</span></span> <span data-ttu-id="567c4-161">Por exemplo, se a pasta do projeto for *myproject*, e a `dotnet publish` pasta de saída publicar for *myproject/publish*, e você for executado duas vezes, a segunda execução coloca arquivos de conteúdo como *arquivos .config* e *.json* no *myproject/publish/publish*.</span><span class="sxs-lookup"><span data-stu-id="567c4-161">For example, if the project folder is *myproject*, and the publish output folder is *myproject/publish*, and you run `dotnet publish` twice, the second run puts content files such as *.config* and *.json* files in *myproject/publish/publish*.</span></span> <span data-ttu-id="567c4-162">Para evitar o ninho de pastas de publicação, especifique uma pasta de publicação que não esteja diretamente sob a pasta do projeto ou exclua a pasta de publicação do projeto.</span><span class="sxs-lookup"><span data-stu-id="567c4-162">To avoid nesting publish folders, specify a publish folder that is not directly under the project folder, or exclude the publish folder from the project.</span></span> <span data-ttu-id="567c4-163">Para excluir uma pasta de publicação chamada *publishoutput*, adicione o seguinte elemento a um `PropertyGroup` elemento no arquivo *.csproj:*</span><span class="sxs-lookup"><span data-stu-id="567c4-163">To exclude a publish folder named *publishoutput*, add the following element to a `PropertyGroup` element in the *.csproj* file:</span></span>

  ```xml
  <DefaultItemExcludes>$(DefaultItemExcludes);publishoutput**</DefaultItemExcludes>
  ```

  - <span data-ttu-id="567c4-164">.NET Core 3.x SDK e posterior</span><span class="sxs-lookup"><span data-stu-id="567c4-164">.NET Core 3.x SDK and later</span></span>
  
    <span data-ttu-id="567c4-165">Se um caminho relativo for especificado ao publicar um projeto, o diretório de saída gerado será relativo ao diretório de trabalho atual, não à localização do arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="567c4-165">If a relative path is specified when publishing a project, the output directory generated is relative to the current working directory, not to the project file location.</span></span>

    <span data-ttu-id="567c4-166">Se um caminho relativo for especificado ao publicar uma solução, toda a saída para todos os projetos entrará na pasta especificada em relação ao diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="567c4-166">If a relative path is specified when publishing a solution, all output for all projects go into the specified folder relative to the current working directory.</span></span> <span data-ttu-id="567c4-167">Para fazer a saída de publicação ir para pastas separadas para `PublishDir` cada projeto, especifique um caminho relativo usando a propriedade msbuild em vez da `--output` opção.</span><span class="sxs-lookup"><span data-stu-id="567c4-167">To make publish output go to separate folders for each project, specify a relative path by using the msbuild `PublishDir` property instead of the `--output` option.</span></span> <span data-ttu-id="567c4-168">Por exemplo, `dotnet publish -p:PublishDir=.\publish` envia a saída `publish` de publicação de cada projeto para uma pasta sob a pasta que contém o arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="567c4-168">For example, `dotnet publish -p:PublishDir=.\publish` sends publish output for each project to a `publish` folder under the folder that contains the project file.</span></span>

  - <span data-ttu-id="567c4-169">.NET Core 2.x SDK</span><span class="sxs-lookup"><span data-stu-id="567c4-169">.NET Core 2.x SDK</span></span>
  
    <span data-ttu-id="567c4-170">Se um caminho relativo for especificado ao publicar um projeto, o diretório de saída gerado será relativo à localização do arquivo do projeto, não ao diretório de trabalho atual.</span><span class="sxs-lookup"><span data-stu-id="567c4-170">If a relative path is specified when publishing a project, the output directory generated is relative to the project file location, not to the current working directory.</span></span>

    <span data-ttu-id="567c4-171">Se um caminho relativo for especificado ao publicar uma solução, a saída de cada projeto será colocada em uma pasta separada em relação ao local do arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="567c4-171">If a relative path is specified when publishing a solution, each project's output goes into a separate folder relative to the project file location.</span></span> <span data-ttu-id="567c4-172">Se um caminho absoluto for especificado ao publicar uma solução, todas as saídas de publicação para todos os projetos serão colocadas na pasta especificada.</span><span class="sxs-lookup"><span data-stu-id="567c4-172">If an absolute path is specified when publishing a solution, all publish output for all projects goes into the specified folder.</span></span>

- **`-p:PublishReadyToRun`**

  <span data-ttu-id="567c4-173">Compila conjuntos de aplicativos como formato ReadyToRun (R2R).</span><span class="sxs-lookup"><span data-stu-id="567c4-173">Compiles application assemblies as ReadyToRun (R2R) format.</span></span> <span data-ttu-id="567c4-174">R2R é uma forma de compilação antecipada (AOT).</span><span class="sxs-lookup"><span data-stu-id="567c4-174">R2R is a form of ahead-of-time (AOT) compilation.</span></span> <span data-ttu-id="567c4-175">Para obter mais informações, consulte [imagens ReadyToRun](../whats-new/dotnet-core-3-0.md#readytorun-images).</span><span class="sxs-lookup"><span data-stu-id="567c4-175">For more information, see [ReadyToRun images](../whats-new/dotnet-core-3-0.md#readytorun-images).</span></span> <span data-ttu-id="567c4-176">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="567c4-176">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="567c4-177">Recomendamos que você especifique esta opção em um perfil de publicação em vez de na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="567c4-177">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="567c4-178">Para mais informações, consulte [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="567c4-178">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishSingleFile`**

  <span data-ttu-id="567c4-179">Empacota o aplicativo em um executável de arquivo único específico da plataforma.</span><span class="sxs-lookup"><span data-stu-id="567c4-179">Packages the app into a platform-specific single-file executable.</span></span> <span data-ttu-id="567c4-180">O executável é auto-extraindo e contém todas as dependências (incluindo nativas) que são necessárias para executar o aplicativo.</span><span class="sxs-lookup"><span data-stu-id="567c4-180">The executable is self-extracting and contains all dependencies (including native) that are required to run the app.</span></span> <span data-ttu-id="567c4-181">Quando o aplicativo é executado pela primeira vez, o aplicativo é extraído para um diretório com base no nome do aplicativo e no identificador do build.</span><span class="sxs-lookup"><span data-stu-id="567c4-181">When the app is first run, the application is extracted to a directory based on the app name and build identifier.</span></span> <span data-ttu-id="567c4-182">A inicialização é mais rápida quando o aplicativo é executado novamente.</span><span class="sxs-lookup"><span data-stu-id="567c4-182">Startup is faster when the application is run again.</span></span> <span data-ttu-id="567c4-183">O aplicativo não precisa se extrair uma segunda vez, a menos que uma nova versão seja usada.</span><span class="sxs-lookup"><span data-stu-id="567c4-183">The application doesn't need to extract itself a second time unless a new version is used.</span></span> <span data-ttu-id="567c4-184">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="567c4-184">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="567c4-185">Para obter mais informações sobre a publicação de arquivo único, consulte o [documento de design de empacotador de arquivo único](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span><span class="sxs-lookup"><span data-stu-id="567c4-185">For more information about single-file publishing, see the [single-file bundler design document](https://github.com/dotnet/designs/blob/master/accepted/2020/single-file/design.md).</span></span>

  <span data-ttu-id="567c4-186">Recomendamos que você especifique esta opção em um perfil de publicação em vez de na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="567c4-186">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="567c4-187">Para mais informações, consulte [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="567c4-187">For more information, see [MSBuild](#msbuild).</span></span>

- **`-p:PublishTrimmed`**

  <span data-ttu-id="567c4-188">Apara bibliotecas não utilizadas para reduzir o tamanho de implantação de um aplicativo ao publicar um executável independente.</span><span class="sxs-lookup"><span data-stu-id="567c4-188">Trims unused libraries to reduce the deployment size of an app when publishing a self-contained executable.</span></span> <span data-ttu-id="567c4-189">Para obter mais informações, consulte [Trim implantações e executáveis independentes](../deploying/trim-self-contained.md).</span><span class="sxs-lookup"><span data-stu-id="567c4-189">For more information, see [Trim self-contained deployments and executables](../deploying/trim-self-contained.md).</span></span> <span data-ttu-id="567c4-190">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="567c4-190">Available since .NET Core 3.0 SDK.</span></span>

  <span data-ttu-id="567c4-191">Recomendamos que você especifique esta opção em um perfil de publicação em vez de na linha de comando.</span><span class="sxs-lookup"><span data-stu-id="567c4-191">We recommend that you specify this option in a publish profile rather than on the command line.</span></span> <span data-ttu-id="567c4-192">Para mais informações, consulte [MSBuild](#msbuild).</span><span class="sxs-lookup"><span data-stu-id="567c4-192">For more information, see [MSBuild](#msbuild).</span></span>

- **`--self-contained [true|false]`**

  <span data-ttu-id="567c4-193">Publica o runtime do .NET Core com seu aplicativo para que não seja necessário instalar o runtime no computador de destino.</span><span class="sxs-lookup"><span data-stu-id="567c4-193">Publishes the .NET Core runtime with your application so the runtime doesn't need to be installed on the target machine.</span></span> <span data-ttu-id="567c4-194">O `true` padrão é se um identificador de tempo de execução for especificado e o projeto for um projeto executável (não um projeto de biblioteca).</span><span class="sxs-lookup"><span data-stu-id="567c4-194">Default is `true` if a runtime identifier is specified and the project is an executable project (not a library project).</span></span> <span data-ttu-id="567c4-195">Para obter mais informações, consulte [a publicação do aplicativo .NET Core](../deploying/index.md) e publique os aplicativos [.NET Core com o .NET Core CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="567c4-195">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

  <span data-ttu-id="567c4-196">Se essa opção for `true` usada `false`sem `true`especificar ou, o padrão será .</span><span class="sxs-lookup"><span data-stu-id="567c4-196">If this option is used without specifying `true` or `false`, the default is `true`.</span></span> <span data-ttu-id="567c4-197">Nesse caso, não coloque a solução ou o `--self-contained`argumento `true` `false` do projeto imediatamente depois, porque ou é esperado nessa posição.</span><span class="sxs-lookup"><span data-stu-id="567c4-197">In that case, don't put the solution or project argument immediately after `--self-contained`, because `true` or `false` is expected in that position.</span></span>

- **`--no-self-contained`**

  <span data-ttu-id="567c4-198">Equivalente a `--self-contained false`.</span><span class="sxs-lookup"><span data-stu-id="567c4-198">Equivalent to `--self-contained false`.</span></span> <span data-ttu-id="567c4-199">Disponível desde o SDK do .NET Core 3.0.</span><span class="sxs-lookup"><span data-stu-id="567c4-199">Available since .NET Core 3.0 SDK.</span></span>

- **`-r|--runtime <RUNTIME_IDENTIFIER>`**

  <span data-ttu-id="567c4-200">Publica o aplicativo para um determinado runtime.</span><span class="sxs-lookup"><span data-stu-id="567c4-200">Publishes the application for a given runtime.</span></span> <span data-ttu-id="567c4-201">Para obter uma lista de RIDs (Identificadores de Runtime), veja o [Catálogo de RIDs](../rid-catalog.md).</span><span class="sxs-lookup"><span data-stu-id="567c4-201">For a list of Runtime Identifiers (RIDs), see the [RID catalog](../rid-catalog.md).</span></span> <span data-ttu-id="567c4-202">Para obter mais informações, consulte [a publicação do aplicativo .NET Core](../deploying/index.md) e publique os aplicativos [.NET Core com o .NET Core CLI](../deploying/deploy-with-cli.md).</span><span class="sxs-lookup"><span data-stu-id="567c4-202">For more information, see [.NET Core application publishing](../deploying/index.md) and [Publish .NET Core apps with the .NET Core CLI](../deploying/deploy-with-cli.md).</span></span>

- **`-v|--verbosity <LEVEL>`**

  <span data-ttu-id="567c4-203">Define o nível de detalhes do comando.</span><span class="sxs-lookup"><span data-stu-id="567c4-203">Sets the verbosity level of the command.</span></span> <span data-ttu-id="567c4-204">Os valores permitidos são `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]` e `diag[nostic]`.</span><span class="sxs-lookup"><span data-stu-id="567c4-204">Allowed values are `q[uiet]`, `m[inimal]`, `n[ormal]`, `d[etailed]`, and `diag[nostic]`.</span></span> <span data-ttu-id="567c4-205">O valor padrão é `minimal`.</span><span class="sxs-lookup"><span data-stu-id="567c4-205">Default value is `minimal`.</span></span>

- **`--version-suffix <VERSION_SUFFIX>`**

  <span data-ttu-id="567c4-206">Define o sufixo da versão para substituir o asterisco (`*`) no campo de versão do arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="567c4-206">Defines the version suffix to replace the asterisk (`*`) in the version field of the project file.</span></span>

## <a name="examples"></a><span data-ttu-id="567c4-207">Exemplos</span><span class="sxs-lookup"><span data-stu-id="567c4-207">Examples</span></span>

- <span data-ttu-id="567c4-208">Crie um [binário multiplataforma dependente de tempo de execução](../deploying/index.md#produce-a-cross-platform-binary) para o projeto no diretório atual:</span><span class="sxs-lookup"><span data-stu-id="567c4-208">Create a [runtime-dependent cross-platform binary](../deploying/index.md#produce-a-cross-platform-binary) for the project in the current directory:</span></span>

  ```dotnetcli
  dotnet publish
  ```

  <span data-ttu-id="567c4-209">Começando com o .NET Core 3.0 SDK, este exemplo também cria um [executável dependente de tempo de execução](../deploying/index.md#publish-runtime-dependent) para a plataforma atual.</span><span class="sxs-lookup"><span data-stu-id="567c4-209">Starting with .NET Core 3.0 SDK, this example also creates a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the current platform.</span></span>

- <span data-ttu-id="567c4-210">Crie um [executável independente](../deploying/index.md#publish-self-contained) para o projeto no diretório atual, por um tempo de execução específico:</span><span class="sxs-lookup"><span data-stu-id="567c4-210">Create a [self-contained executable](../deploying/index.md#publish-self-contained) for the project in the current directory, for a specific runtime:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64
  ```

  <span data-ttu-id="567c4-211">O RID deve estar no arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="567c4-211">The RID must be in the project file.</span></span>

- <span data-ttu-id="567c4-212">Crie um [executável dependente de tempo de execução](../deploying/index.md#publish-runtime-dependent) para o projeto no diretório atual, para uma plataforma específica:</span><span class="sxs-lookup"><span data-stu-id="567c4-212">Create a [runtime-dependent executable](../deploying/index.md#publish-runtime-dependent) for the project in the current directory, for a specific platform:</span></span>

  ```dotnetcli
  dotnet publish --runtime osx.10.11-x64 --self-contained false
  ```

  <span data-ttu-id="567c4-213">O RID deve estar no arquivo do projeto.</span><span class="sxs-lookup"><span data-stu-id="567c4-213">The RID must be in the project file.</span></span> <span data-ttu-id="567c4-214">Este exemplo se aplica ao .NET Core 3.0 SDK e versões posteriores.</span><span class="sxs-lookup"><span data-stu-id="567c4-214">This example applies to .NET Core 3.0 SDK and later versions.</span></span>

- <span data-ttu-id="567c4-215">Publique o projeto no diretório atual, para obter um tempo de execução específico e uma estrutura de destino:</span><span class="sxs-lookup"><span data-stu-id="567c4-215">Publish the project in the current directory, for a specific runtime and target framework:</span></span>

  ```dotnetcli
  dotnet publish --framework netcoreapp3.1 --runtime osx.10.11-x64
  ```

- <span data-ttu-id="567c4-216">Publicar o arquivo de projeto especificado:</span><span class="sxs-lookup"><span data-stu-id="567c4-216">Publish the specified project file:</span></span>

  ```dotnetcli
  dotnet publish ~/projects/app1/app1.csproj
  ```

- <span data-ttu-id="567c4-217">Publique o aplicativo atual, mas não restaure as referências p2P (project-to-project), apenas o projeto raiz durante a operação de restauração:</span><span class="sxs-lookup"><span data-stu-id="567c4-217">Publish the current application but don't restore project-to-project (P2P) references, just the root project during the restore operation:</span></span>

  ```dotnetcli
  dotnet publish --no-dependencies
  ```

## <a name="see-also"></a><span data-ttu-id="567c4-218">Confira também</span><span class="sxs-lookup"><span data-stu-id="567c4-218">See also</span></span>

- [<span data-ttu-id="567c4-219">Visão geral da publicação de aplicativos .NET Core</span><span class="sxs-lookup"><span data-stu-id="567c4-219">.NET Core application publishing overview</span></span>](../deploying/index.md)
- [<span data-ttu-id="567c4-220">Publique os aplicativos .NET Core com o .NET Core CLI</span><span class="sxs-lookup"><span data-stu-id="567c4-220">Publish .NET Core apps with the .NET Core CLI</span></span>](../deploying/deploy-with-cli.md)
- [<span data-ttu-id="567c4-221">Frameworks de destino</span><span class="sxs-lookup"><span data-stu-id="567c4-221">Target frameworks</span></span>](../../standard/frameworks.md)
- [<span data-ttu-id="567c4-222">Catálogo de identificadores de execução (RID)</span><span class="sxs-lookup"><span data-stu-id="567c4-222">Runtime IDentifier (RID) catalog</span></span>](../rid-catalog.md)
- [<span data-ttu-id="567c4-223">Trabalhando com nota nota notardo pelo macOS Catalina</span><span class="sxs-lookup"><span data-stu-id="567c4-223">Working with macOS Catalina Notarization</span></span>](../install/macos-notarization-issues.md)
- [<span data-ttu-id="567c4-224">Estrutura do diretório de um aplicativo publicado</span><span class="sxs-lookup"><span data-stu-id="567c4-224">Directory structure of a published application</span></span>](/aspnet/core/hosting/directory-structure)
- [<span data-ttu-id="567c4-225">Referência de linha de comando MSBuild</span><span class="sxs-lookup"><span data-stu-id="567c4-225">MSBuild command-line reference</span></span>](/visualstudio/msbuild/msbuild-command-line-reference)
- [<span data-ttu-id="567c4-226">Visual Studio publica perfis (.pubxml) para implantação de aplicativos ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="567c4-226">Visual Studio publish profiles (.pubxml) for ASP.NET Core app deployment</span></span>](/aspnet/core/host-and-deploy/visual-studio-publish-profiles)
- [<span data-ttu-id="567c4-227">dotnet msbuild</span><span class="sxs-lookup"><span data-stu-id="567c4-227">dotnet msbuild</span></span>](dotnet-msbuild.md)
- [<span data-ttu-id="567c4-228">ILLInk.Tarefas</span><span class="sxs-lookup"><span data-stu-id="567c4-228">ILLInk.Tasks</span></span>](https://aka.ms/dotnet-illink)
