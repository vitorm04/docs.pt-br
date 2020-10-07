---
title: 'Usando o Gerenciamento de Pacotes com F # para o Azure'
description: 'Usar o paket ou o NuGet para gerenciar as dependências do Azure F #'
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: 7816c82e87db113a35fef967886c8c3e27959332
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/06/2020
ms.locfileid: "91756228"
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="56d5e-103">Pacote de gerenciamento para Dependências F# do Azure</span><span class="sxs-lookup"><span data-stu-id="56d5e-103">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="56d5e-104">A obtenção de pacotes para o desenvolvimento do Azure é fácil quando você usa um Gerenciador de pacotes.</span><span class="sxs-lookup"><span data-stu-id="56d5e-104">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="56d5e-105">As duas opções são [paket](https://fsprojects.github.io/Paket/) e [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="56d5e-105">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="56d5e-106">Usando paket</span><span class="sxs-lookup"><span data-stu-id="56d5e-106">Using Paket</span></span>

<span data-ttu-id="56d5e-107">Se você estiver usando o [paket](https://fsprojects.github.io/Paket/) como seu Gerenciador de dependências, poderá usar a `paket.exe` ferramenta para adicionar as dependências do Azure.</span><span class="sxs-lookup"><span data-stu-id="56d5e-107">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="56d5e-108">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="56d5e-108">For example:</span></span>

```console
> paket add nuget WindowsAzure.Storage
```

<span data-ttu-id="56d5e-109">Ou, se você estiver usando o [mono](https://www.mono-project.com/) para desenvolvimento em .net de plataforma cruzada:</span><span class="sxs-lookup"><span data-stu-id="56d5e-109">Or, if you're using [Mono](https://www.mono-project.com/) for cross-platform .NET development:</span></span>

```console
> mono paket.exe add nuget WindowsAzure.Storage
```

<span data-ttu-id="56d5e-110">Isso adicionará `WindowsAzure.Storage` ao conjunto de dependências do pacote para o projeto no diretório atual, modificará o `paket.dependencies` arquivo e baixará o pacote.</span><span class="sxs-lookup"><span data-stu-id="56d5e-110">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="56d5e-111">Se você tiver configurado as dependências anteriormente ou estiver trabalhando com um projeto em que as dependências foram configuradas por outro desenvolvedor, você poderá resolver e instalar dependências localmente da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="56d5e-111">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```console
> paket install
```

<span data-ttu-id="56d5e-112">Ou, para o desenvolvimento mono:</span><span class="sxs-lookup"><span data-stu-id="56d5e-112">Or, for Mono development:</span></span>

```console
> mono paket.exe install
```

<span data-ttu-id="56d5e-113">Você pode atualizar todas as dependências de pacote para a versão mais recente como esta:</span><span class="sxs-lookup"><span data-stu-id="56d5e-113">You can update all your package dependencies to the latest version like this:</span></span>

```console
> paket update
```

<span data-ttu-id="56d5e-114">Ou, para o desenvolvimento mono:</span><span class="sxs-lookup"><span data-stu-id="56d5e-114">Or, for Mono development:</span></span>

```console
> mono paket.exe update
```

## <a name="using-nuget"></a><span data-ttu-id="56d5e-115">Usando o NuGet</span><span class="sxs-lookup"><span data-stu-id="56d5e-115">Using NuGet</span></span>

<span data-ttu-id="56d5e-116">Se você estiver usando o [NuGet](https://www.nuget.org/) como seu Gerenciador de dependências, poderá usar a `nuget.exe` ferramenta para adicionar as dependências do Azure.</span><span class="sxs-lookup"><span data-stu-id="56d5e-116">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="56d5e-117">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="56d5e-117">For example:</span></span>

```console
> nuget install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="56d5e-118">Ou, para o desenvolvimento mono:</span><span class="sxs-lookup"><span data-stu-id="56d5e-118">Or, for Mono development:</span></span>

```console
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="56d5e-119">Isso adicionará `WindowsAzure.Storage` ao conjunto de dependências do pacote para o projeto no diretório atual e baixará o pacote.</span><span class="sxs-lookup"><span data-stu-id="56d5e-119">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="56d5e-120">Se você tiver configurado as dependências anteriormente ou estiver trabalhando com um projeto em que as dependências foram configuradas por outro desenvolvedor, você poderá resolver e instalar dependências localmente da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="56d5e-120">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```console
> nuget restore
```

<span data-ttu-id="56d5e-121">Ou, para o desenvolvimento mono:</span><span class="sxs-lookup"><span data-stu-id="56d5e-121">Or, for Mono development:</span></span>

```console
> mono nuget.exe restore
```

<span data-ttu-id="56d5e-122">Você pode atualizar todas as dependências de pacote para a versão mais recente como esta:</span><span class="sxs-lookup"><span data-stu-id="56d5e-122">You can update all your package dependencies to the latest version like this:</span></span>

```console
> nuget update
```

<span data-ttu-id="56d5e-123">Ou, para o desenvolvimento mono:</span><span class="sxs-lookup"><span data-stu-id="56d5e-123">Or, for Mono development:</span></span>

```console
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a><span data-ttu-id="56d5e-124">Fazendo Referência a Assemblies</span><span class="sxs-lookup"><span data-stu-id="56d5e-124">Referencing Assemblies</span></span>

<span data-ttu-id="56d5e-125">Para usar seus pacotes em seu script F #, você precisa fazer referência aos assemblies incluídos nos pacotes usando uma `#r` diretiva.</span><span class="sxs-lookup"><span data-stu-id="56d5e-125">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="56d5e-126">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="56d5e-126">For example:</span></span>

```fsharp
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

<span data-ttu-id="56d5e-127">Como você pode ver, você precisará especificar o caminho relativo para a DLL e o nome de DLL completo, que pode não ser exatamente o mesmo que o nome do pacote.</span><span class="sxs-lookup"><span data-stu-id="56d5e-127">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="56d5e-128">O caminho incluirá uma versão da estrutura e, possivelmente, um número de versão do pacote.</span><span class="sxs-lookup"><span data-stu-id="56d5e-128">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="56d5e-129">Para localizar todos os assemblies instalados, você pode usar algo como este em uma linha de comando do Windows:</span><span class="sxs-lookup"><span data-stu-id="56d5e-129">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

```console
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

<span data-ttu-id="56d5e-130">Ou em um shell do UNIX, algo assim:</span><span class="sxs-lookup"><span data-stu-id="56d5e-130">Or in a Unix shell, something like this:</span></span>

```console
> find packages/WindowsAzure.Storage -name "*.dll"
```

<span data-ttu-id="56d5e-131">Isso fornecerá os caminhos para os assemblies instalados.</span><span class="sxs-lookup"><span data-stu-id="56d5e-131">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="56d5e-132">A partir daí, você pode selecionar o caminho correto para a versão da estrutura.</span><span class="sxs-lookup"><span data-stu-id="56d5e-132">From there, you can select the correct path for your framework version.</span></span>
