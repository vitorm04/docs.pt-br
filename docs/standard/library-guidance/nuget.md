---
title: Bibliotecas do NuGet e .NET
description: Práticas recomendadas para o empacotamento com o NuGet para bibliotecas do .NET.
author: jamesnk
ms.author: mairaw
ms.date: 10/02/2018
ms.openlocfilehash: d0ea462a7f52dd9a6b2f14be9ed5770160bf66b1
ms.sourcegitcommit: e42d09e5966dd9fd02847d3e7eeb4ec0877069f8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2018
ms.locfileid: "49374478"
---
# <a name="nuget"></a><span data-ttu-id="465e5-103">NuGet</span><span class="sxs-lookup"><span data-stu-id="465e5-103">NuGet</span></span>

<span data-ttu-id="465e5-104">NuGet é um Gerenciador de pacotes para o ecossistema do .NET e é os principal dos desenvolvedores descobrir e adquirem as bibliotecas de código-fonte aberto do .NET.</span><span class="sxs-lookup"><span data-stu-id="465e5-104">NuGet is a package manager for the .NET ecosystem and is the primary way developers discover and acquire .NET open-source libraries.</span></span> <span data-ttu-id="465e5-105">[NuGet.org](https://www.nuget.org/), um serviço gratuito, fornecido pela Microsoft para hospedar pacotes do NuGet, é o host primário para os pacotes do NuGet públicos, mas você pode publicar em serviços personalizados do NuGet, como [MyGet](https://www.myget.org/) e [artefatos do Azure ](https://azure.microsoft.com/services/devops/artifacts/).</span><span class="sxs-lookup"><span data-stu-id="465e5-105">[NuGet.org](https://www.nuget.org/), a free service provided by Microsoft for hosting NuGet packages, is the primary host for public NuGet packages, but you can publish to custom NuGet services like [MyGet](https://www.myget.org/) and [Azure Artifacts](https://azure.microsoft.com/services/devops/artifacts/).</span></span>

<span data-ttu-id="465e5-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span><span class="sxs-lookup"><span data-stu-id="465e5-106">![NuGet](./media/nuget/nuget-logo.png "NuGet")</span></span>

## <a name="create-a-nuget-package"></a><span data-ttu-id="465e5-107">Criar um pacote do NuGet</span><span class="sxs-lookup"><span data-stu-id="465e5-107">Create a NuGet package</span></span>

<span data-ttu-id="465e5-108">Um pacote do NuGet (`*.nupkg`) é um arquivo zip que contém os assemblies do .NET e os metadados associados.</span><span class="sxs-lookup"><span data-stu-id="465e5-108">A NuGet package (`*.nupkg`) is a zip file that contains .NET assemblies and associated metadata.</span></span>

<span data-ttu-id="465e5-109">Há duas maneiras principais de criar um pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="465e5-109">There are two main ways to create a NuGet package.</span></span> <span data-ttu-id="465e5-110">A maneira recomendada e mais recente é criar um pacote de um projeto de estilo do SDK (arquivo de projeto cujo conteúdo é iniciado com `<Project Sdk="Microsoft.NET.Sdk">`).</span><span class="sxs-lookup"><span data-stu-id="465e5-110">The newer and recommended way is to create a package from a SDK-style project (project file whose content starts with `<Project Sdk="Microsoft.NET.Sdk">`).</span></span> <span data-ttu-id="465e5-111">Assemblies e destinos são automaticamente adicionados ao pacote e o restante de metadados é adicionada ao arquivo MSBuild, como o número de versão e o nome do pacote.</span><span class="sxs-lookup"><span data-stu-id="465e5-111">Assemblies and targets are automatically added to the package and remaining metadata is added to the MSBuild file, like package name and version number.</span></span> <span data-ttu-id="465e5-112">Compilar com o [ `dotnet pack` ](../../core/tools/dotnet-pack.md) saídas de comando um `*.nupkg` arquivo em vez de assemblies.</span><span class="sxs-lookup"><span data-stu-id="465e5-112">Compiling with the [`dotnet pack`](../../core/tools/dotnet-pack.md) command outputs a `*.nupkg` file instead of assemblies.</span></span>

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

<span data-ttu-id="465e5-113">A maneira mais antiga da criação de um pacote do NuGet é com um `*.nuspec` arquivo e o `nuget.exe` ferramenta de linha de comando.</span><span class="sxs-lookup"><span data-stu-id="465e5-113">The older way of creating a NuGet package is with a `*.nuspec` file and the `nuget.exe` command-line tool.</span></span> <span data-ttu-id="465e5-114">Um arquivo nuspec lhe dá controle excelente, mas você deve especificar cuidadosamente quais assemblies e destinos para incluir no pacote do NuGet final.</span><span class="sxs-lookup"><span data-stu-id="465e5-114">A nuspec file gives you great control but you must carefully specify what assemblies and targets to include in the final NuGet package.</span></span> <span data-ttu-id="465e5-115">É fácil cometer um erro ou que alguém se esqueça de atualizar o nuspec ao fazer alterações.</span><span class="sxs-lookup"><span data-stu-id="465e5-115">It's easy to make a mistake or for someone to forget to update the nuspec when making changes.</span></span> <span data-ttu-id="465e5-116">A vantagem de um nuspec é que você pode usá-la criar pacotes do NuGet para estruturas que ainda não dão suporte a um arquivo de projeto de estilo do SDK.</span><span class="sxs-lookup"><span data-stu-id="465e5-116">The advantage of a nuspec is you can use it create NuGet packages for frameworks that don't yet support an SDK-style project file.</span></span>

<span data-ttu-id="465e5-117">**Considere a possibilidade de ✔️** usando um arquivo de projeto de estilo do SDK para criar o pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="465e5-117">**✔️ CONSIDER** using an SDK-style project file to create the NuGet package.</span></span>

<span data-ttu-id="465e5-118">**Considere a possibilidade de ✔️** Configurando SourceLink para adicionar metadados de controle do código-fonte para seus assemblies e o pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="465e5-118">**✔️ CONSIDER** setting up SourceLink to add source control metadata to your assemblies and NuGet package.</span></span>

## <a name="package-dependencies"></a><span data-ttu-id="465e5-119">Dependências do pacote</span><span class="sxs-lookup"><span data-stu-id="465e5-119">Package dependencies</span></span>

<span data-ttu-id="465e5-120">Dependências de pacotes NuGet são abordadas detalhadamente os [dependências](./dependencies.md) artigo.</span><span class="sxs-lookup"><span data-stu-id="465e5-120">NuGet package dependencies are covered in detail in the [Dependencies](./dependencies.md) article.</span></span>

## <a name="important-nuget-package-metadata"></a><span data-ttu-id="465e5-121">Metadados de pacote do NuGet importantes</span><span class="sxs-lookup"><span data-stu-id="465e5-121">Important NuGet package metadata</span></span>

<span data-ttu-id="465e5-122">Um pacote do NuGet dá suporte a muitos [propriedades de metadados](/nuget/reference/nuspec).</span><span class="sxs-lookup"><span data-stu-id="465e5-122">A NuGet package supports many [metadata properties](/nuget/reference/nuspec).</span></span> <span data-ttu-id="465e5-123">A tabela a seguir contém os metadados de núcleo que cada projeto de código-fonte aberto deve fornecer:</span><span class="sxs-lookup"><span data-stu-id="465e5-123">The following table contains the core metadata that every open-source project should provide:</span></span>

| <span data-ttu-id="465e5-124">Nome da propriedade do MSBuild</span><span class="sxs-lookup"><span data-stu-id="465e5-124">MSBuild Property name</span></span>              | <span data-ttu-id="465e5-125">Nome de NuSpec</span><span class="sxs-lookup"><span data-stu-id="465e5-125">Nuspec name</span></span>              | <span data-ttu-id="465e5-126">Descrição</span><span class="sxs-lookup"><span data-stu-id="465e5-126">Description</span></span>  |
| ---------------------------------- | ------------------------ | ------------ |
| `PackageId`                        | `id`                       | <span data-ttu-id="465e5-127">O identificador de pacote.</span><span class="sxs-lookup"><span data-stu-id="465e5-127">The package identifier.</span></span> <span data-ttu-id="465e5-128">Um prefixo do identificador pode ser reservado se ele atende a [critérios](/nuget/reference/id-prefix-reservation).</span><span class="sxs-lookup"><span data-stu-id="465e5-128">A prefix from the identifier can be reserved if it meets the [criteria](/nuget/reference/id-prefix-reservation).</span></span> |
| `PackageVersion`                   | `version`                  | <span data-ttu-id="465e5-129">Versão do pacote do NuGet.</span><span class="sxs-lookup"><span data-stu-id="465e5-129">NuGet package version.</span></span> <span data-ttu-id="465e5-130">Para obter mais informações, consulte [versão do pacote NuGet](./versioning.md#nuget-package-version).</span><span class="sxs-lookup"><span data-stu-id="465e5-130">For more information, see [NuGet package version](./versioning.md#nuget-package-version).</span></span>             |
| `Title`                            | `title`                    | <span data-ttu-id="465e5-131">Um título amigável a humanos do pacote.</span><span class="sxs-lookup"><span data-stu-id="465e5-131">A human-friendly title of the package.</span></span> <span data-ttu-id="465e5-132">O padrão é o `PackageId`.</span><span class="sxs-lookup"><span data-stu-id="465e5-132">It defaults to the `PackageId`.</span></span>             |
| `Description`                      | `description`              | <span data-ttu-id="465e5-133">Uma descrição longa do pacote exibido na interface do usuário.</span><span class="sxs-lookup"><span data-stu-id="465e5-133">A long description of the package displayed in UI.</span></span>             |
| `Authors`                          | `authors`                  | <span data-ttu-id="465e5-134">Uma lista separada por vírgulas de autores de pacote, a correspondência de nomes de perfil em nuget.org.</span><span class="sxs-lookup"><span data-stu-id="465e5-134">A comma-separated list of package authors, matching the profile names on nuget.org.</span></span>             |
| `PackageTags`                      | `tags`                     | <span data-ttu-id="465e5-135">Uma lista delimitada por espaço de marcas e palavras-chave que descrevem o pacote.</span><span class="sxs-lookup"><span data-stu-id="465e5-135">A space-delimited list of tags and keywords that describe the package.</span></span> <span data-ttu-id="465e5-136">Marcas são usadas ao procurar pacotes.</span><span class="sxs-lookup"><span data-stu-id="465e5-136">Tags are used when searching for packages.</span></span>             |
| `PackageIconUrl`                   | `iconUrl`                  | <span data-ttu-id="465e5-137">Uma URL para uma imagem a ser usado como o ícone para o pacote.</span><span class="sxs-lookup"><span data-stu-id="465e5-137">A URL for an image to use as the icon for the package.</span></span> <span data-ttu-id="465e5-138">URL deve ser HTTPS e a imagem deve ser 64 x 64 e ter um plano de fundo transparente.</span><span class="sxs-lookup"><span data-stu-id="465e5-138">URL should be HTTPS and the image should be 64x64 and have a transparent background.</span></span>             |
| `PackageProjectUrl`                | `projectUrl`               | <span data-ttu-id="465e5-139">Uma URL para o repositório de home page ou a fonte do projeto.</span><span class="sxs-lookup"><span data-stu-id="465e5-139">A URL for the project homepage or source repository.</span></span>             |
| `PackageLicenseUrl`                | `licenseUrl`               | <span data-ttu-id="465e5-140">Uma URL para a licença do projeto.</span><span class="sxs-lookup"><span data-stu-id="465e5-140">A URL to the project license.</span></span> <span data-ttu-id="465e5-141">Pode ser a URL para o `LICENSE` arquivo no controle de origem.</span><span class="sxs-lookup"><span data-stu-id="465e5-141">Can be the URL to the `LICENSE` file in source control.</span></span>             |

<span data-ttu-id="465e5-142">**Considere a possibilidade de ✔️** escolher um nome de pacote do NuGet com um prefixo que atenda a reserva de prefixo do NuGet [critérios](/nuget/reference/id-prefix-reservation).</span><span class="sxs-lookup"><span data-stu-id="465e5-142">**✔️ CONSIDER** choosing a NuGet package name with a prefix that meets NuGet's prefix reservation [criteria](/nuget/reference/id-prefix-reservation).</span></span>

<span data-ttu-id="465e5-143">**✔️ CONSIDERE** usando o `LICENSE` arquivo no controle do código-fonte como o `LicenseUrl`.</span><span class="sxs-lookup"><span data-stu-id="465e5-143">**✔️ CONSIDER** using the `LICENSE` file in source control as the `LicenseUrl`.</span></span> <span data-ttu-id="465e5-144">Por exemplo, [LICENSE.md](https://github.com/JamesNK/Newtonsoft.Json/blob/c4af75c8e91ca0d75aa6c335e8c106780c4f7712/LICENSE.md).</span><span class="sxs-lookup"><span data-stu-id="465e5-144">For example, [LICENSE.md](https://github.com/JamesNK/Newtonsoft.Json/blob/c4af75c8e91ca0d75aa6c335e8c106780c4f7712/LICENSE.md).</span></span>

> [!IMPORTANT]
> <span data-ttu-id="465e5-145">Um projeto sem o padrão é uma licença [copyright exclusivo](https://choosealicense.com/no-permission/), tornando impossível para que outras pessoas usem.</span><span class="sxs-lookup"><span data-stu-id="465e5-145">A project without a license defaults to [exclusive copyright](https://choosealicense.com/no-permission/), making it impossible for other people to use.</span></span>

<span data-ttu-id="465e5-146">**FAZER ✔️** usar um href HTTPS com o ícone do pacote.</span><span class="sxs-lookup"><span data-stu-id="465e5-146">**✔️ DO** use an HTTPS href to your package icon.</span></span>

> <span data-ttu-id="465e5-147">Sites, como o NuGet.org executam com habilitadas para HTTPS e exibir uma imagem não HTTPS criará um aviso de conteúdo misto.</span><span class="sxs-lookup"><span data-stu-id="465e5-147">Sites like NuGet.org run with HTTPS enabled and displaying a non-HTTPS image will create a mixed content warning.</span></span>

<span data-ttu-id="465e5-148">**FAZER ✔️** usar uma imagem de ícone do pacote que é 64 x 64 e tem um plano de fundo transparente para melhor visualização dos resultados.</span><span class="sxs-lookup"><span data-stu-id="465e5-148">**✔️ DO** use a package icon image that is 64x64 and has a transparent background for best viewing results.</span></span>

## <a name="pre-release-packages"></a><span data-ttu-id="465e5-149">Pacotes de pré-lançamento</span><span class="sxs-lookup"><span data-stu-id="465e5-149">Pre-release packages</span></span>

<span data-ttu-id="465e5-150">Pacotes do NuGet com um sufixo de versão são considerados [pré-lançamento](/nuget/create-packages/prerelease-packages).</span><span class="sxs-lookup"><span data-stu-id="465e5-150">NuGet packages with a version suffix are considered [pre-release](/nuget/create-packages/prerelease-packages).</span></span> <span data-ttu-id="465e5-151">Por padrão, a UI do Gerenciador de pacotes do NuGet mostra versões estáveis, a menos que um usuário aceita-in de pré-lançamento em pacotes, tornando os pacotes de pré-lançamento ideal para testes de usuário limitado.</span><span class="sxs-lookup"><span data-stu-id="465e5-151">By default, the NuGet Package Manager UI shows stable releases unless a user opts-in to pre-release packages, making pre-release packages ideal for limited user testing.</span></span>

```xml
<PackageVersion>1.0.1-beta1</PackageVersion>
```

> [!NOTE]
> <span data-ttu-id="465e5-152">Um pacote estável não pode depender de um pacote de pré-lançamento.</span><span class="sxs-lookup"><span data-stu-id="465e5-152">A stable package cannot depend on a pre-release package.</span></span> <span data-ttu-id="465e5-153">Você deve fazer seu próprio pacote de pré-lançamento ou dependem de uma versão estável mais antiga.</span><span class="sxs-lookup"><span data-stu-id="465e5-153">You must either make your own package pre-release or depend on an older stable version.</span></span>

<span data-ttu-id="465e5-154">![Dependência de pacote de pré-lançamento do NuGet](./media/nuget/nuget-prerelease-package.png "dependência de pacote de pré-lançamento do NuGet")</span><span class="sxs-lookup"><span data-stu-id="465e5-154">![NuGet pre-release package dependency](./media/nuget/nuget-prerelease-package.png "NuGet pre-release package dependency")</span></span>

<span data-ttu-id="465e5-155">**FAZER ✔️** publicar um pacote de pré-lançamento ao testar, visualizar ou testar.</span><span class="sxs-lookup"><span data-stu-id="465e5-155">**✔️ DO** publish a pre-release package when testing, previewing, or experimenting.</span></span>

<span data-ttu-id="465e5-156">**FAZER ✔️** publicar um pacote estável quando seu pronto para os outros pacotes estáveis podem fazer referência a ela.</span><span class="sxs-lookup"><span data-stu-id="465e5-156">**✔️ DO** publish a stable package when its ready so other stable packages can reference it.</span></span>

## <a name="symbol-packages"></a><span data-ttu-id="465e5-157">Pacotes de símbolos</span><span class="sxs-lookup"><span data-stu-id="465e5-157">Symbol packages</span></span>

<span data-ttu-id="465e5-158">O NuGet dá suporte a [gerar um pacote de símbolos separados](/nuget/create-packages/symbol-packages) contendo depurar arquivos PDB junto com o pacote principal que contém os assemblies do .NET.</span><span class="sxs-lookup"><span data-stu-id="465e5-158">NuGet supports [generating a separate symbol package](/nuget/create-packages/symbol-packages) containing debug PDB files alongside the main package containing .NET assemblies.</span></span> <span data-ttu-id="465e5-159">A ideia de pacotes de símbolos é que eles estão hospedados em um servidor de símbolos e são baixados somente por uma ferramenta como o Visual Studio sob demanda.</span><span class="sxs-lookup"><span data-stu-id="465e5-159">The idea of symbol packages is they're hosted on a symbol server and are only downloaded by a tool like Visual Studio on demand.</span></span>

<span data-ttu-id="465e5-160">No momento, o principal público do host para símbolos - [SymbolSource](http://www.symbolsource.org/) -não dá suporte as PDBs portáteis criados pelo SDK do estilo projetos e pacotes de símbolos não são úteis.</span><span class="sxs-lookup"><span data-stu-id="465e5-160">Currently the main public host for symbols - [SymbolSource](http://www.symbolsource.org/) - doesn't support the portable PDBs created by SDK-style projects and symbol packages aren't useful.</span></span>

<span data-ttu-id="465e5-161">**Considere a possibilidade de ✔️** inserindo PDBs no pacote NuGet principal.</span><span class="sxs-lookup"><span data-stu-id="465e5-161">**✔️ CONSIDER** embedding PDBs in the main NuGet package.</span></span>

<span data-ttu-id="465e5-162">**❌ Evite** criando um pacote de símbolos com PDBs.</span><span class="sxs-lookup"><span data-stu-id="465e5-162">**❌ AVOID** creating a symbols package containing PDBs.</span></span>

>[!div class="step-by-step"]
<span data-ttu-id="465e5-163">[Anterior](./strong-naming.md)
[Próximo](./dependencies.md)</span><span class="sxs-lookup"><span data-stu-id="465e5-163">[Previous](./strong-naming.md)
[Next](./dependencies.md)</span></span>
