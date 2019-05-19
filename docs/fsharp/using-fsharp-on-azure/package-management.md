---
title: Usando o gerenciamento de pacotes com F# para o Azure
description: Usar Paket ou Nuget para gerenciar F# dependências do Azure
author: sylvanc
ms.date: 09/20/2016
ms.openlocfilehash: b180024e2276a2fd7786f35cb922b1aa1d91f0ad
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2019
ms.locfileid: "65880013"
---
# <a name="package-management-for-f-azure-dependencies"></a><span data-ttu-id="a9f17-103">Pacote de gerenciamento para Dependências F# do Azure</span><span class="sxs-lookup"><span data-stu-id="a9f17-103">Package Management for F# Azure Dependencies</span></span>

<span data-ttu-id="a9f17-104">Obter pacotes para desenvolvimento do Azure é fácil quando você usa um Gerenciador de pacotes.</span><span class="sxs-lookup"><span data-stu-id="a9f17-104">Obtaining packages for Azure development is easy when you use a package manager.</span></span> <span data-ttu-id="a9f17-105">As duas opções são [Paket](https://fsprojects.github.io/Paket/) e [NuGet](https://www.nuget.org/).</span><span class="sxs-lookup"><span data-stu-id="a9f17-105">The two options are [Paket](https://fsprojects.github.io/Paket/) and [NuGet](https://www.nuget.org/).</span></span>

## <a name="using-paket"></a><span data-ttu-id="a9f17-106">Usando Paket</span><span class="sxs-lookup"><span data-stu-id="a9f17-106">Using Paket</span></span>

<span data-ttu-id="a9f17-107">Se você estiver usando [Paket](https://fsprojects.github.io/Paket/) como o Gerenciador de dependência, você pode usar o `paket.exe` ferramenta para adicionar dependências do Azure.</span><span class="sxs-lookup"><span data-stu-id="a9f17-107">If you're using [Paket](https://fsprojects.github.io/Paket/) as your dependency manager, you can use the `paket.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="a9f17-108">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a9f17-108">For example:</span></span>

```
> paket add nuget WindowsAzure.Storage
```

<span data-ttu-id="a9f17-109">Ou, se você estiver usando [Mono](https://www.mono-project.com/) para desenvolvimento de plataforma cruzada do .NET:</span><span class="sxs-lookup"><span data-stu-id="a9f17-109">Or, if you're using [Mono](https://www.mono-project.com/) for cross-platform .NET development:</span></span>

```
> mono paket.exe add nuget WindowsAzure.Storage
```

<span data-ttu-id="a9f17-110">Isso adicionará `WindowsAzure.Storage` ao seu conjunto de dependências do pacote para o projeto no diretório atual, modifique o `paket.dependencies` de arquivo e baixe o pacote.</span><span class="sxs-lookup"><span data-stu-id="a9f17-110">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, modify the `paket.dependencies` file, and download the package.</span></span> <span data-ttu-id="a9f17-111">Se você tiver configurado anteriormente dependências ou trabalhando com um projeto em que as dependências foram configuradas por outro desenvolvedor, você pode resolver e instalar dependências localmente como este:</span><span class="sxs-lookup"><span data-stu-id="a9f17-111">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```
> paket install
```

<span data-ttu-id="a9f17-112">Ou, para desenvolvimento Mono:</span><span class="sxs-lookup"><span data-stu-id="a9f17-112">Or, for Mono development:</span></span>

```
> mono paket.exe install
```

<span data-ttu-id="a9f17-113">Você pode atualizar todas as suas dependências de pacote para a versão mais recente, como este:</span><span class="sxs-lookup"><span data-stu-id="a9f17-113">You can update all your package dependencies to the latest version like this:</span></span>

```
> paket update
```

<span data-ttu-id="a9f17-114">Ou, para desenvolvimento Mono:</span><span class="sxs-lookup"><span data-stu-id="a9f17-114">Or, for Mono development:</span></span>

```
> mono paket.exe update
```

## <a name="using-nuget"></a><span data-ttu-id="a9f17-115">Usando o Nuget</span><span class="sxs-lookup"><span data-stu-id="a9f17-115">Using Nuget</span></span>

<span data-ttu-id="a9f17-116">Se você estiver usando [NuGet](https://www.nuget.org/) como o Gerenciador de dependência, você pode usar o `nuget.exe` ferramenta para adicionar dependências do Azure.</span><span class="sxs-lookup"><span data-stu-id="a9f17-116">If you're using [NuGet](https://www.nuget.org/) as your dependency manager, you can use the `nuget.exe` tool to add Azure dependencies.</span></span> <span data-ttu-id="a9f17-117">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a9f17-117">For example:</span></span>

```
> nuget install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="a9f17-118">Ou, para desenvolvimento Mono:</span><span class="sxs-lookup"><span data-stu-id="a9f17-118">Or, for Mono development:</span></span>

```
> mono nuget.exe install WindowsAzure.Storage -ExcludeVersion
```

<span data-ttu-id="a9f17-119">Isso adicionará `WindowsAzure.Storage` ao seu conjunto de dependências do pacote para o projeto no diretório atual e o pacote de download.</span><span class="sxs-lookup"><span data-stu-id="a9f17-119">This will add `WindowsAzure.Storage` to your set of package dependencies for the project in the current directory, and download the package.</span></span> <span data-ttu-id="a9f17-120">Se você tiver configurado anteriormente dependências ou trabalhando com um projeto em que as dependências foram configuradas por outro desenvolvedor, você pode resolver e instalar dependências localmente como este:</span><span class="sxs-lookup"><span data-stu-id="a9f17-120">If you have previously set up dependencies, or are working with a project where dependencies have been set up by another developer, you can resolve and install dependencies locally like this:</span></span>

```
> nuget restore
```

<span data-ttu-id="a9f17-121">Ou, para desenvolvimento Mono:</span><span class="sxs-lookup"><span data-stu-id="a9f17-121">Or, for Mono development:</span></span>

```
> mono nuget.exe restore
```

<span data-ttu-id="a9f17-122">Você pode atualizar todas as suas dependências de pacote para a versão mais recente, como este:</span><span class="sxs-lookup"><span data-stu-id="a9f17-122">You can update all your package dependencies to the latest version like this:</span></span>

```
> nuget update
```

<span data-ttu-id="a9f17-123">Ou, para desenvolvimento Mono:</span><span class="sxs-lookup"><span data-stu-id="a9f17-123">Or, for Mono development:</span></span>

```
> mono nuget.exe update
```

## <a name="referencing-assemblies"></a><span data-ttu-id="a9f17-124">Fazendo Referência a Assemblies</span><span class="sxs-lookup"><span data-stu-id="a9f17-124">Referencing Assemblies</span></span>

<span data-ttu-id="a9f17-125">Para usar os pacotes em seu F# script, você precisa fazer referência os assemblies incluídos nos pacotes usando uma `#r` diretiva.</span><span class="sxs-lookup"><span data-stu-id="a9f17-125">In order to use your packages in your F# script, you need to reference the assemblies included in the packages using a `#r` directive.</span></span> <span data-ttu-id="a9f17-126">Por exemplo:</span><span class="sxs-lookup"><span data-stu-id="a9f17-126">For example:</span></span>

```
> #r "packages/WindowsAzure.Storage/lib/net40/Microsoft.WindowsAzure.Storage.dll"
```

<span data-ttu-id="a9f17-127">Como você pode ver, você precisará especificar o caminho relativo para a DLL e o nome completo de DLL, que pode não ser exatamente o mesmo que o nome do pacote.</span><span class="sxs-lookup"><span data-stu-id="a9f17-127">As you can see, you'll need to specify the relative path to the DLL and the full DLL name, which may not be exactly the same as the package name.</span></span> <span data-ttu-id="a9f17-128">O caminho inclui uma versão do framework e, possivelmente, um número de versão do pacote.</span><span class="sxs-lookup"><span data-stu-id="a9f17-128">The path will include a framework version and possibly a package version number.</span></span> <span data-ttu-id="a9f17-129">Para localizar todos os assemblies instalados, você pode usar algo parecido com isso em uma linha de comando do Windows:</span><span class="sxs-lookup"><span data-stu-id="a9f17-129">To find all the installed assemblies, you can use something like this on a Windows command line:</span></span>

```
> cd packages/WindowsAzure.Storage
> dir /s/b *.dll
```

<span data-ttu-id="a9f17-130">Ou em um shell do Unix, algo parecido com isto:</span><span class="sxs-lookup"><span data-stu-id="a9f17-130">Or in a Unix shell, something like this:</span></span>

```
> find packages/WindowsAzure.Storage -name "*.dll"
```

<span data-ttu-id="a9f17-131">Isso lhe dará os caminhos para os assemblies instalados.</span><span class="sxs-lookup"><span data-stu-id="a9f17-131">This will give you the paths to the installed assemblies.</span></span> <span data-ttu-id="a9f17-132">A partir daí, você pode selecionar o caminho correto para a sua versão do framework.</span><span class="sxs-lookup"><span data-stu-id="a9f17-132">From there, you can select the correct path for your framework version.</span></span>
