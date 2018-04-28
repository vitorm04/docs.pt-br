---
title: 'Usando o gerenciamento de pacotes com F # para o Azure'
description: 'Use Paket ou Nuget para gerenciar as dependências de F # do Azure'
author: sylvanc
ms.author: phcart
ms.date: 09/20/2016
ms.topic: conceptual
ms.prod: dotnet-fsharp
ms.devlang: fsharp
ms.openlocfilehash: da6938c6ee29292571f4269c68a9148c13738422
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="bdc9c-103">Pacote de gerenciamento para Dependências F# do Azure</span><span class="sxs-lookup"><span data-stu-id="bdc9c-103">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="bdc9c-104">Obter pacotes para o desenvolvimento do Azure é fácil quando você usa um Gerenciador de pacotes.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-104">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="bdc9c-105">As duas opções são [Paket](https://fsprojects.github.io/Paket/) e [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="bdc9c-105">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="bdc9c-106">Usando Paket</span><span class="sxs-lookup"><span data-stu-id="bdc9c-106">Using Paket</span></span>

<span data-ttu-id="bdc9c-107">Se você estiver usando [Paket](https://fsprojects.github.io/Paket/) como seu gerente de dependência, você pode usar o `paket.exe` ferramenta para adicionar dependências do Azure.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-107">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="bdc9c-108">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bdc9c-108">For example:</span></span>

    > paket add nuget WindowsAzure.Storage

<span data-ttu-id="bdc9c-109">Ou, se você estiver usando [Mono](https://www.mono-project.com/) para desenvolvimento de plataforma cruzada do .NET:</span><span class="sxs-lookup"><span data-stu-id="bdc9c-109">Or, if you're using [Mono](https://www.mono-project.com/) for cross-platform .NET development:</span></span>

    > mono paket.exe add nuget WindowsAzure.Storage

<span data-ttu-id="bdc9c-110">Isso adicionará `WindowsAzure.Storage` seu conjunto de dependências do pacote para o projeto no diretório atual, modifique o `paket.dependencies` de arquivo e baixar o pacote.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-110">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="bdc9c-111">Se você tiver configurado anteriormente dependências ou trabalha com um projeto em que as dependências foram definidas por outro desenvolvedor, você pode resolver e instalar dependências localmente como este:</span><span class="sxs-lookup"><span data-stu-id="bdc9c-111">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > paket install

<span data-ttu-id="bdc9c-112">Ou, para desenvolvimento Mono:</span><span class="sxs-lookup"><span data-stu-id="bdc9c-112">Or, for Mono development:</span></span>

    > mono paket.exe install

<span data-ttu-id="bdc9c-113">Você pode atualizar todas as suas dependências de pacote para a versão mais recente assim:</span><span class="sxs-lookup"><span data-stu-id="bdc9c-113">You can update all your package dependencies to the latest version like this:</span></span>

    > paket update

<span data-ttu-id="bdc9c-114">Ou, para desenvolvimento Mono:</span><span class="sxs-lookup"><span data-stu-id="bdc9c-114">Or, for Mono development:</span></span>

    > mono paket.exe update

## <a name="using-nuget"></a><span data-ttu-id="bdc9c-115">Usando o Nuget</span><span class="sxs-lookup"><span data-stu-id="bdc9c-115">Using Nuget</span></span>

<span data-ttu-id="bdc9c-116">Se você estiver usando [NuGet](https://www.nuget.org/) como seu gerente de dependência, você pode usar o `nuget.exe` ferramenta para adicionar dependências do Azure.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-116">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="bdc9c-117">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bdc9c-117">For example:</span></span>

    > nuget install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="bdc9c-118">Ou, para desenvolvimento Mono:</span><span class="sxs-lookup"><span data-stu-id="bdc9c-118">Or, for Mono development:</span></span>

    > mono nuget.exe install WindowsAzure.Storage -ExcludeVersion

<span data-ttu-id="bdc9c-119">Isso adicionará `WindowsAzure.Storage` seu conjunto de dependências do pacote para o projeto no diretório atual e o pacote de download.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-119">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="bdc9c-120">Se você tiver configurado anteriormente dependências ou trabalha com um projeto em que as dependências foram definidas por outro desenvolvedor, você pode resolver e instalar dependências localmente como este:</span><span class="sxs-lookup"><span data-stu-id="bdc9c-120">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

    > nuget restore 

<span data-ttu-id="bdc9c-121">Ou, para desenvolvimento Mono:</span><span class="sxs-lookup"><span data-stu-id="bdc9c-121">Or, for Mono development:</span></span>

    > mono nuget.exe restore

<span data-ttu-id="bdc9c-122">Você pode atualizar todas as suas dependências de pacote para a versão mais recente assim:</span><span class="sxs-lookup"><span data-stu-id="bdc9c-122">You can update all your package dependencies to the latest version like this:</span></span>

    > nuget update

<span data-ttu-id="bdc9c-123">Ou, para desenvolvimento Mono:</span><span class="sxs-lookup"><span data-stu-id="bdc9c-123">Or, for Mono development:</span></span>

    > mono nuget.exe update

## <a name="referencing-assemblies"></a><span data-ttu-id="bdc9c-124">Fazendo Referência a Assemblies</span><span class="sxs-lookup"><span data-stu-id="bdc9c-124">Referencing Assemblies</span></span>

<span data-ttu-id="bdc9c-125">Para usar seus pacotes em seu script F #, você precisa referenciar os assemblies incluídos nos pacotes usando um `#r` diretiva.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-125">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="bdc9c-126">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="bdc9c-126">For example:</span></span>

    > #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"

<span data-ttu-id="bdc9c-127">Como você pode ver, você precisará especificar o caminho relativo para a DLL e o nome completo de DLL, que pode não ser exatamente o mesmo que o nome do pacote.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-127">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="bdc9c-128">O caminho inclui uma versão do framework e, possivelmente, um número de versão do pacote.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-128">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="bdc9c-129">Para localizar todos os assemblies instalados, você pode usar algo como em uma linha de comando do Windows:</span><span class="sxs-lookup"><span data-stu-id="bdc9c-129">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

    > cd packages/WindowsAzure.Storage
    > dir /s/b *.dll

<span data-ttu-id="bdc9c-130">Ou, em um shell do Unix, algo parecido com:</span><span class="sxs-lookup"><span data-stu-id="bdc9c-130">Or in a Unix shell, something like this:</span></span>

    > find packages/WindowsAzure.Storage -name "*.dll"

<span data-ttu-id="bdc9c-131">Isso lhe dará os caminhos para os assemblies instalados.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-131">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="bdc9c-132">A partir daí, você pode selecionar o caminho correto para a sua versão do framework.</span><span class="sxs-lookup"><span data-stu-id="bdc9c-132">From there, you can select the correct path for your framework version.</span></span>
