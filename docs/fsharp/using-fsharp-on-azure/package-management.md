---
title: 'Usando o gerenciamento de pacotes com F # para o Azure'
description: "Use Paket ou Nuget para gerenciar as dependências de F # do Azure"
keywords: "o Visual f #, f #, funcional programação .NET, .NET Core, o Azure"
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: article
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: dd32ef9c-5416-467e-9fa3-c9ee3bb08456
ms.openlocfilehash: 22dc94ea69e0dfb95e22da4bc64ce915398190d2
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="91b28-104">Pacote de gerenciamento para Dependências F# do Azure</span><span class="sxs-lookup"><span data-stu-id="91b28-104">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="91b28-105">Obter pacotes para o desenvolvimento do Azure é fácil quando você usa um Gerenciador de pacotes.</span><span class="sxs-lookup"><span data-stu-id="91b28-105">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="91b28-106">As duas opções são [Paket](https://fsprojects.github.io/Paket/) e [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="91b28-106">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="91b28-107">Usando Paket</span><span class="sxs-lookup"><span data-stu-id="91b28-107">Using Paket</span></span>

<span data-ttu-id="91b28-108">Se você estiver usando [Paket](https://fsprojects.github.io/Paket/) como seu gerente de dependência, você pode usar o `paket.exe` ferramenta para adicionar dependências do Azure.</span><span class="sxs-lookup"><span data-stu-id="91b28-108">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="91b28-109">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="91b28-109">For example:</span></span>

    > paket add nuget WindowsAzure.Storage

<span data-ttu-id="91b28-110">Ou, se você estiver usando [Mono](http://www.mono-project.com/) para desenvolvimento de plataforma cruzada do .NET:</span><span class="sxs-lookup"><span data-stu-id="91b28-110">Or, if you're using [Mono](http://www.mono-project.com/) for cross-platform .NET development:</span></span>

    > mono paket.exe add nuget WindowsAzure.Storage

<span data-ttu-id="91b28-111">Isso adicionará `WindowsAzure.Storage` seu conjunto de dependências do pacote para o projeto no diretório atual, modifique o `paket.dependencies` de arquivo e baixar o pacote.</span><span class="sxs-lookup"><span data-stu-id="91b28-111">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="91b28-112">Se você tiver configurado anteriormente dependências ou trabalha com um projeto em que as dependências foram definidas por outro desenvolvedor, você pode resolver e instalar dependências localmente como este:</span><span class="sxs-lookup"><span data-stu-id="91b28-112">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > paket install

<span data-ttu-id="91b28-113">Ou, para desenvolvimento Mono:</span><span class="sxs-lookup"><span data-stu-id="91b28-113">Or, for Mono development:</span></span>

    > mono paket.exe install

<span data-ttu-id="91b28-114">Você pode atualizar todas as suas dependências de pacote para a versão mais recente assim:</span><span class="sxs-lookup"><span data-stu-id="91b28-114">You can update all your package dependencies to the latest version like this:</span></span>

    > paket update

<span data-ttu-id="91b28-115">Ou, para desenvolvimento Mono:</span><span class="sxs-lookup"><span data-stu-id="91b28-115">Or, for Mono development:</span></span>

    > mono paket.exe update

## <a name="using-nuget"></a><span data-ttu-id="91b28-116">Usando o Nuget</span><span class="sxs-lookup"><span data-stu-id="91b28-116">Using Nuget</span></span>

<span data-ttu-id="91b28-117">Se você estiver usando [NuGet](https://www.nuget.org/) como seu gerente de dependência, você pode usar o `nuget.exe` ferramenta para adicionar dependências do Azure.</span><span class="sxs-lookup"><span data-stu-id="91b28-117">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="91b28-118">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="91b28-118">For example:</span></span>

    > nuget install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="91b28-119">Ou, para desenvolvimento Mono:</span><span class="sxs-lookup"><span data-stu-id="91b28-119">Or, for Mono development:</span></span>

    > mono nuget.exe install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="91b28-120">Isso adicionará `WindowsAzure.Storage` seu conjunto de dependências do pacote para o projeto no diretório atual e o pacote de download.</span><span class="sxs-lookup"><span data-stu-id="91b28-120">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="91b28-121">Se você tiver configurado anteriormente dependências ou trabalha com um projeto em que as dependências foram definidas por outro desenvolvedor, você pode resolver e instalar dependências localmente como este:</span><span class="sxs-lookup"><span data-stu-id="91b28-121">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > nuget restore 

<span data-ttu-id="91b28-122">Ou, para desenvolvimento Mono:</span><span class="sxs-lookup"><span data-stu-id="91b28-122">Or, for Mono development:</span></span>

    > mono nuget.exe restore

<span data-ttu-id="91b28-123">Você pode atualizar todas as suas dependências de pacote para a versão mais recente assim:</span><span class="sxs-lookup"><span data-stu-id="91b28-123">You can update all your package dependencies to the latest version like this:</span></span>

    > nuget update

<span data-ttu-id="91b28-124">Ou, para desenvolvimento Mono:</span><span class="sxs-lookup"><span data-stu-id="91b28-124">Or, for Mono development:</span></span>

    > mono nuget.exe update

## <a name="referencing-assemblies"></a><span data-ttu-id="91b28-125">Fazendo Referência a Assemblies</span><span class="sxs-lookup"><span data-stu-id="91b28-125">Referencing Assemblies</span></span>

<span data-ttu-id="91b28-126">Para usar seus pacotes em seu script F #, você precisa referenciar os assemblies incluídos nos pacotes usando um `#r` diretiva.</span><span class="sxs-lookup"><span data-stu-id="91b28-126">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="91b28-127">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="91b28-127">For example:</span></span>

    > #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"

<span data-ttu-id="91b28-128">Como você pode ver, você precisará especificar o caminho relativo para a DLL e o nome completo de DLL, que pode não ser exatamente o mesmo que o nome do pacote.</span><span class="sxs-lookup"><span data-stu-id="91b28-128">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="91b28-129">O caminho inclui uma versão do framework e, possivelmente, um número de versão do pacote.</span><span class="sxs-lookup"><span data-stu-id="91b28-129">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="91b28-130">Para localizar todos os assemblies instalados, você pode usar algo como em uma linha de comando do Windows:</span><span class="sxs-lookup"><span data-stu-id="91b28-130">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

    > cd packages/WindowsAzure.Storage
    > dir /s/b *.dll

<span data-ttu-id="91b28-131">Ou, em um shell do Unix, algo parecido com:</span><span class="sxs-lookup"><span data-stu-id="91b28-131">Or in a Unix shell, something like this:</span></span>

    > find packages/WindowsAzure.Storage -name "*.dll"

<span data-ttu-id="91b28-132">Isso lhe dará os caminhos para os assemblies instalados.</span><span class="sxs-lookup"><span data-stu-id="91b28-132">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="91b28-133">A partir daí, você pode selecionar o caminho correto para a sua versão do framework.</span><span class="sxs-lookup"><span data-stu-id="91b28-133">From there, you can select the correct path for your framework version.</span></span>
