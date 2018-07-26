---
title: Modelo de extensibilidade da CLI do .NET Core
description: Saiba como você pode estender as ferramentas da CLI (interface de linha de comando).
author: blackdwarf
ms.author: mairaw
ms.date: 04/12/2017
ms.openlocfilehash: 6cabd3959a29878788916ae26589be408c12e0ca
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/25/2018
ms.locfileid: "39244784"
---
# <a name="net-core-cli-tools-extensibility-model"></a><span data-ttu-id="37842-103">Modelo de extensibilidade das ferramentas da CLI do .NET Core</span><span class="sxs-lookup"><span data-stu-id="37842-103">.NET Core CLI tools extensibility model</span></span>

<span data-ttu-id="37842-104">Este documento aborda as diferentes maneiras que você pode estender as ferramentas da CLI (interface de linha de comando) do .NET Core e explica os cenários que orientam cada uma delas.</span><span class="sxs-lookup"><span data-stu-id="37842-104">This document covers the different ways you can extend the .NET Core Command-line Interface (CLI) tools and explain the scenarios that drive each one of them.</span></span>
<span data-ttu-id="37842-105">Você verá como utilizar as ferramentas, bem como criar os diferentes tipos de ferramentas.</span><span class="sxs-lookup"><span data-stu-id="37842-105">You'll see how to consume the tools as well as how to build the different types of tools.</span></span>

## <a name="how-to-extend-cli-tools"></a><span data-ttu-id="37842-106">Como estender as ferramentas da CLI</span><span class="sxs-lookup"><span data-stu-id="37842-106">How to extend CLI tools</span></span>
<span data-ttu-id="37842-107">As ferramentas da CLI podem ser estendidas de três maneiras principais:</span><span class="sxs-lookup"><span data-stu-id="37842-107">The CLI tools can be extended in three main ways:</span></span>

1. [<span data-ttu-id="37842-108">Por meio de pacotes NuGet por projeto</span><span class="sxs-lookup"><span data-stu-id="37842-108">Via NuGet packages on a per-project basis</span></span>](#per-project-based-extensibility)

   <span data-ttu-id="37842-109">As ferramentas por projeto estão contidas no contexto do projeto, mas permitem uma fácil instalação por meio da restauração.</span><span class="sxs-lookup"><span data-stu-id="37842-109">Per-project tools are contained within the project's context, but they allow easy installation through restoration.</span></span>

2. [<span data-ttu-id="37842-110">Por meio de pacotes NuGet com destinos personalizados</span><span class="sxs-lookup"><span data-stu-id="37842-110">Via NuGet packages with custom targets</span></span>](#custom-targets)

   <span data-ttu-id="37842-111">Destinos personalizados permitem que você amplie facilmente o processo de build com tarefas personalizadas.</span><span class="sxs-lookup"><span data-stu-id="37842-111">Custom targets allow you to easily extend the build process with custom tasks.</span></span>

3. [<span data-ttu-id="37842-112">Por meio do PATH do sistema</span><span class="sxs-lookup"><span data-stu-id="37842-112">Via the system's PATH</span></span>](#path-based-extensibility)

   <span data-ttu-id="37842-113">Ferramentas baseadas em PATH são boas para ferramentas gerais de vários projetos que são usadas em um único computador.</span><span class="sxs-lookup"><span data-stu-id="37842-113">PATH-based tools are good for general, cross-project tools that are usable on a single machine.</span></span>

<span data-ttu-id="37842-114">Os três mecanismos de extensibilidade descritos acima não são exclusivos.</span><span class="sxs-lookup"><span data-stu-id="37842-114">The three extensibility mechanisms outlined above are not exclusive.</span></span> <span data-ttu-id="37842-115">Você pode usar um, todos ou uma combinação deles.</span><span class="sxs-lookup"><span data-stu-id="37842-115">You can use one, or all, or a combination of them.</span></span> <span data-ttu-id="37842-116">Qual deles escolher depende muito da meta que você está tentando alcançar com a extensão.</span><span class="sxs-lookup"><span data-stu-id="37842-116">Which one to pick depends largely on the goal you are trying to achieve with your extension.</span></span>

## <a name="per-project-based-extensibility"></a><span data-ttu-id="37842-117">Extensibilidade por projeto</span><span class="sxs-lookup"><span data-stu-id="37842-117">Per-project based extensibility</span></span>
<span data-ttu-id="37842-118">Ferramentas por projeto são [implantações dependentes de estrutura](../deploying/index.md#framework-dependent-deployments-fdd) distribuídas como pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="37842-118">Per-project tools are [framework-dependent deployments](../deploying/index.md#framework-dependent-deployments-fdd) that are distributed as NuGet packages.</span></span> <span data-ttu-id="37842-119">As ferramentas estão disponíveis apenas no contexto do projeto que faz referência a eles e para os quais eles são restaurados.</span><span class="sxs-lookup"><span data-stu-id="37842-119">Tools are only available in the context of the project that references them and for which they are restored.</span></span> <span data-ttu-id="37842-120">A invocação fora do contexto do projeto (por exemplo, fora do diretório que contém o projeto) falhará porque o comando não foi encontrado.</span><span class="sxs-lookup"><span data-stu-id="37842-120">Invocation outside of the context of the project (for example, outside of the directory that contains the project) will fail because the command cannot be found.</span></span>

<span data-ttu-id="37842-121">Essas ferramentas são perfeitas para criar servidores, desde que nada fora do arquivo de projeto seja necessário.</span><span class="sxs-lookup"><span data-stu-id="37842-121">These tools are perfect for build servers, since nothing outside of the project file is needed.</span></span> <span data-ttu-id="37842-122">O processo de build executa a restauração para o projeto compilado e as ferramentas disponíveis.</span><span class="sxs-lookup"><span data-stu-id="37842-122">The build process runs restore for the project it builds and tools will be available.</span></span> <span data-ttu-id="37842-123">Projetos de linguagem, como F#, também estão nesta categoria, uma vez que cada projeto pode ser escrito apenas em uma linguagem específica.</span><span class="sxs-lookup"><span data-stu-id="37842-123">Language projects, such as F#, are also in this category since each project can only be written in one specific language.</span></span>

<span data-ttu-id="37842-124">Por fim, esse modelo de extensibilidade dá suporte à criação de ferramentas que precisam acessar a saída da compilação do projeto.</span><span class="sxs-lookup"><span data-stu-id="37842-124">Finally, this extensibility model provides support for creation of tools that need access to the built output of the project.</span></span> <span data-ttu-id="37842-125">Por exemplo, diversas ferramentas de exibição Razor em aplicativos [ASP.NET](https://www.asp.net/) MVC se enquadram nesta categoria.</span><span class="sxs-lookup"><span data-stu-id="37842-125">For instance, various Razor view tools in [ASP.NET](https://www.asp.net/) MVC applications fall into this category.</span></span>

### <a name="consuming-per-project-tools"></a><span data-ttu-id="37842-126">Consumir ferramentas por projeto</span><span class="sxs-lookup"><span data-stu-id="37842-126">Consuming per-project tools</span></span>
<span data-ttu-id="37842-127">Consumir essas ferramentas requer a adição de um elemento `<DotNetCliToolReference>` ao seu arquivo de projeto para cada ferramenta que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="37842-127">Consuming these tools requires you to add a `<DotNetCliToolReference>` element to your project file for each tool you want to use.</span></span> <span data-ttu-id="37842-128">Dentro do elemento `<DotNetCliToolReference>`, você referencia o pacote no qual a ferramenta reside e especifica a versão necessária.</span><span class="sxs-lookup"><span data-stu-id="37842-128">Inside the `<DotNetCliToolReference>` element, you reference the package in which the tool resides and specify the version you need.</span></span> <span data-ttu-id="37842-129">Após executar [`dotnet restore`](dotnet-restore.md), a ferramenta e suas dependências são restauradas.</span><span class="sxs-lookup"><span data-stu-id="37842-129">After running [`dotnet restore`](dotnet-restore.md), the tool and its dependencies are restored.</span></span>

[!INCLUDE[DotNet Restore Note](~/includes/dotnet-restore-note.md)]

<span data-ttu-id="37842-130">Para ferramentas que precisam carregar a saída do build do projeto para execução, geralmente há outra dependência listada nas dependências regulares no arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="37842-130">For tools that need to load the build output of the project for execution, there is usually another dependency which is listed under the regular dependencies in the project file.</span></span> <span data-ttu-id="37842-131">Como a CLI usa o MSBuild como seu mecanismo de build, é recomendável que essas partes da ferramenta sejam gravadas como [destinos](/visualstudio/msbuild/msbuild-targets) e [tarefas](/visualstudio/msbuild/msbuild-tasks) personalizados do MSBuild, pois eles podem participar do processo geral de build.</span><span class="sxs-lookup"><span data-stu-id="37842-131">Since CLI uses MSBuild as its build engine, we recommend that these parts of the tool be written as custom MSBuild [targets](/visualstudio/msbuild/msbuild-targets) and [tasks](/visualstudio/msbuild/msbuild-tasks), since they can then take part in the overall build process.</span></span> <span data-ttu-id="37842-132">Além disso, eles podem obter todos os dados produzidos por meio do build facilmente, como o local dos arquivos de saída, a configuração atual que está sendo compilada, etc. Todas essas informações se tornam um conjunto de propriedades do MSBuild que pode ser lido de qualquer destino.</span><span class="sxs-lookup"><span data-stu-id="37842-132">Also, they can get any and all data easily that is produced via the build, such as the location of the output files, the current configuration being built, etc. All this information becomes a set of MSBuild properties that can be read from any target.</span></span> <span data-ttu-id="37842-133">Você pode ver como adicionar um destino personalizado usando o NuGet mais adiante neste documento.</span><span class="sxs-lookup"><span data-stu-id="37842-133">You can see how to add a custom target using NuGet later in this document.</span></span>

<span data-ttu-id="37842-134">Vamos examinar um exemplo de como adicionar uma ferramenta única simples a um projeto simples.</span><span class="sxs-lookup"><span data-stu-id="37842-134">Let's review an example of adding a simple tools-only tool to a simple project.</span></span> <span data-ttu-id="37842-135">Dado um exemplo de comando chamado `dotnet-api-search` que permite que você pesquise os pacotes NuGet para a API especificada, veja este arquivo de projeto do aplicativo de console que usa essa ferramenta:</span><span class="sxs-lookup"><span data-stu-id="37842-135">Given an example command called `dotnet-api-search` that allows you to search through the NuGet packages for the specified API, here is a console application's project file that uses that tool:</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <OutputType>Exe</OutputType>
    <TargetFramework>netcoreapp1.1</TargetFramework>
  </PropertyGroup>

  <!-- The tools reference -->
  <ItemGroup>
    <DotNetCliToolReference Include="dotnet-api-search" Version="1.0.0" />
  </ItemGroup>
</Project>
```

<span data-ttu-id="37842-136">O elemento `<DotNetCliToolReference>` é estruturado de forma semelhante ao elemento `<PackageReference>`.</span><span class="sxs-lookup"><span data-stu-id="37842-136">The `<DotNetCliToolReference>` element is structured in a similar way as the `<PackageReference>` element.</span></span> <span data-ttu-id="37842-137">Ele precisa da ID do pacote que contém a ferramenta e sua versão para poder restaurar.</span><span class="sxs-lookup"><span data-stu-id="37842-137">It needs the package ID of the package containing the tool and its version to be able to restore.</span></span>

### <a name="building-tools"></a><span data-ttu-id="37842-138">Compilando ferramentas</span><span class="sxs-lookup"><span data-stu-id="37842-138">Building tools</span></span>
<span data-ttu-id="37842-139">Como mencionado anteriormente, ferramentas são apenas aplicativos de console portáteis.</span><span class="sxs-lookup"><span data-stu-id="37842-139">As mentioned, tools are just portable console applications.</span></span> <span data-ttu-id="37842-140">Você compila as ferramentas da mesma maneira que qualquer outro aplicativo de console.</span><span class="sxs-lookup"><span data-stu-id="37842-140">You build tools as you would build any other console application.</span></span>
<span data-ttu-id="37842-141">Depois de compilá-la, você usaria o comando [`dotnet pack`](dotnet-pack.md) para criar um pacote NuGet (arquivo .nupkg) que contém o código, as informações sobre suas dependências e assim por diante.</span><span class="sxs-lookup"><span data-stu-id="37842-141">After you build it, you use the [`dotnet pack`](dotnet-pack.md) command to create a NuGet package (.nupkg file) that contains your code, information about its dependencies, and so on.</span></span> <span data-ttu-id="37842-142">Você pode atribuir qualquer nome ao pacote, mas o aplicativo dentro dele, o binário da ferramenta de fato, precisa estar em conformidade com a convenção de `dotnet-<command>` para que `dotnet` consiga invocá-lo.</span><span class="sxs-lookup"><span data-stu-id="37842-142">You can give any name to the package, but the application inside, the actual tool binary, has to conform to the convention of `dotnet-<command>` in order for `dotnet` to be able to invoke it.</span></span>

> [!NOTE]
> <span data-ttu-id="37842-143">Em versões pré-RC3 das ferramentas de linha de comando do .NET Core, o comando `dotnet pack` tinha um bug que fazia com que o `runtime.config.json` não fosse adicionado ao pacote com a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="37842-143">In pre-RC3 versions of the .NET Core command-line tools, the `dotnet pack` command had a bug that caused the `runtime.config.json` to not be packed with the tool.</span></span> <span data-ttu-id="37842-144">A falta desse arquivo resulta em erros em tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="37842-144">Lacking that file results in errors at runtime.</span></span> <span data-ttu-id="37842-145">Se você encontrar esse comportamento, certifique-se de atualizar para as ferramentas mais recentes e tente o `dotnet pack` novamente.</span><span class="sxs-lookup"><span data-stu-id="37842-145">If you encounter this behavior, be sure to update to the latest tooling and try the `dotnet pack` again.</span></span>

<span data-ttu-id="37842-146">Como ferramentas são aplicativos portáteis, o usuário que a consume precisa ter a versão das bibliotecas do .NET Core para as quais a biblioteca foi criada para executar a ferramenta.</span><span class="sxs-lookup"><span data-stu-id="37842-146">Since tools are portable applications, the user consuming the tool must have the version of the .NET Core libraries that the tool was built against in order to run the tool.</span></span> <span data-ttu-id="37842-147">Qualquer outra dependência que a ferramenta usa e que não está contida em bibliotecas do .NET Core é restaurada e colocada no cache do NuGet.</span><span class="sxs-lookup"><span data-stu-id="37842-147">Any other dependency that the tool uses and that is not contained within the .NET Core libraries is restored and placed in the NuGet cache.</span></span> <span data-ttu-id="37842-148">Toda a ferramenta é, portanto, executada usando os assemblies de bibliotecas .NET Core, bem como assemblies do cache do NuGet.</span><span class="sxs-lookup"><span data-stu-id="37842-148">The entire tool is, therefore, run using the assemblies from the .NET Core libraries as well as assemblies from the NuGet cache.</span></span>

<span data-ttu-id="37842-149">Esses tipos de ferramentas têm um grafo de dependência completamente separado do grafo de dependência do projeto que as utiliza.</span><span class="sxs-lookup"><span data-stu-id="37842-149">These kinds of tools have a dependency graph that is completely separate from the dependency graph of the project that uses them.</span></span> <span data-ttu-id="37842-150">O processo de restauração restaura primeiro as dependências do projeto e, em seguida, cada uma das ferramentas e suas dependências.</span><span class="sxs-lookup"><span data-stu-id="37842-150">The restore process first restores the project's dependencies and then restores each of the tools and their dependencies.</span></span>

<span data-ttu-id="37842-151">Você pode encontrar exemplos mais sofisticados e diferentes combinações disso no [repositório da CLI do .NET Core](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects).</span><span class="sxs-lookup"><span data-stu-id="37842-151">You can find richer examples and different combinations of this in the [.NET Core CLI repo](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestProjects).</span></span>
<span data-ttu-id="37842-152">Você também pode ver a [implementação das ferramentas utilizadas](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) no mesmo repositório.</span><span class="sxs-lookup"><span data-stu-id="37842-152">You can also see the [implementation of tools used](https://github.com/dotnet/cli/tree/release/2.1/TestAssets/TestPackages) in the same repo.</span></span>

### <a name="custom-targets"></a><span data-ttu-id="37842-153">Destinos personalizados</span><span class="sxs-lookup"><span data-stu-id="37842-153">Custom targets</span></span>
<span data-ttu-id="37842-154">O NuGet tem a capacidade de [criar um pacote com os arquivos de propriedades e destinos personalizados do MSBuild](/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package).</span><span class="sxs-lookup"><span data-stu-id="37842-154">NuGet has the capability to [package custom MSBuild targets and props files](/nuget/create-packages/creating-a-package#including-msbuild-props-and-targets-in-a-package).</span></span> <span data-ttu-id="37842-155">Com a mudança das ferramentas da CLI do .NET Core para usar o MSBuild, o mesmo mecanismo de extensibilidade agora se aplica a projetos .NET Core.</span><span class="sxs-lookup"><span data-stu-id="37842-155">With the move of the .NET Core CLI tools to use MSBuild, the same mechanism of extensibility now applies to .NET Core projects.</span></span> <span data-ttu-id="37842-156">Você deve usar esse tipo de extensibilidade quando desejar estender o processo de build ou quando desejar acessar qualquer um dos artefatos no processo de build, como arquivos gerados, ou desejar inspecionar a configuração pela qual o build é invocado, etc.</span><span class="sxs-lookup"><span data-stu-id="37842-156">You would use this type of extensibility when you want to extend the build process, or when you want to access any of the artifacts in the build process, such as generated files, or you want to inspect the configuration under which the build is invoked, etc.</span></span>

<span data-ttu-id="37842-157">No exemplo a seguir, você pode ver o arquivo de projeto de destino usando a sintaxe `csproj`.</span><span class="sxs-lookup"><span data-stu-id="37842-157">In the following example, you can see the target's project file using the `csproj` syntax.</span></span> <span data-ttu-id="37842-158">Isso instrui ao comando [`dotnet pack`](dotnet-pack.md) o que empacotar, colocando os arquivos de destino e os assemblies na pasta *build* dentro do pacote.</span><span class="sxs-lookup"><span data-stu-id="37842-158">This instructs the [`dotnet pack`](dotnet-pack.md) command what to package, placing the targets files as well as the assemblies into the *build* folder inside the package.</span></span> <span data-ttu-id="37842-159">Observe o elemento `<ItemGroup>` que tem a propriedade `Label` definida como `dotnet pack instructions` e o destino definido abaixo dele.</span><span class="sxs-lookup"><span data-stu-id="37842-159">Notice the `<ItemGroup>` element that has the `Label` property set to `dotnet pack instructions`, and the Target defined beneath it.</span></span>

```xml
<Project Sdk="Microsoft.NET.Sdk">
  <PropertyGroup>
    <Description>Sample Packer</Description>
    <VersionPrefix>0.1.0-preview</VersionPrefix>
    <TargetFramework>netstandard1.3</TargetFramework>
    <DebugType>portable</DebugType>
    <AssemblyName>SampleTargets.PackerTarget</AssemblyName>
  </PropertyGroup>
  <ItemGroup>
    <EmbeddedResource Include="Resources\Pkg\dist-template.xml;compiler\resources\**\*" Exclude="bin\**;obj\**;**\*.xproj;packages\**" />
    <None Include="build\SampleTargets.PackerTarget.targets" />
  </ItemGroup>
  <ItemGroup Label="dotnet pack instructions">
    <Content Include="build\*.targets">
      <Pack>true</Pack>
      <PackagePath>build\</PackagePath>
    </Content>
  </ItemGroup>
  <Target Name="CollectRuntimeOutputs" BeforeTargets="_GetPackageFiles">
    <!-- Collect these items inside a target that runs after build but before packaging. -->
    <ItemGroup>
      <Content Include="$(OutputPath)\*.dll;$(OutputPath)\*.json">
        <Pack>true</Pack>
        <PackagePath>build\</PackagePath>
      </Content>
    </ItemGroup>
  </Target>
  <ItemGroup>
    <PackageReference Include="Microsoft.Extensions.DependencyModel" Version="1.0.1-beta-000933"/>
    <PackageReference Include="Microsoft.Build.Framework" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Microsoft.Build.Utilities.Core" Version="0.1.0-preview-00028-160627" />
    <PackageReference Include="Newtonsoft.Json" Version="9.0.1" />
  </ItemGroup>
  <ItemGroup />
  <PropertyGroup Label="Globals">
    <ProjectGuid>463c66f0-921d-4d34-8bde-7c9d0bffaf7b</ProjectGuid>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(TargetFramework)' == 'netstandard1.3' ">
    <DefineConstants>$(DefineConstants);NETSTANDARD1_3</DefineConstants>
  </PropertyGroup>
  <PropertyGroup Condition=" '$(Configuration)' == 'Release' ">
    <DefineConstants>$(DefineConstants);RELEASE</DefineConstants>
  </PropertyGroup>
</Project>
```

<span data-ttu-id="37842-160">O consumo de destinos personalizados é realizado por meio de um `<PackageReference>` que aponta para o pacote e sua versão dentro do projeto que está sendo estendido.</span><span class="sxs-lookup"><span data-stu-id="37842-160">Consuming custom targets is done by providing a `<PackageReference>` that points to the package and its version inside the project that is being extended.</span></span> <span data-ttu-id="37842-161">Diferentemente das ferramentas, o pacote de destinos personalizados será incluído no fechamento de dependência do projeto de consumo.</span><span class="sxs-lookup"><span data-stu-id="37842-161">Unlike the tools, the custom targets package does get included into the consuming project's dependency closure.</span></span>

<span data-ttu-id="37842-162">Usar o destino personalizado depende exclusivamente como você o configura.</span><span class="sxs-lookup"><span data-stu-id="37842-162">Using the custom target depends solely on how you configure it.</span></span> <span data-ttu-id="37842-163">Como é um destino do MSBuild, ele pode depender de um determinado destino, executar após outro destino e também pode ser invocado manualmente usando o comando `dotnet msbuild /t:<target-name>`.</span><span class="sxs-lookup"><span data-stu-id="37842-163">Since it's an MSBuild target, it can depend on a given target, run after another target and can also be manually invoked using the `dotnet msbuild /t:<target-name>` command.</span></span>

<span data-ttu-id="37842-164">No entanto, se você quiser fornecer uma experiência melhor para seus usuários, poderá combinar ferramentas por projeto e destinos personalizados.</span><span class="sxs-lookup"><span data-stu-id="37842-164">However, if you want to provide a better user experience to your users, you can combine per-project tools and custom targets.</span></span> <span data-ttu-id="37842-165">Nesse cenário, a ferramenta por projeto apenas aceitaria os parâmetros necessários e os converteria para a invocação de [`dotnet msbuild`](dotnet-msbuild.md) necessária, que executaria o destino.</span><span class="sxs-lookup"><span data-stu-id="37842-165">In this scenario, the per-project tool would essentially just accept whatever needed parameters and would translate that into the required [`dotnet msbuild`](dotnet-msbuild.md) invocation that would execute the target.</span></span> <span data-ttu-id="37842-166">Veja um exemplo desse tipo de sinergia no repositório [Exemplos do MVP Summit 2016 Hackathon](https://github.com/dotnet/MVPSummitHackathon2016) do projeto [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer).</span><span class="sxs-lookup"><span data-stu-id="37842-166">You can see a sample of this kind of synergy on the [MVP Summit 2016 Hackathon samples](https://github.com/dotnet/MVPSummitHackathon2016) repo in the [`dotnet-packer`](https://github.com/dotnet/MVPSummitHackathon2016/tree/master/dotnet-packer) project.</span></span>

### <a name="path-based-extensibility"></a><span data-ttu-id="37842-167">Extensibilidade baseada em PATH</span><span class="sxs-lookup"><span data-stu-id="37842-167">PATH-based extensibility</span></span>
<span data-ttu-id="37842-168">A extensibilidade do PATH geralmente é usada para computadores de desenvolvimento em que você precisa de uma ferramenta que abrange conceitualmente mais de um único projeto.</span><span class="sxs-lookup"><span data-stu-id="37842-168">PATH-based extensibility is usually used for development machines where you need a tool that conceptually covers more than a single project.</span></span> <span data-ttu-id="37842-169">A principal desvantagem desse mecanismo de extensão é que ele está vinculado ao computador no qual a ferramenta existe.</span><span class="sxs-lookup"><span data-stu-id="37842-169">The main drawback of this extension mechanism is that it's tied to the machine where the tool exists.</span></span> <span data-ttu-id="37842-170">Se você precisar dela em outro computador, precisará implantá-la.</span><span class="sxs-lookup"><span data-stu-id="37842-170">If you need it on another machine, you would have to deploy it.</span></span>

<span data-ttu-id="37842-171">Esse padrão de extensibilidade do conjunto de ferramentas da CLI é muito simples.</span><span class="sxs-lookup"><span data-stu-id="37842-171">This pattern of CLI toolset extensibility is very simple.</span></span> <span data-ttu-id="37842-172">Conforme abordado na [Visão geral da CLI do .NET Core](index.md), o driver `dotnet` pode executar qualquer comando nomeado segundo a convenção `dotnet-<command>`.</span><span class="sxs-lookup"><span data-stu-id="37842-172">As covered in the [.NET Core CLI overview](index.md), `dotnet` driver can run any command that is named after the `dotnet-<command>` convention.</span></span> <span data-ttu-id="37842-173">A lógica de resolução padrão primeiro investiga os vários locais e finalmente volta para o PATH do sistema.</span><span class="sxs-lookup"><span data-stu-id="37842-173">The default resolution logic first probes several locations and finally falls back to the system PATH.</span></span> <span data-ttu-id="37842-174">Se o comando solicitado existir no PATH do sistema e for um binário que pode ser invocado, o driver `dotnet` o invocará.</span><span class="sxs-lookup"><span data-stu-id="37842-174">If the requested command exists in the system PATH and is a binary that can be invoked, `dotnet` driver will invoke it.</span></span>

<span data-ttu-id="37842-175">O arquivo deve ser executável.</span><span class="sxs-lookup"><span data-stu-id="37842-175">The file must be executable.</span></span> <span data-ttu-id="37842-176">Em sistemas Unix, isso significa tudo que tiver o conjunto de bits execute por meio de `chmod +x`.</span><span class="sxs-lookup"><span data-stu-id="37842-176">On Unix systems, this means anything that has the execute bit set via `chmod +x`.</span></span> <span data-ttu-id="37842-177">No Windows, você pode usar arquivos *cmd*.</span><span class="sxs-lookup"><span data-stu-id="37842-177">On Windows, you can use *cmd* files.</span></span>

<span data-ttu-id="37842-178">Vamos analisar uma implementação muito simples de uma ferramenta “Olá, Mundo”.</span><span class="sxs-lookup"><span data-stu-id="37842-178">Let's take a look at the very simple implementation of a "Hello World" tool.</span></span> <span data-ttu-id="37842-179">Usaremos `bash` e `cmd` no Windows.</span><span class="sxs-lookup"><span data-stu-id="37842-179">We will use both `bash` and `cmd` on Windows.</span></span>
<span data-ttu-id="37842-180">O comando a seguir simplesmente ecoará “Olá, Mundo” para o console.</span><span class="sxs-lookup"><span data-stu-id="37842-180">The following command will simply echo "Hello World" to the console.</span></span>

```bash
#!/bin/bash

echo "Hello World!"
```

```cmd
echo "Hello World"
```

<span data-ttu-id="37842-181">No macOS, podemos eliminar esse script como `dotnet-hello` e definir o bit executável com `chmod +x dotnet-hello`.</span><span class="sxs-lookup"><span data-stu-id="37842-181">On macOS, we can save this script as `dotnet-hello` and set its executable bit with `chmod +x dotnet-hello`.</span></span> <span data-ttu-id="37842-182">Podemos então criar um link simbólico para ele em `/usr/local/bin` usando o comando `ln -s <full_path>/dotnet-hello /usr/local/bin/`.</span><span class="sxs-lookup"><span data-stu-id="37842-182">We can then create a symbolic link to it in `/usr/local/bin` using the command `ln -s <full_path>/dotnet-hello /usr/local/bin/`.</span></span> <span data-ttu-id="37842-183">Isso tornará possível invocar o comando usando a sintaxe `dotnet hello`.</span><span class="sxs-lookup"><span data-stu-id="37842-183">This will make it possible to invoke the command using the `dotnet hello` syntax.</span></span>

<span data-ttu-id="37842-184">No Windows, podemos eliminar esse script como `dotnet-hello.cmd` e colocá-lo em um local que está em um caminho do sistema (ou você pode adicioná-lo a uma pasta que já está no caminho).</span><span class="sxs-lookup"><span data-stu-id="37842-184">On Windows, we can save this script as `dotnet-hello.cmd` and put it in a location that is in a system path (or you can add it to a folder that is already in the path).</span></span> <span data-ttu-id="37842-185">Depois disso, você pode simplesmente usar `dotnet hello` para executar este exemplo.</span><span class="sxs-lookup"><span data-stu-id="37842-185">After this, you can just use `dotnet hello` to run this example.</span></span>
