---
title: Bibliotecas do NuGet e .NET
description: Recomendações de melhor prática para o empacotamento com o NuGet para bibliotecas do .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: 8ac01046f25176b781240baeba8bf1efb9376689
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129604"
---
# <a name="nuget"></a><span data-ttu-id="c9268-103">NuGet</span><span class="sxs-lookup"><span data-stu-id="c9268-103">NuGet</span></span>

<span data-ttu-id="c9268-104">O NuGet é um gerenciador de pacotes para o ecossistema do .NET e é a principal maneira como os desenvolvedores descobrem e adquirem bibliotecas de código-fonte aberto do .NET.</span><span class="sxs-lookup"><span data-stu-id="c9268-104">NuGet is a package manager for the .NET ecosystem and is the primary way developers discover and acquire .NET open-source libraries.</span></span> <span data-ttu-id="c9268-105">O [NuGet.org](https://www.nuget.org/), um serviço gratuito fornecido pela Microsoft para hospedar pacotes do NuGet, é o host primário para os pacotes públicos do NuGet, mas você pode publicar em serviços personalizados do NuGet, como [MyGet](https://www.myget.org/) e [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/).</span><span class="sxs-lookup"><span data-stu-id="c9268-105">[NuGet.org](https://www.nuget.org/), a free service provided by Microsoft for hosting NuGet packages, is the primary host for public NuGet packages, but you can publish to custom NuGet services like [MyGet](https://www.myget.org/) and [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/).</span></span>

<span data-ttu-id="c9268-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span><span class="sxs-lookup"><span data-stu-id="c9268-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="c9268-107">Criar um pacote NuGet</span><span class="sxs-lookup"><span data-stu-id="c9268-107">Create a NuGet package</span></span>

<span data-ttu-id="c9268-108">Um pacote do NuGet (`*.nupkg`) é um arquivo zip que contém os assemblies do .NET e os metadados associados.</span><span class="sxs-lookup"><span data-stu-id="c9268-108">A NuGet package (`*.nupkg`) is a zip file that contains .NET assemblies and associated metadata.</span></span>

<span data-ttu-id="c9268-109">Há duas maneiras principais de criar um pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="c9268-109">There are two main ways to create a NuGet package.</span></span> <span data-ttu-id="c9268-110">A maneira recomendada e mais recente é criar um pacote de um projeto no estilo do SDK (arquivo de projeto cujo conteúdo começa com `<Project Sdk="Microsoft.NET.Sdk">`).</span><span class="sxs-lookup"><span data-stu-id="c9268-110">The newer and recommended way is to create a package from a SDK-style project (project file whose content starts with `<Project Sdk="Microsoft.NET.Sdk">`).</span></span> <span data-ttu-id="c9268-111">Assemblies e destinos são automaticamente adicionados ao pacote e o restante dos metadados é adicionado ao arquivo MSBuild, como o número de versão e o nome do pacote.</span><span class="sxs-lookup"><span data-stu-id="c9268-111">Assemblies and targets are automatically added to the package and remaining metadata is added to the MSBuild file, like package name and version number.</span></span> <span data-ttu-id="c9268-112">Compilar com o comando [`dotnet pack`](../../core/tools/dotnet-pack.md) gera um arquivo `*.nupkg`, em vez de assemblies.</span><span class="sxs-lookup"><span data-stu-id="c9268-112">Compiling with the [`dotnet pack`](../../core/tools/dotnet-pack.md) command outputs a `*.nupkg` file instead of assemblies.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <TargetFramework>netstandard2.0</TargetFramework>
    <AssemblyName>Contoso.Api</AssemblyName>
    <PackageVersion>1.1.0</PackageVersion>
    <Authors>John Doe</Authors>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="c9268-113">A maneira mais antiga de criar um pacote do NuGet é com um arquivo `*.nuspec` e a ferramenta de linha de comando `nuget.exe`.</span><span class="sxs-lookup"><span data-stu-id="c9268-113">The older way of creating a NuGet package is with a `*.nuspec` file and the `nuget.exe` command-line tool.</span></span> <span data-ttu-id="c9268-114">Um arquivo nuspec dá excelente controle, mas você deve especificar com cuidado quais assemblies e destinos incluir no pacote final do NuGet.</span><span class="sxs-lookup"><span data-stu-id="c9268-114">A nuspec file gives you great control but you must carefully specify what assemblies and targets to include in the final NuGet package.</span></span> <span data-ttu-id="c9268-115">É fácil cometer um erro ou alguém se esquecer de atualizar o nuspec ao fazer alterações.</span><span class="sxs-lookup"><span data-stu-id="c9268-115">It's easy to make a mistake or for someone to forget to update the nuspec when making changes.</span></span> <span data-ttu-id="c9268-116">A vantagem de um nuspec é que você pode usá-lo criar pacotes do NuGet para estruturas que ainda não dão suporte a um arquivo de projeto de estilo do SDK.</span><span class="sxs-lookup"><span data-stu-id="c9268-116">The advantage of a nuspec is you can use it create NuGet packages for frameworks that don't yet support an SDK-style project file.</span></span>

<span data-ttu-id="c9268-117">**✔️ CONSIDERE** usar um arquivo de projeto no estilo SDK para criar o pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="c9268-117">**✔️ CONSIDER** using an SDK-style project file to create the NuGet package.</span></span>

## <a name="package-dependencies"></a><span data-ttu-id="c9268-118">Dependências do pacote</span><span class="sxs-lookup"><span data-stu-id="c9268-118">Package dependencies</span></span>

<span data-ttu-id="c9268-119">Dependências de pacotes NuGet são abordadas detalhadamente no artigo [Dependências](./dependencies.md).</span><span class="sxs-lookup"><span data-stu-id="c9268-119">NuGet package dependencies are covered in detail in the [Dependencies](./dependencies.md) article.</span></span>

## <a name="important-nuget-package-metadata"></a><span data-ttu-id="c9268-120">Metadados de pacote do NuGet importantes</span><span class="sxs-lookup"><span data-stu-id="c9268-120">Important NuGet package metadata</span></span>

<span data-ttu-id="c9268-121">Um pacote do NuGet dá suporte a muitas [propriedades de metadados](/nuget/reference/nuspec).</span><span class="sxs-lookup"><span data-stu-id="c9268-121">A NuGet package supports many [metadata properties](/nuget/reference/nuspec).</span></span> <span data-ttu-id="c9268-122">A tabela a seguir contém os principais metadados que cada projeto de software livre deve fornecer:</span><span class="sxs-lookup"><span data-stu-id="c9268-122">The following table contains the core metadata that every open-source project should provide:</span></span>

| <span data-ttu-id="c9268-123">Nome da Propriedade do MSBuild</span><span class="sxs-lookup"><span data-stu-id="c9268-123">MSBuild Property name</span></span>              | <span data-ttu-id="c9268-124">Nome Nuspec</span><span class="sxs-lookup"><span data-stu-id="c9268-124">Nuspec name</span></span>              | <span data-ttu-id="c9268-125">Descrição</span><span class="sxs-lookup"><span data-stu-id="c9268-125">Description</span></span>  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | <span data-ttu-id="c9268-126">O identificador do pacote.</span><span class="sxs-lookup"><span data-stu-id="c9268-126">The package identifier.</span></span> <span data-ttu-id="c9268-127">Um prefixo do identificador poderá ser reservado se ele cumprir os [critérios](/nuget/reference/id-prefix-reservation).</span><span class="sxs-lookup"><span data-stu-id="c9268-127">A prefix from the identifier can be reserved if it meets the [criteria](/nuget/reference/id-prefix-reservation).</span></span> |
| `PackageVersion`                   | `version`                  | <span data-ttu-id="c9268-128">Versão do pacote NuGet.</span><span class="sxs-lookup"><span data-stu-id="c9268-128">NuGet package version.</span></span> <span data-ttu-id="c9268-129">Para obter mais informações, veja [Controle de versão de pacote do NuGet](./versioning.md#nuget-package-version).</span><span class="sxs-lookup"><span data-stu-id="c9268-129">For more information, see [NuGet package version](./versioning.md#nuget-package-version).</span></span>             |
| `Title`                            | `title`                    | <span data-ttu-id="c9268-130">Um título amigável a humanos do pacote.</span><span class="sxs-lookup"><span data-stu-id="c9268-130">A human-friendly title of the package.</span></span> <span data-ttu-id="c9268-131">Usa como padrão `PackageId`.</span><span class="sxs-lookup"><span data-stu-id="c9268-131">It defaults to the `PackageId`.</span></span>             |
| `Description`                      | `description`              | <span data-ttu-id="c9268-132">Uma descrição longa do pacote exibida na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="c9268-132">A long description of the package displayed in UI.</span></span>             |
| `Authors`                          | `authors`                  | <span data-ttu-id="c9268-133">Uma lista separada por vírgulas de autores de pacote que correspondem aos nomes de perfil em nuget.org.</span><span class="sxs-lookup"><span data-stu-id="c9268-133">A comma-separated list of package authors, matching the profile names on nuget.org.</span></span>             |
| `PackageTags`                      | `tags`                     | <span data-ttu-id="c9268-134">Uma lista delimitada por espaço de marcas e palavras-chave que descrevem o pacote.</span><span class="sxs-lookup"><span data-stu-id="c9268-134">A space-delimited list of tags and keywords that describe the package.</span></span> <span data-ttu-id="c9268-135">Marcas são usadas ao pesquisar pacotes.</span><span class="sxs-lookup"><span data-stu-id="c9268-135">Tags are used when searching for packages.</span></span>             |
| `PackageIconUrl`                   | `iconUrl`                  | <span data-ttu-id="c9268-136">Uma URL para uma imagem a ser usada como o ícone para o pacote.</span><span class="sxs-lookup"><span data-stu-id="c9268-136">A URL for an image to use as the icon for the package.</span></span> <span data-ttu-id="c9268-137">A URL deve ser HTTPS e a imagem deve ser 64 x 64 e ter um segundo plano transparente.</span><span class="sxs-lookup"><span data-stu-id="c9268-137">URL should be HTTPS and the image should be 64x64 and have a transparent background.</span></span>             |
| `PackageProjectUrl`                | `projectUrl`               | <span data-ttu-id="c9268-138">Uma URL para o repositório de origem ou página inicial do projeto.</span><span class="sxs-lookup"><span data-stu-id="c9268-138">A URL for the project homepage or source repository.</span></span>             |
| `PackageLicenseUrl`                | `licenseUrl`               | <span data-ttu-id="c9268-139">Uma URL para a licença do projeto.</span><span class="sxs-lookup"><span data-stu-id="c9268-139">A URL to the project license.</span></span> <span data-ttu-id="c9268-140">Pode ser a URL para o arquivo `LICENSE` no controle do código-fonte.</span><span class="sxs-lookup"><span data-stu-id="c9268-140">Can be the URL to the `LICENSE` file in source control.</span></span>             |

<span data-ttu-id="c9268-141">**✔️ CONSIDERE** escolher um nome de pacote do NuGet com um prefixo que cumpra os [critérios](/nuget/reference/id-prefix-reservation) de reserva de prefixo do NuGet.</span><span class="sxs-lookup"><span data-stu-id="c9268-141">**✔️ CONSIDER** choosing a NuGet package name with a prefix that meets NuGet's prefix reservation [criteria](/nuget/reference/id-prefix-reservation).</span></span>

<span data-ttu-id="c9268-142">**✔️ CONSIDERE** usar o arquivo `LICENSE` no controle do código-fonte como o `LicenseUrl`.</span><span class="sxs-lookup"><span data-stu-id="c9268-142">**✔️ CONSIDER** using the `LICENSE` file in source control as the `LicenseUrl`.</span></span> <span data-ttu-id="c9268-143">Por exemplo, [LICENSE.md](https://github.com/JamesNK/Newtonsoft.Json/blob/c4af75c8e91ca0d75aa6c335e8c106780c4f7712/LICENSE.md).</span><span class="sxs-lookup"><span data-stu-id="c9268-143">For example, [LICENSE.md](https://github.com/JamesNK/Newtonsoft.Json/blob/c4af75c8e91ca0d75aa6c335e8c106780c4f7712/LICENSE.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c9268-144">Um projeto sem uma licença usa como padrão [direitos autorais exclusivo](https://choosealicense.com/no-permission/), tornando impossível que outras pessoas o usem.</span><span class="sxs-lookup"><span data-stu-id="c9268-144">A project without a license defaults to [exclusive copyright](https://choosealicense.com/no-permission/), making it impossible for other people to use.</span></span>

<span data-ttu-id="c9268-145">**✔️ FAÇA** uso de um href HTTPS com o ícone do pacote.</span><span class="sxs-lookup"><span data-stu-id="c9268-145">**✔️ DO** use an HTTPS href to your package icon.</span></span>

> <span data-ttu-id="c9268-146">Sites, como o NuGet.org são executados com HTTPS habilitado e exibir uma imagem não HTTPS criará um aviso de conteúdo misto.</span><span class="sxs-lookup"><span data-stu-id="c9268-146">Sites like NuGet.org run with HTTPS enabled and displaying a non-HTTPS image will create a mixed content warning.</span></span>

<span data-ttu-id="c9268-147">**✔️ FAÇA** uso de uma imagem de ícone do pacote de 64 x 64 e com um segundo plano transparente para melhor visualização dos resultados.</span><span class="sxs-lookup"><span data-stu-id="c9268-147">**✔️ DO** use a package icon image that is 64x64 and has a transparent background for best viewing results.</span></span>

<span data-ttu-id="c9268-148">**✔️ CONSIDERE** configurar o [SourceLink](./sourcelink.md) para adicionar metadados de controle do código-fonte aos seus assemblies e pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="c9268-148">**✔️ CONSIDER** setting up [SourceLink](./sourcelink.md) to add source control metadata to your assemblies and NuGet package.</span></span>

> <span data-ttu-id="c9268-149">O SourceLink adiciona automaticamente os metadados `RepositoryUrl` e `RepositoryType` ao pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="c9268-149">SourceLink automatically adds `RepositoryUrl` and `RepositoryType` metadata to the NuGet package.</span></span>
> <span data-ttu-id="c9268-150">O SourceLink também adiciona informações sobre o código-fonte exato do qual o pacote foi criado.</span><span class="sxs-lookup"><span data-stu-id="c9268-150">SourceLink also adds information about the exact source code the package was built from.</span></span>
> <span data-ttu-id="c9268-151">Por exemplo, um pacote criado de um repositório Git terá o hash de confirmação adicionado como metadados.</span><span class="sxs-lookup"><span data-stu-id="c9268-151">For example, a package created from a Git repository will have the commit hash added as metadata.</span></span>

## <a name="pre-release-packages"></a><span data-ttu-id="c9268-152">Pacotes de pré-lançamento</span><span class="sxs-lookup"><span data-stu-id="c9268-152">Pre-release packages</span></span>

<span data-ttu-id="c9268-153">Pacotes do NuGet com um sufixo de versão são considerados [pré-lançamento](/nuget/create-packages/prerelease-packages).</span><span class="sxs-lookup"><span data-stu-id="c9268-153">NuGet packages with a version suffix are considered [pre-release](/nuget/create-packages/prerelease-packages).</span></span> <span data-ttu-id="c9268-154">Por padrão, a interface do usuário do Gerenciador de Pacotes do NuGet mostra versões estáveis, a menos que um usuário aceite pacotes de pré-lançamento, tornando os pacotes de pré-lançamento ideais para testes de usuários limitados.</span><span class="sxs-lookup"><span data-stu-id="c9268-154">By default, the NuGet Package Manager UI shows stable releases unless a user opts-in to pre-release packages, making pre-release packages ideal for limited user testing.</span></span>

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> <span data-ttu-id="c9268-155">Um pacote estável não pode depender de um pacote de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="c9268-155">A stable package cannot depend on a pre-release package.</span></span> <span data-ttu-id="c9268-156">Você deve criar seu próprio pacote de pré-lançamento ou depender de uma versão estável mais antiga.</span><span class="sxs-lookup"><span data-stu-id="c9268-156">You must either make your own package pre-release or depend on an older stable version.</span></span>

<span data-ttu-id="c9268-157">![Dependência de pacote de pré-lançamento do NuGet](./media/nuget/nuget-prerelease-package.png "Dependência de pacote de pré-lançamento do NuGet")</span><span class="sxs-lookup"><span data-stu-id="c9268-157">![NuGet pre-release package dependency](./media/nuget/nuget-prerelease-package.png "NuGet pre-release package dependency")</span></span>

<span data-ttu-id="c9268-158">**✔️ FAÇA** a publicação de um pacote de pré-lançamento ao testar, visualizar ou experimentar.</span><span class="sxs-lookup"><span data-stu-id="c9268-158">**✔️ DO** publish a pre-release package when testing, previewing, or experimenting.</span></span>

<span data-ttu-id="c9268-159">**✔️ FAÇA** a publicação de um pacote estável quando ele estiver pronto para que outros pacotes estáveis possam fazer referência a ele.</span><span class="sxs-lookup"><span data-stu-id="c9268-159">**✔️ DO** publish a stable package when its ready so other stable packages can reference it.</span></span>

## <a name="symbol-packages"></a><span data-ttu-id="c9268-160">Pacotes de símbolo</span><span class="sxs-lookup"><span data-stu-id="c9268-160">Symbol packages</span></span>

<span data-ttu-id="c9268-161">Arquivos de símbolo (`*.pdb`) são produzidos pelo compilador do .NET junto com assemblies.</span><span class="sxs-lookup"><span data-stu-id="c9268-161">Symbol files (`*.pdb`) are produced by the .NET compiler alongside assemblies.</span></span> <span data-ttu-id="c9268-162">Arquivos de símbolo mapeiam locais de execução para o código-fonte original para que você possa percorrer o código-fonte conforme ele é executado usando um depurador.</span><span class="sxs-lookup"><span data-stu-id="c9268-162">Symbol files map execution locations to the original source code so you can step through source code as it is running using a debugger.</span></span> <span data-ttu-id="c9268-163">O NuGet é compatível com a [geração de um pacote de símbolos separado (`*.snupkg`)](/nuget/create-packages/symbol-packages-snupkg) contendo arquivos de símbolo junto com o pacote principal contendo assemblies do .NET.</span><span class="sxs-lookup"><span data-stu-id="c9268-163">NuGet supports [generating a separate symbol package (`*.snupkg`)](/nuget/create-packages/symbol-packages-snupkg) containing symbol files alongside the main package containing .NET assemblies.</span></span> <span data-ttu-id="c9268-164">A ideia de pacotes de símbolos é que eles estão hospedados em um servidor de símbolos e são baixados somente por uma ferramenta como o Visual Studio sob demanda.</span><span class="sxs-lookup"><span data-stu-id="c9268-164">The idea of symbol packages is they're hosted on a symbol server and are only downloaded by a tool like Visual Studio on demand.</span></span>

<span data-ttu-id="c9268-165">O NuGet.org hospeda seu próprio [repositório do servidor de símbolos](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server).</span><span class="sxs-lookup"><span data-stu-id="c9268-165">NuGet.org hosts its own [symbols server repository](/nuget/create-packages/symbol-packages-snupkg#nugetorg-symbol-server).</span></span> <span data-ttu-id="c9268-166">Os desenvolvedores podem usar os símbolos publicados no servidor de símbolos do NuGet.org adicionando `https://symbols.nuget.org/download/symbols` às suas [fontes de símbolos no Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span><span class="sxs-lookup"><span data-stu-id="c9268-166">Developers can use the symbols published to the NuGet.org symbol server by adding `https://symbols.nuget.org/download/symbols` to their [symbol sources in Visual Studio](/visualstudio/debugger/specify-symbol-dot-pdb-and-source-files-in-the-visual-studio-debugger).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="c9268-167">O servidor de símbolos do NuGet.org é compatível apenas com novos [arquivos de símbolo portátil](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) criados por projetos no estilo de SDK.</span><span class="sxs-lookup"><span data-stu-id="c9268-167">The NuGet.org symbol server only supports the new [portable symbol files](https://github.com/dotnet/core/blob/master/Documentation/diagnostics/portable_pdb.md) (`*.pdb`) created by SDK-style projects.</span></span>

<span data-ttu-id="c9268-168">Uma alternativa para criar um pacote de símbolos é inserir arquivos de símbolo no pacote do NuGet principal.</span><span class="sxs-lookup"><span data-stu-id="c9268-168">An alternative to creating a symbol package is embedding symbol files in the main NuGet package.</span></span> <span data-ttu-id="c9268-169">O pacote do NuGet principal será maior, mas os arquivos de símbolos inseridos significam que os desenvolvedores não precisam configurar o servidor de símbolos do NuGet.org.</span><span class="sxs-lookup"><span data-stu-id="c9268-169">The main NuGet package will be larger, but the embedded symbol files means developers don't need to configure the NuGet.org symbol server.</span></span> <span data-ttu-id="c9268-170">Se você estiver criando seu pacote do NuGet usando um projeto de estilo do SDK, poderá inserir arquivos de símbolo definindo a propriedade `AllowedOutputExtensionsInPackageBuildOutputFolder`:</span><span class="sxs-lookup"><span data-stu-id="c9268-170">If you're building your NuGet package using an SDK-style project, then you can embed symbol files by setting the `AllowedOutputExtensionsInPackageBuildOutputFolder` property:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
 <PropertyGroup>
    <!-- Include symbol files (*.pdb) in the built .nupkg -->
    <AllowedOutputExtensionsInPackageBuildOutputFolder>$(AllowedOutputExtensionsInPackageBuildOutputFolder);.pdb</AllowedOutputExtensionsInPackageBuildOutputFolder>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="c9268-171">**✔️ CONSIDERE** inserir arquivos de símbolo no pacote NuGet principal.</span><span class="sxs-lookup"><span data-stu-id="c9268-171">**✔️ CONSIDER** embedding symbol files in the main NuGet package.</span></span>

> <span data-ttu-id="c9268-172">Inserir arquivos de símbolo no pacote do NuGet principal oferece aos desenvolvedores em uma experiência de depuração melhor por padrão.</span><span class="sxs-lookup"><span data-stu-id="c9268-172">Embedding symbol files in the main NuGet package gives developers a better debugging experience by default.</span></span> <span data-ttu-id="c9268-173">Eles não precisam encontrar e configurar o servidor de símbolos do NuGet no seu IDE para obter os arquivos de símbolo.</span><span class="sxs-lookup"><span data-stu-id="c9268-173">They don't need to find and configure the NuGet symbol server in their IDE to get symbol files.</span></span>
>
> <span data-ttu-id="c9268-174">A desvantagem de arquivos de símbolo inseridos é que eles aumentam o tamanho do pacote em cerca de 30% para bibliotecas do .NET compiladas usando os projetos de estilo de SDK.</span><span class="sxs-lookup"><span data-stu-id="c9268-174">The downside to embedded symbol files is they increase the package size by about 30% for .NET libraries compiled using SDK-style projects.</span></span> <span data-ttu-id="c9268-175">Se o tamanho do pacote é uma preocupação, você deve publicar símbolos em um pacote de símbolos em vez disso.</span><span class="sxs-lookup"><span data-stu-id="c9268-175">If package size is a concern, you should publish symbols in a symbol package instead.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c9268-176">[Anterior](strong-naming.md)
>[Próximo](dependencies.md)</span><span class="sxs-lookup"><span data-stu-id="c9268-176">[Previous](strong-naming.md)
[Next](dependencies.md)</span></span>