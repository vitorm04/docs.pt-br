---
title: 'Usando o Gerenciamento de Pacotes com F # para o Azure'
description: 'Usar o paket ou o NuGet para gerenciar as dependências do Azure F #'
author: sylvanc
ms.date: 09/20/2016
ms.custom: devx-track-fsharp
ms.openlocfilehash: 011a363b264079599e8b7d402fe9896045b1fe04
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91100107"
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="b9a23-103">Pacote de gerenciamento para Dependências F# do Azure</span><span class="sxs-lookup"><span data-stu-id="b9a23-103">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="b9a23-104">A obtenção de pacotes para o desenvolvimento do Azure é fácil quando você usa um Gerenciador de pacotes.</span><span class="sxs-lookup"><span data-stu-id="b9a23-104">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="b9a23-105">As duas opções são [paket](https://fsprojects.github.io/Paket/) e [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="b9a23-105">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="b9a23-106">Usando paket</span><span class="sxs-lookup"><span data-stu-id="b9a23-106">Using Paket</span></span>

<span data-ttu-id="b9a23-107">Se você estiver usando o [paket](https://fsprojects.github.io/Paket/) como seu Gerenciador de dependências, poderá usar a `paket.exe` ferramenta para adicionar as dependências do Azure.</span><span class="sxs-lookup"><span data-stu-id="b9a23-107">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="b9a23-108">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b9a23-108">For example:</span></span>

```console
> paket add nuget WindowsAzure.Storage
```

<span data-ttu-id="b9a23-109">Ou, se você estiver usando o [mono](https://www.mono-project.com/) para desenvolvimento em .net de plataforma cruzada:</span><span class="sxs-lookup"><span data-stu-id="b9a23-109">Or, if you're using [Mono](https://www.mono-project.com/) for cross-platform .NET development:</span></span>

```console
> mono paket.exe add nuget WindowsAzure.Storage
```

<span data-ttu-id="b9a23-110">Isso adicionará `WindowsAzure.Storage` ao conjunto de dependências do pacote para o projeto no diretório atual, modificará o `paket.dependencies` arquivo e baixará o pacote.</span><span class="sxs-lookup"><span data-stu-id="b9a23-110">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="b9a23-111">Se você tiver configurado as dependências anteriormente ou estiver trabalhando com um projeto em que as dependências foram configuradas por outro desenvolvedor, você poderá resolver e instalar dependências localmente da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b9a23-111">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```console
> paket install
```

<span data-ttu-id="b9a23-112">Ou, para o desenvolvimento mono:</span><span class="sxs-lookup"><span data-stu-id="b9a23-112">Or, for Mono development:</span></span>

```console
> mono paket.exe install
```

<span data-ttu-id="b9a23-113">Você pode atualizar todas as dependências de pacote para a versão mais recente como esta:</span><span class="sxs-lookup"><span data-stu-id="b9a23-113">You can update all your package dependencies to the latest version like this:</span></span>

```console
> paket update
```

<span data-ttu-id="b9a23-114">Ou, para o desenvolvimento mono:</span><span class="sxs-lookup"><span data-stu-id="b9a23-114">Or, for Mono development:</span></span>

```console
> mono paket.exe update
```

## <a name="using-nuget"></a><span data-ttu-id="b9a23-115">Usando o NuGet</span><span class="sxs-lookup"><span data-stu-id="b9a23-115">Using Nuget</span></span>

<span data-ttu-id="b9a23-116">Se você estiver usando o [NuGet](https://www.nuget.org/) como seu Gerenciador de dependências, poderá usar a `nuget.exe` ferramenta para adicionar as dependências do Azure.</span><span class="sxs-lookup"><span data-stu-id="b9a23-116">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="b9a23-117">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b9a23-117">For example:</span></span>

```console
> nuget install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="b9a23-118">Ou, para o desenvolvimento mono:</span><span class="sxs-lookup"><span data-stu-id="b9a23-118">Or, for Mono development:</span></span>

```console
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="b9a23-119">Isso adicionará `WindowsAzure.Storage` ao conjunto de dependências do pacote para o projeto no diretório atual e baixará o pacote.</span><span class="sxs-lookup"><span data-stu-id="b9a23-119">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="b9a23-120">Se você tiver configurado as dependências anteriormente ou estiver trabalhando com um projeto em que as dependências foram configuradas por outro desenvolvedor, você poderá resolver e instalar dependências localmente da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="b9a23-120">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```console
> nuget restore
```

<span data-ttu-id="b9a23-121">Ou, para o desenvolvimento mono:</span><span class="sxs-lookup"><span data-stu-id="b9a23-121">Or, for Mono development:</span></span>

```console
> mono nuget.exe restore
```

<span data-ttu-id="b9a23-122">Você pode atualizar todas as dependências de pacote para a versão mais recente como esta:</span><span class="sxs-lookup"><span data-stu-id="b9a23-122">You can update all your package dependencies to the latest version like this:</span></span>

```console
> nuget update
```

<span data-ttu-id="b9a23-123">Ou, para o desenvolvimento mono:</span><span class="sxs-lookup"><span data-stu-id="b9a23-123">Or, for Mono development:</span></span>

```console
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a><span data-ttu-id="b9a23-124">Fazendo Referência a Assemblies</span><span class="sxs-lookup"><span data-stu-id="b9a23-124">Referencing Assemblies</span></span>

<span data-ttu-id="b9a23-125">Para usar seus pacotes em seu script F #, você precisa fazer referência aos assemblies incluídos nos pacotes usando uma `#r` diretiva.</span><span class="sxs-lookup"><span data-stu-id="b9a23-125">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="b9a23-126">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="b9a23-126">For example:</span></span>

```fsharp
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

<span data-ttu-id="b9a23-127">Como você pode ver, você precisará especificar o caminho relativo para a DLL e o nome de DLL completo, que pode não ser exatamente o mesmo que o nome do pacote.</span><span class="sxs-lookup"><span data-stu-id="b9a23-127">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="b9a23-128">O caminho incluirá uma versão da estrutura e, possivelmente, um número de versão do pacote.</span><span class="sxs-lookup"><span data-stu-id="b9a23-128">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="b9a23-129">Para localizar todos os assemblies instalados, você pode usar algo como este em uma linha de comando do Windows:</span><span class="sxs-lookup"><span data-stu-id="b9a23-129">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

```console
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

<span data-ttu-id="b9a23-130">Ou em um shell do UNIX, algo assim:</span><span class="sxs-lookup"><span data-stu-id="b9a23-130">Or in a Unix shell, something like this:</span></span>

```console
> find packages/WindowsAzure.Storage -name "*.dll"
```

<span data-ttu-id="b9a23-131">Isso fornecerá os caminhos para os assemblies instalados.</span><span class="sxs-lookup"><span data-stu-id="b9a23-131">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="b9a23-132">A partir daí, você pode selecionar o caminho correto para a versão da estrutura.</span><span class="sxs-lookup"><span data-stu-id="b9a23-132">From there, you can select the correct path for your framework version.</span></span>
