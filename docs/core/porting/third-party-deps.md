---
title: Portabilidade para .NET Core – Analisar as dependências de terceiros
description: Aprenda a analisar as dependências de terceiros para fazer a portabilidade do seu projeto do .NET Framework para o .NET Core.
author: cartermp
ms.author: mairaw
ms.date: 02/15/2018
ms.openlocfilehash: 06d8d36d8369680c54af4d16513b2b871b57079c
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/16/2018
ms.locfileid: "45679265"
---
# <a name="analyze-your-third-party-dependencies"></a><span data-ttu-id="bcf67-103">Analisar as dependências de terceiros</span><span class="sxs-lookup"><span data-stu-id="bcf67-103">Analyze your third-party dependencies</span></span>

<span data-ttu-id="bcf67-104">Se você tem a intenção de portar seu código para o .NET Core ou o .NET Standard, a primeira etapa no processo de portabilidade é entender as dependências de terceiros.</span><span class="sxs-lookup"><span data-stu-id="bcf67-104">If you're looking to port your code to .NET Core or .NET Standard, the first step in the porting process is to understand your third-party dependencies.</span></span> <span data-ttu-id="bcf67-105">As dependências de terceiros são [pacotes NuGet](#analyze-referenced-nuget-packages-on-your-project) ou [DLLs](#analyze-dependencies-that-arent-nuget-packages) aos quais você faz referência em seu projeto.</span><span class="sxs-lookup"><span data-stu-id="bcf67-105">Third-party dependencies are either [NuGet packages](#analyze-referenced-nuget-packages-on-your-project) or [DLLs](#analyze-dependencies-that-arent-nuget-packages) you're referencing in your project.</span></span> <span data-ttu-id="bcf67-106">Avalie cada dependência e desenvolva um plano de contingência para as dependências que não são compatíveis com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bcf67-106">Evaluate each dependency and develop a contingency plan for the dependencies that aren't compatible with .NET Core.</span></span> <span data-ttu-id="bcf67-107">Este artigo mostra como determinar se a dependência é compatível com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bcf67-107">This article shows you how to determine if the dependency is compatible with .NET Core.</span></span>

## <a name="analyze-referenced-nuget-packages-in-your-project"></a><span data-ttu-id="bcf67-108">Analisar os pacotes NuGet referenciados em seu projeto</span><span class="sxs-lookup"><span data-stu-id="bcf67-108">Analyze referenced NuGet packages in your project</span></span>

<span data-ttu-id="bcf67-109">Se você estiver fazendo referência a pacotes NuGet em seu projeto, é necessário verificar se eles são compatíveis com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bcf67-109">If you're referencing NuGet packages in your project, you need to verify if they're compatible with .NET Core.</span></span>
<span data-ttu-id="bcf67-110">Há duas maneiras de fazer isso:</span><span class="sxs-lookup"><span data-stu-id="bcf67-110">There are two ways to accomplish that:</span></span>

* <span data-ttu-id="bcf67-111">[Usando o aplicativo Explorador de Pacotes NuGet](#analyze-nuget-packages-using-nuget-package-explorer) (o método mais confiável).</span><span class="sxs-lookup"><span data-stu-id="bcf67-111">[Using the NuGet Package Explorer app](#analyze-nuget-packages-using-nuget-package-explorer) (the most reliable method).</span></span>
* <span data-ttu-id="bcf67-112">[Usando o site nuget.org](#analyze-nuget-packages-using-nugetorg).</span><span class="sxs-lookup"><span data-stu-id="bcf67-112">[Using the nuget.org site](#analyze-nuget-packages-using-nugetorg).</span></span>

<span data-ttu-id="bcf67-113">Depois de analisar os pacotes, se eles não forem compatíveis com o .NET Core e destinarem-se apenas ao .NET Framework, você poderá verificar se o [modo de compatibilidade do .NET Framework](#net-framework-compatibility-mode) pode ajudar no processo de portabilidade.</span><span class="sxs-lookup"><span data-stu-id="bcf67-113">After analyzing the packages, if they're not compatible with .NET Core and only target .NET Framework, you can check if the [.NET Framework compatibility mode](#net-framework-compatibility-mode) can help with your porting process.</span></span>

### <a name="analyze-nuget-packages-using-nuget-package-explorer"></a><span data-ttu-id="bcf67-114">Analisar pacotes NuGet usando o Explorador de Pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="bcf67-114">Analyze NuGet packages using NuGet Package Explorer</span></span>

<span data-ttu-id="bcf67-115">Um pacote NuGet é um conjunto de pastas que contêm assemblies específicos de plataforma.</span><span class="sxs-lookup"><span data-stu-id="bcf67-115">A NuGet package is itself a set of folders that contain platform-specific assemblies.</span></span> <span data-ttu-id="bcf67-116">Portanto, você precisa verificar se há uma pasta que contém um assembly compatível dentro do pacote.</span><span class="sxs-lookup"><span data-stu-id="bcf67-116">So you need to check if there's a folder that contains a compatible assembly inside the package.</span></span>

<span data-ttu-id="bcf67-117">A maneira mais fácil de inspecionar a pastas do pacote NuGet é usar a ferramenta [Explorador de Pacotes NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer).</span><span class="sxs-lookup"><span data-stu-id="bcf67-117">The easiest way to inspect NuGet Package folders is to use the [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) tool.</span></span> <span data-ttu-id="bcf67-118">Depois da instalação, use as seguintes etapas para ver os nomes de pasta:</span><span class="sxs-lookup"><span data-stu-id="bcf67-118">After installing it, use the following steps to see the folder names:</span></span>

1. <span data-ttu-id="bcf67-119">Abra o Explorador de Pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="bcf67-119">Open the NuGet Package Explorer.</span></span>
2. <span data-ttu-id="bcf67-120">Clique em **Abrir pacote de feed online**.</span><span class="sxs-lookup"><span data-stu-id="bcf67-120">Click **Open package from online feed**.</span></span>
3. <span data-ttu-id="bcf67-121">Pesquise o nome do pacote.</span><span class="sxs-lookup"><span data-stu-id="bcf67-121">Search for the name of the package.</span></span>
4. <span data-ttu-id="bcf67-122">Selecione o nome do pacote nos resultados da pesquisa e clique em **abrir**.</span><span class="sxs-lookup"><span data-stu-id="bcf67-122">Select the package name from the search results and click **open**.</span></span>
5. <span data-ttu-id="bcf67-123">Expanda a pasta *lib* no lado direito e observe os nomes de pasta.</span><span class="sxs-lookup"><span data-stu-id="bcf67-123">Expand the *lib* folder on the right-hand side and look at folder names.</span></span>

<span data-ttu-id="bcf67-124">Procure uma pasta com qualquer um dos seguintes nomes:</span><span class="sxs-lookup"><span data-stu-id="bcf67-124">Look for a folder with any of the following names:</span></span>

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netstandard2.0
netcoreapp1.0
netcoreapp1.1
netcoreapp2.0
netcoreapp2.1
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

<span data-ttu-id="bcf67-125">Esses valores são [TFMs (Monikers da Estrutura de Destino)](../../standard/frameworks.md), que são mapeados para versões do [.NET Standard](../../standard/net-standard.md), .NET Core e perfis de PCL (Biblioteca de Classes Portátil) tradicionais que são compatíveis com .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bcf67-125">These values are the [Target Framework Monikers (TFMs)](../../standard/frameworks.md) that map to versions of the [.NET Standard](../../standard/net-standard.md), .NET Core, and traditional Portable Class Library (PCL) profiles that are compatible with .NET Core.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="bcf67-126">Ao analisar os TFMs compatíveis com um pacote, observe que o `netcoreapp*`, embora compatível, serve somente para projetos do .NET Core e não para projetos do .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="bcf67-126">When looking at the TFMs that a package supports, note that `netcoreapp*`, while compatible, is for .NET Core projects only and not for .NET Standard projects.</span></span>
> <span data-ttu-id="bcf67-127">Uma biblioteca destinada somente a `netcoreapp*` e não a `netstandard*` só pode ser consumida por outros aplicativos do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bcf67-127">A library that only targets `netcoreapp*` and not `netstandard*` can only be consumed by other .NET Core apps.</span></span>

<span data-ttu-id="bcf67-128">Também há alguns TFMs herdados usados em versões de pré-lançamento do .NET Core que podem ser compatíveis:</span><span class="sxs-lookup"><span data-stu-id="bcf67-128">There are also some legacy TFMs used in pre-release versions of .NET Core that may also be compatible:</span></span>

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

<span data-ttu-id="bcf67-129">Embora esses TMFs provavelmente funcionem com o seu código, não há nenhuma garantia de compatibilidade.</span><span class="sxs-lookup"><span data-stu-id="bcf67-129">While these TFMs likely work with your code, there is no guarantee of compatibility.</span></span> <span data-ttu-id="bcf67-130">Pacotes com esses TFMs foram compilados com pacotes de pré-lançamento do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bcf67-130">Packages with these TFMs were built with pre-release .NET Core packages.</span></span> <span data-ttu-id="bcf67-131">Anote quando (ou se) os pacotes que usam esses TFMs serão atualizados para tornarem-se baseados em .NET Standard.</span><span class="sxs-lookup"><span data-stu-id="bcf67-131">Take note of when (or if) packages using these TFMs are updated to be .NET Standard-based.</span></span>

> [!NOTE]
> <span data-ttu-id="bcf67-132">Para usar um pacote direcionado a uma PCL tradicional ou destinado ao .NET Core de pré-lançamento, você deve usar o elemento `PackageTargetFallback` do MSBuild no seu arquivo de projeto.</span><span class="sxs-lookup"><span data-stu-id="bcf67-132">To use a package targeting a traditional PCL or pre-release .NET Core target, you must use the `PackageTargetFallback` MSBuild element in your project file.</span></span>
> <span data-ttu-id="bcf67-133">Para obter mais informações sobre este elemento do MSBuild, consulte [`PackageTargetFallback`](../tools/csproj.md#packagetargetfallback).</span><span class="sxs-lookup"><span data-stu-id="bcf67-133">For more information about this MSBuild element, see [`PackageTargetFallback`](../tools/csproj.md#packagetargetfallback).</span></span>

### <a name="analyze-nuget-packages-using-nugetorg"></a><span data-ttu-id="bcf67-134">Analisar pacotes NuGet usando nuget.org</span><span class="sxs-lookup"><span data-stu-id="bcf67-134">Analyze NuGet packages using nuget.org</span></span>

<span data-ttu-id="bcf67-135">Como alternativa, você pode ver os TFMs que são compatíveis com cada pacote em [nuget.org](https://www.nuget.org/), na seção **Dependências** da página do pacote.</span><span class="sxs-lookup"><span data-stu-id="bcf67-135">Alternatively, you can see the TFMs that each package supports on [nuget.org](https://www.nuget.org/) under the **Dependencies** section of the package page.</span></span>

<span data-ttu-id="bcf67-136">Embora o uso do site seja um método mais fácil para verificar a compatibilidade, as informações de **Dependências** não estão disponíveis no site para todos os pacotes.</span><span class="sxs-lookup"><span data-stu-id="bcf67-136">Although using the site is an easier method to verify the compatibility, **Dependencies** information is not available on the site for all packages.</span></span>

### <a name="net-framework-compatibility-mode"></a><span data-ttu-id="bcf67-137">Modo de compatibilidade do .NET framework</span><span class="sxs-lookup"><span data-stu-id="bcf67-137">.NET Framework compatibility mode</span></span>

<span data-ttu-id="bcf67-138">Depois de analisar os pacotes NuGet, você pode chegar à conclusão de que eles se destinam apenas ao .NET Framework, como a maioria dos pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="bcf67-138">After analyzing the NuGet packages, you might find that they only target the .NET Framework, as most NuGet packages do.</span></span>

<span data-ttu-id="bcf67-139">O modo de compatibilidade do .NET Framework foi introduzido a partir do .NET Standard 2.0.</span><span class="sxs-lookup"><span data-stu-id="bcf67-139">Starting with .NET Standard 2.0, the .NET Framework compatibility mode was introduced.</span></span> <span data-ttu-id="bcf67-140">Esse modo de compatibilidade permite que os projetos do .NET Standard e do .NET Core referenciem bibliotecas do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="bcf67-140">This compatibility mode allows .NET Standard and .NET Core projects to reference .NET Framework libraries.</span></span> <span data-ttu-id="bcf67-141">Fazer referência a bibliotecas do .NET Framework não funciona para todos os projetos, como nos casos em que a biblioteca usa APIs do WPF (Windows Presentation Foundation), mas isso desbloqueia muitos cenários de portabilidade.</span><span class="sxs-lookup"><span data-stu-id="bcf67-141">Referencing .NET Framework libraries doesn't work for all projects, such as if the library uses Windows Presentation Foundation (WPF) APIs, but it does unblock many porting scenarios.</span></span>

<span data-ttu-id="bcf67-142">Ao fazer referência a pacotes NuGet que se destinam ao .NET Framework em seu projeto, como [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), você receberá um aviso de fallback do pacote ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) semelhante ao exemplo a seguir:</span><span class="sxs-lookup"><span data-stu-id="bcf67-142">When you reference NuGet packages that target the .NET Framework in your project, such as [Huitian.PowerCollections](https://www.nuget.org/packages/Huitian.PowerCollections), you get a package fallback warning ([NU1701](/nuget/reference/errors-and-warnings#nu1701)) similar to the following example:</span></span>

`NU1701: Package ‘Huitian.PowerCollections 1.0.0’ was restored using ‘.NETFramework,Version=v4.6.1’ instead of the project target framework ‘.NETStandard,Version=v2.0’. This package may not be fully compatible with your project.`

<span data-ttu-id="bcf67-143">Esse aviso será exibido quando você adicionar o pacote e sempre que você compilar, para que você não se esqueça de testar o pacote com o projeto.</span><span class="sxs-lookup"><span data-stu-id="bcf67-143">That warning is displayed when you add the package and every time you build to make sure you test that package with your project.</span></span> <span data-ttu-id="bcf67-144">Se o projeto está funcionando como esperado, você pode suprimir esse aviso, editando as propriedades do pacote no Visual Studio ou editando manualmente o arquivo de projeto em seu editor de código favorito.</span><span class="sxs-lookup"><span data-stu-id="bcf67-144">If your project is working as expected, you can suppress that warning by editing the package properties in Visual Studio or by manually editing the project file in your favorite code editor.</span></span>

<span data-ttu-id="bcf67-145">Para suprimir o aviso editando o arquivo de projeto, localize a entrada `PackageReference` do pacote em que você deseja suprimir o aviso e adicione o atributo `NoWarn`.</span><span class="sxs-lookup"><span data-stu-id="bcf67-145">To suppress the warning by editing the project file, find the `PackageReference` entry for the package you want to suppress the warning for and add the `NoWarn` attribute.</span></span> <span data-ttu-id="bcf67-146">O atributo `NoWarn` aceita uma lista separada por vírgulas de todas as IDs de aviso.</span><span class="sxs-lookup"><span data-stu-id="bcf67-146">The `NoWarn` attribute accepts a comma-separated list of all the warning IDs.</span></span> <span data-ttu-id="bcf67-147">O exemplo a seguir mostra como suprimir o aviso `NU1701` do pacote `Huitian.PowerCollections` por meio da edição manual do arquivo de projeto:</span><span class="sxs-lookup"><span data-stu-id="bcf67-147">The following example shows how to suppress the `NU1701` warning for the `Huitian.PowerCollections` package by editing your project file manually:</span></span>

```xml
<ItemGroup>
  <PackageReference Include="Huitian.PowerCollections" Version="1.0.0" NoWarn="NU1701" />
</ItemGroup>
```

<span data-ttu-id="bcf67-148">Para obter mais informações sobre como suprimir avisos do compilador no Visual Studio, consulte [Suprimir avisos de pacotes NuGet](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages).</span><span class="sxs-lookup"><span data-stu-id="bcf67-148">For more information on how to suppress compiler warnings in Visual Studio, see [Suppressing warnings for NuGet packages](/visualstudio/ide/how-to-suppress-compiler-warnings#suppressing-warnings-for-nuget-packages).</span></span>

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a><span data-ttu-id="bcf67-149">O que fazer quando a dependência de pacote NuGet não é executada no .NET Core</span><span class="sxs-lookup"><span data-stu-id="bcf67-149">What to do when your NuGet package dependency doesn't run on .NET Core</span></span>

<span data-ttu-id="bcf67-150">Há algumas coisas que você pode fazer se um pacote NuGet do qual você depende não for executado no .NET Core:</span><span class="sxs-lookup"><span data-stu-id="bcf67-150">There are a few things you can do if a NuGet package you depend on doesn't run on .NET Core:</span></span>

1. <span data-ttu-id="bcf67-151">Se o projeto for um software livre e estiver hospedado em algum lugar como o GitHub, você poderá entrar em contato diretamente com os desenvolvedores.</span><span class="sxs-lookup"><span data-stu-id="bcf67-151">If the project is open source and hosted somewhere like GitHub, you can engage the developers directly.</span></span>
2. <span data-ttu-id="bcf67-152">Você pode entrar em contato diretamente com o autor no [nuget.org](https://www.nuget.org/). Pesquise o pacote e clique em **Entrar em contato com os proprietários** no lado esquerdo da página do pacote.</span><span class="sxs-lookup"><span data-stu-id="bcf67-152">You can contact the author directly on [nuget.org](https://www.nuget.org/). Search for the package and click **Contact Owners** on the left-hand side of the package's page.</span></span>
3. <span data-ttu-id="bcf67-153">Você pode pesquisar outro pacote que seja executado no .NET Core e realize a mesma tarefa que o pacote que você estava usando.</span><span class="sxs-lookup"><span data-stu-id="bcf67-153">You can search for another package that runs on .NET Core that accomplishes the same task as the package you were using.</span></span>
4. <span data-ttu-id="bcf67-154">Você pode tentar escrever por conta própria o código do que o pacote estava fazendo.</span><span class="sxs-lookup"><span data-stu-id="bcf67-154">You can attempt to write the code the package was doing yourself.</span></span>
5. <span data-ttu-id="bcf67-155">Você pode eliminar a dependência do pacote alterando a funcionalidade do aplicativo, pelo menos até que uma versão compatível do pacote fique disponível.</span><span class="sxs-lookup"><span data-stu-id="bcf67-155">You could eliminate the dependency on the package by changing the functionality of your app, at least until a compatible version of the package becomes available.</span></span>

<span data-ttu-id="bcf67-156">Lembre-se que os mantenedores de projetos de software livre e os editores de pacote NuGet geralmente são voluntários.</span><span class="sxs-lookup"><span data-stu-id="bcf67-156">Remember that open-source project maintainers and NuGet package publishers are often volunteers.</span></span> <span data-ttu-id="bcf67-157">Elas contribuem porque se importam com um determinado domínio, fazem-no gratuitamente e geralmente têm um trabalho diferente durante dia.</span><span class="sxs-lookup"><span data-stu-id="bcf67-157">They contribute because they care about a given domain, do it for free, and often have a different daytime job.</span></span> <span data-ttu-id="bcf67-158">Portanto, lembre-se disso ao entrar em contato com eles para solicitar suporte para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bcf67-158">So be mindful of that when contacting them to ask for .NET Core support.</span></span>

<span data-ttu-id="bcf67-159">Se você não puder resolver o problema com nenhuma das opções acima, talvez seja necessário realizar a portabilidade para o .NET Core posteriormente.</span><span class="sxs-lookup"><span data-stu-id="bcf67-159">If you can't resolve your issue with any of the above, you may have to port to .NET Core at a later date.</span></span>

<span data-ttu-id="bcf67-160">A equipe do .NET gostaria de saber quais bibliotecas são as mais importantes para compatibilidade com o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bcf67-160">The .NET Team would like to know which libraries are the most important to support with .NET Core.</span></span> <span data-ttu-id="bcf67-161">Você pode enviar um email para dotnet@microsoft.com, informando sobre as bibliotecas que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="bcf67-161">You can send an email to dotnet@microsoft.com about the libraries you'd like to use.</span></span>

## <a name="analyze-dependencies-that-arent-nuget-packages"></a><span data-ttu-id="bcf67-162">Analisar dependências que não são pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="bcf67-162">Analyze dependencies that aren't NuGet packages</span></span>

<span data-ttu-id="bcf67-163">Você pode ter uma dependência que não seja um pacote NuGet, tal como uma DLL no sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="bcf67-163">You may have a dependency that isn't a NuGet package, such as a DLL in the file system.</span></span> <span data-ttu-id="bcf67-164">A única maneira de determinar a portabilidade dessa dependência é executar a ferramenta [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport).</span><span class="sxs-lookup"><span data-stu-id="bcf67-164">The only way to determine the portability of that dependency is to run the [.NET Portability Analyzer](https://github.com/Microsoft/dotnet-apiport) tool.</span></span> <span data-ttu-id="bcf67-165">A ferramenta pode analisar assemblies direcionados ao .NET Framework e identificar as APIs que não são portáteis para outras plataformas do .NET, como o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="bcf67-165">The tool can analyze assemblies that target the .NET Framework and identify APIs that aren't portable to other .NET platforms such as .NET Core.</span></span> <span data-ttu-id="bcf67-166">Você pode executar a ferramenta como um aplicativo de console ou uma [extensão do Visual Studio](../../standard/analyzers/portability-analyzer.md).</span><span class="sxs-lookup"><span data-stu-id="bcf67-166">You can run the tool as a console application or as a [Visual Studio extension](../../standard/analyzers/portability-analyzer.md).</span></span>

## <a name="next-steps"></a><span data-ttu-id="bcf67-167">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="bcf67-167">Next steps</span></span>

<span data-ttu-id="bcf67-168">Se você estiver portando uma biblioteca, consulte [Portando suas bibliotecas](libraries.md).</span><span class="sxs-lookup"><span data-stu-id="bcf67-168">If you're porting a library, check out [Porting your Libraries](libraries.md).</span></span>
