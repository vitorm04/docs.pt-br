---
title: "Portabilidade para .NET Core – Analisar suas dependências de terceiros"
description: "Portabilidade para .NET Core – Analisar suas dependências de terceiros"
keywords: .NET, .NET Core
author: cartermp
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: b446e9e0-72f6-48f6-92c6-70ad0ce3f86a
ms.openlocfilehash: a074978f2817abafa7b8a9fefe7c67c9c52195b3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="porting-to-net-core---analyzing-your-third-party-party-dependencies"></a><span data-ttu-id="344ae-104">Portabilidade para .NET Core – Analisar suas dependências de terceiros</span><span class="sxs-lookup"><span data-stu-id="344ae-104">Porting to .NET Core - Analyzing your Third-Party Party Dependencies</span></span>

<span data-ttu-id="344ae-105">A primeira etapa no processo de portabilidade é entender suas dependências de terceiros.</span><span class="sxs-lookup"><span data-stu-id="344ae-105">The first step in the porting process is to understand your third party dependencies.</span></span>  <span data-ttu-id="344ae-106">Você precisa descobrir quais delas, se houver, ainda não são executadas no .NET Core e desenvolver um plano de contingência para elas.</span><span class="sxs-lookup"><span data-stu-id="344ae-106">You need to figure out which of them, if any, don't yet run on .NET Core, and develop a contingency plan for those which don't run on .NET Core.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="344ae-107">Pré-requisitos</span><span class="sxs-lookup"><span data-stu-id="344ae-107">Prerequisites</span></span>

<span data-ttu-id="344ae-108">Este artigo supõe que você está usando o Windows e o Visual Studio, e que você tem um código que é executado no .NET Framework atualmente.</span><span class="sxs-lookup"><span data-stu-id="344ae-108">This article will assume you are using Windows and Visual Studio, and that you have code which runs on the .NET Framework today.</span></span>

## <a name="analyzing-nuget-packages"></a><span data-ttu-id="344ae-109">Analisando Pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="344ae-109">Analyzing NuGet Packages</span></span>

<span data-ttu-id="344ae-110">É muito fácil analisar pacotes NuGet para portabilidade.</span><span class="sxs-lookup"><span data-stu-id="344ae-110">Analyzing NuGet packages for portability is very easy.</span></span>  <span data-ttu-id="344ae-111">Como um pacote NuGet é essencialmente um conjunto de pastas que contêm assemblies específicos de plataforma, basta você verificar se há uma pasta que contém um assembly .NET Core.</span><span class="sxs-lookup"><span data-stu-id="344ae-111">Because a NuGet package is itself a set of folders which contain platform-specific assemblies, all you have to do is check to see if there is a folder which contains a .NET Core assembly.</span></span>

<span data-ttu-id="344ae-112">Inspecionar as pastas do pacote NuGet é mais fácil com a ferramenta [Explorador de Pacotes NuGet](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer).</span><span class="sxs-lookup"><span data-stu-id="344ae-112">Inspecting NuGet Package folders is easiest with the [NuGet Package Explorer](https://github.com/NuGetPackageExplorer/NuGetPackageExplorer) tool.</span></span>  <span data-ttu-id="344ae-113">Veja como fazer isso.</span><span class="sxs-lookup"><span data-stu-id="344ae-113">Here's how to do it.</span></span>

1. <span data-ttu-id="344ae-114">Baixe e abra o Explorador de Pacotes NuGet.</span><span class="sxs-lookup"><span data-stu-id="344ae-114">Download and open the NuGet Package Explorer.</span></span>
2. <span data-ttu-id="344ae-115">Clique em "Abrir pacote de feed online".</span><span class="sxs-lookup"><span data-stu-id="344ae-115">Click "Open package from online feed".</span></span>
3. <span data-ttu-id="344ae-116">Pesquise o nome do pacote.</span><span class="sxs-lookup"><span data-stu-id="344ae-116">Search for the name of the package.</span></span>
4. <span data-ttu-id="344ae-117">Expanda a pasta "lib" no lado direito e observe os nomes de pasta.</span><span class="sxs-lookup"><span data-stu-id="344ae-117">Expand the "lib" folder on the right-hand side and look at folder names.</span></span>

<span data-ttu-id="344ae-118">Você também pode ver o que tem suporte em um pacote em [nuget.org](https://www.nuget.org/) na seção **Dependências** da página desse pacote.</span><span class="sxs-lookup"><span data-stu-id="344ae-118">You can also see what a package supports on [nuget.org](https://www.nuget.org/) under the **Dependencies** section of the page for that package.</span></span>

<span data-ttu-id="344ae-119">Em ambos os casos, você precisará procurar uma pasta ou entrada em [nuget.org](https://www.nuget.org/) com um dos seguintes nomes:</span><span class="sxs-lookup"><span data-stu-id="344ae-119">In either case, you'll need to look for a folder or entry on [nuget.org](https://www.nuget.org/) with any of the following names:</span></span>

```
netstandard1.0
netstandard1.1
netstandard1.2
netstandard1.3
netstandard1.4
netstandard1.5
netstandard1.6
netcoreapp1.0
portable-net45-win8
portable-win8-wpa8
portable-net451-win81
portable-net45-win8-wpa8-wpa81
```

<span data-ttu-id="344ae-120">Esses são TFMs (Monikers da Estrutura de Destino), que são mapeados para versões do [.NET Standard](../../standard/net-standard.md) e perfis de PCL (Biblioteca de Classes Portátil) tradicionais, os quais são compatíveis com .NET Core.</span><span class="sxs-lookup"><span data-stu-id="344ae-120">These are the Target Framework Monikers (TFM) which map to versions of the [.NET Standard](../../standard/net-standard.md) and traditional Portable Class Library (PCL) profiles which are compatible with .NET Core.</span></span>  <span data-ttu-id="344ae-121">Observe que `netcoreapp1.0`, embora seja compatível, ele se destina a aplicativos e não a bibliotecas.</span><span class="sxs-lookup"><span data-stu-id="344ae-121">Note that `netcoreapp1.0`, while compatible, is for applications and not libraries.</span></span>  <span data-ttu-id="344ae-122">Embora não haja nada de errado em usar uma biblioteca baseada em `netcoreapp1.0`, ela pode não destinar-se a nada *além* de consumir outros aplicativos `netcoreapp1.0`.</span><span class="sxs-lookup"><span data-stu-id="344ae-122">Although there's nothing wrong with using a library which is `netcoreapp1.0`-based, that library may not be intended for anything *other* than consumption by other `netcoreapp1.0` applications.</span></span>

<span data-ttu-id="344ae-123">Também há alguns TFMs herdados usados em versões de pré-lançamento do .NET Core que podem ser compatíveis:</span><span class="sxs-lookup"><span data-stu-id="344ae-123">There are also some legacy TFMs used in pre-release versions of .NET Core that may also be compatible:</span></span>

```
dnxcore50
dotnet5.0
dotnet5.1
dotnet5.2
dotnet5.3
dotnet5.4
dotnet5.5
```

<span data-ttu-id="344ae-124">**Embora elas provavelmente funcionarão com o seu código, não há nenhuma garantia de compatibilidade**.</span><span class="sxs-lookup"><span data-stu-id="344ae-124">**While these will likely work with your code, there is no guarantee of compatibility**.</span></span>  <span data-ttu-id="344ae-125">Pacotes com esses TFMs foram compilados com pacotes de pré-lançamento do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="344ae-125">Packages with these TFMs were built with pre-release .NET Core packages.</span></span>  <span data-ttu-id="344ae-126">Tome nota de quando (se ocorrer) tais pacotes forem atualizados para serem baseados em `netstandard`.</span><span class="sxs-lookup"><span data-stu-id="344ae-126">Take note of when (or if) packages like this are updated to be `netstandard`-based.</span></span>

> [!NOTE]
> <span data-ttu-id="344ae-127">Para usar um pacote direcionado para uma PCL tradicional ou para um destino .NET Core pré-lançamento, você deve usar a diretiva `imports` no seu arquivo `project.json`.</span><span class="sxs-lookup"><span data-stu-id="344ae-127">To use a package targeting a traditional PCL or pre-release .NET Core target, you must use the `imports` directive in your `project.json` file.</span></span>

### <a name="what-to-do-when-your-nuget-package-dependency-doesnt-run-on-net-core"></a><span data-ttu-id="344ae-128">O que fazer quando a dependência de pacote NuGet não é executada no .NET Core</span><span class="sxs-lookup"><span data-stu-id="344ae-128">What to do when your NuGet package dependency doesn't run on .NET Core</span></span>

<span data-ttu-id="344ae-129">Há algumas coisas que você pode fazer se um pacote NuGet do qual você depende não for executado no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="344ae-129">There are a few things you can do if a NuGet package you depend on won't run on .NET Core.</span></span>

1. <span data-ttu-id="344ae-130">Se o projeto for um software livre e estiver hospedados em algum lugar como o GitHub, você poderá entrar em contato com os desenvolvedores diretamente.</span><span class="sxs-lookup"><span data-stu-id="344ae-130">If the project is open source and hosted somewhere like GitHub, you can engage the developer(s) directly.</span></span>
2. <span data-ttu-id="344ae-131">Você pode contatar o autor diretamente em [nuget.org](https://www.nuget.org/) procurando o pacote e clicando em "Entre em contato com os proprietários" no lado esquerdo da página do pacote.</span><span class="sxs-lookup"><span data-stu-id="344ae-131">You can contact the author directly on [nuget.org](https://www.nuget.org/) by searching for the package and clicking "Contact Owners" on the left hand side of the package's page.</span></span>
3. <span data-ttu-id="344ae-132">Você pode procurar por outro pacote que é executado no .NET Core que realiza a mesma tarefa do pacote que você estava usando.</span><span class="sxs-lookup"><span data-stu-id="344ae-132">You can look for another package that runs on .NET Core which accomplishes the same task as the package you were using.</span></span>
4. <span data-ttu-id="344ae-133">Você pode tentar escrever por conta própria o código do que o pacote estava fazendo.</span><span class="sxs-lookup"><span data-stu-id="344ae-133">You can attempt to write the code the package was doing yourself.</span></span>
5. <span data-ttu-id="344ae-134">Você pode eliminar a dependência do pacote alterando a funcionalidade do aplicativo, pelo menos até que uma versão compatível do pacote fique disponível.</span><span class="sxs-lookup"><span data-stu-id="344ae-134">You could eliminate the dependency on the package by changing the functionality of your app, at least until a compatible version of the package becomes available.</span></span>

<span data-ttu-id="344ae-135">Lembre-se que mantenedores do projeto de software livre e editores de pacotes NuGet costumam ser voluntários que contribuem porque se importam com um determinado domínio, fazendo-o gratuitamente e geralmente têm um emprego regular diferente.</span><span class="sxs-lookup"><span data-stu-id="344ae-135">Please remember that open source project maintainers and NuGet package publishers are often volunteers who contribute because they care about a given domain, do it for free, and often have a different daytime job.</span></span> <span data-ttu-id="344ae-136">Se você entrar em contato, introduza uma declaração positiva sobre a biblioteca antes de pedir suporte para o .NET Core.</span><span class="sxs-lookup"><span data-stu-id="344ae-136">If you do reach out, you might start with a positive statement about the library before asking about .NET Core support.</span></span>

<span data-ttu-id="344ae-137">Se você não conseguir resolver seu problema com nenhuma das opções acima, talvez seja necessário realizar a portabilidade para o .NET Core posteriormente.</span><span class="sxs-lookup"><span data-stu-id="344ae-137">If you're unable to resolve your issue with any of the above, you may have to port to .NET Core at a later date.</span></span>

<span data-ttu-id="344ae-138">A Equipe .NET gostaria de saber quais bibliotecas são as próximas mais importantes para receber suporte no .NET Core.</span><span class="sxs-lookup"><span data-stu-id="344ae-138">The .NET Team would like to know which libraries are the most important to support next with .NET Core.</span></span> <span data-ttu-id="344ae-139">Você também pode nos enviar um email em dotnet@microsoft.com sobre as bibliotecas que você deseja usar.</span><span class="sxs-lookup"><span data-stu-id="344ae-139">You can also send us mail at dotnet@microsoft.com about the libraries you'd like to use.</span></span>

## <a name="analyzing-dependencies-which-arent-nuget-packages"></a><span data-ttu-id="344ae-140">Analisando dependências que não são pacotes NuGet</span><span class="sxs-lookup"><span data-stu-id="344ae-140">Analyzing Dependencies which aren't NuGet Packages</span></span>

<span data-ttu-id="344ae-141">Você pode ter uma dependência que não é um pacote NuGet, tal como uma DLL no sistema de arquivos.</span><span class="sxs-lookup"><span data-stu-id="344ae-141">You may have a dependency that isn't a NuGet package, such as a DLL in the filesystem.</span></span>  <span data-ttu-id="344ae-142">A única maneira de determinar a portabilidade dessa dependência é executar a [ferramenta ApiPort](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/).</span><span class="sxs-lookup"><span data-stu-id="344ae-142">The only way to determine the portability of that dependency is to run the [ApiPort tool](https://github.com/Microsoft/dotnet-apiport/blob/master/docs/HowTo/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="344ae-143">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="344ae-143">Next steps</span></span>

<span data-ttu-id="344ae-144">Se você estiver portando uma biblioteca, consulte [Portando suas bibliotecas](libraries.md).</span><span class="sxs-lookup"><span data-stu-id="344ae-144">If you're porting a library, check out [Porting your Libraries](libraries.md).</span></span>
