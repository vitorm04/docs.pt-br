---
title: Limitações do Xamarin
ms.date: 12/13/2019
description: Descreve algumas das limitações que você encontrará ao usar o Xamarin.
ms.openlocfilehash: 192f25954726919dc66d706e755e0853404b4d85
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/25/2019
ms.locfileid: "75447163"
---
# <a name="xamarin-limitations"></a><span data-ttu-id="9accd-103">Limitações do Xamarin</span><span class="sxs-lookup"><span data-stu-id="9accd-103">Xamarin limitations</span></span>

<span data-ttu-id="9accd-104">O Microsoft. Data. sqlite tem como destino .NET Standard 2,0 e tem suporte no Xamarin.</span><span class="sxs-lookup"><span data-stu-id="9accd-104">Microsoft.Data.Sqlite targets .NET Standard 2.0 and is supported on Xamarin.</span></span> <span data-ttu-id="9accd-105">A tabela a seguir mostra quais plataformas o pacote SQLitePCLRaw padrão fornece binários do SQLite nativos para o.</span><span class="sxs-lookup"><span data-stu-id="9accd-105">The following table shows which platforms the default SQLitePCLRaw bundle provides native SQLite binaries for.</span></span> <span data-ttu-id="9accd-106">Consulte [versões personalizadas do SQLite](custom-versions.md) para obter detalhes sobre como usar um pacote diferente ou fornecer seus próprios binários do SQLite nativos.</span><span class="sxs-lookup"><span data-stu-id="9accd-106">See [Custom SQLite versions](custom-versions.md) for details on using a different bundle or providing your own native SQLite binaries.</span></span>

| <span data-ttu-id="9accd-107">Platform</span><span class="sxs-lookup"><span data-stu-id="9accd-107">Platform</span></span> | <span data-ttu-id="9accd-108">Binários do SQLite</span><span class="sxs-lookup"><span data-stu-id="9accd-108">SQLite binaries</span></span> |
| --- | --- |
| <span data-ttu-id="9accd-109">**Xamarin.Android**</span><span class="sxs-lookup"><span data-stu-id="9accd-109">**Xamarin.Android**</span></span> | <span data-ttu-id="9accd-110">—</span><span class="sxs-lookup"><span data-stu-id="9accd-110">—</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64-v8a` | <span data-ttu-id="9accd-111">✔</span><span class="sxs-lookup"><span data-stu-id="9accd-111">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`armeabi-v7a` | <span data-ttu-id="9accd-112">✔</span><span class="sxs-lookup"><span data-stu-id="9accd-112">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | <span data-ttu-id="9accd-113">✔</span><span class="sxs-lookup"><span data-stu-id="9accd-113">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86_64` | <span data-ttu-id="9accd-114">✔</span><span class="sxs-lookup"><span data-stu-id="9accd-114">✔</span></span> |
| <span data-ttu-id="9accd-115">**Xamarin.iOS**</span><span class="sxs-lookup"><span data-stu-id="9accd-115">**Xamarin.iOS**</span></span> | <span data-ttu-id="9accd-116">✔</span><span class="sxs-lookup"><span data-stu-id="9accd-116">✔</span></span> |
| <span data-ttu-id="9accd-117">**Xamarin.Mac**</span><span class="sxs-lookup"><span data-stu-id="9accd-117">**Xamarin.Mac**</span></span> | <span data-ttu-id="9accd-118">✔</span><span class="sxs-lookup"><span data-stu-id="9accd-118">✔</span></span> |
| <span data-ttu-id="9accd-119">**Xamarin. TVOS**</span><span class="sxs-lookup"><span data-stu-id="9accd-119">**Xamarin.TVOS**</span></span> | <span data-ttu-id="9accd-120">✔</span><span class="sxs-lookup"><span data-stu-id="9accd-120">✔</span></span> |
| <span data-ttu-id="9accd-121">**UWP**</span><span class="sxs-lookup"><span data-stu-id="9accd-121">**UWP**</span></span> | <span data-ttu-id="9accd-122">—</span><span class="sxs-lookup"><span data-stu-id="9accd-122">—</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm` | <span data-ttu-id="9accd-123">✔</span><span class="sxs-lookup"><span data-stu-id="9accd-123">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`arm64` | <span data-ttu-id="9accd-124">✔</span><span class="sxs-lookup"><span data-stu-id="9accd-124">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x64` | <span data-ttu-id="9accd-125">✔</span><span class="sxs-lookup"><span data-stu-id="9accd-125">✔</span></span> |
| &nbsp;&nbsp;&nbsp;&nbsp;`x86` | <span data-ttu-id="9accd-126">✔</span><span class="sxs-lookup"><span data-stu-id="9accd-126">✔</span></span> |

## <a name="ios"></a><span data-ttu-id="9accd-127">iOS</span><span class="sxs-lookup"><span data-stu-id="9accd-127">iOS</span></span>

<span data-ttu-id="9accd-128">Microsoft. Data. sqlite tenta inicializar automaticamente os pacotes de SQLitePCLRaw.</span><span class="sxs-lookup"><span data-stu-id="9accd-128">Microsoft.Data.Sqlite tries to automatically initialize SQLitePCLRaw bundles.</span></span> <span data-ttu-id="9accd-129">Infelizmente, devido a limitações na compilação da AOT (antecipadamente de tempo) para Xamarin. iOS, a tentativa falha e você obtém o erro a seguir.</span><span class="sxs-lookup"><span data-stu-id="9accd-129">Unfortunately, because of limitations in the ahead-of-time (AOT) compilation for Xamarin.iOS, the attempt fails and you get the following error.</span></span>

> <span data-ttu-id="9accd-130">Você precisa chamar `SQLitePCL.raw.SetProvider()`.</span><span class="sxs-lookup"><span data-stu-id="9accd-130">You need to call `SQLitePCL.raw.SetProvider()`.</span></span> <span data-ttu-id="9accd-131">Se você estiver usando um pacote de pacotes, isso é feito chamando `SQLitePCL.Batteries.Init()`.</span><span class="sxs-lookup"><span data-stu-id="9accd-131">If you're using a bundle package, this is done by calling `SQLitePCL.Batteries.Init()`.</span></span>

<span data-ttu-id="9accd-132">Para inicializar o pacote, adicione a seguinte linha de código ao seu aplicativo antes de usar o Microsoft. Data. sqlite.</span><span class="sxs-lookup"><span data-stu-id="9accd-132">To initialize the bundle, add the following line of code to your app before using Microsoft.Data.Sqlite.</span></span>

```csharp
SQLitePCL.Batteries_V2.Init();
```

## <a name="see-also"></a><span data-ttu-id="9accd-133">Veja também</span><span class="sxs-lookup"><span data-stu-id="9accd-133">See also</span></span>

* [<span data-ttu-id="9accd-134">Limitações assíncronas</span><span class="sxs-lookup"><span data-stu-id="9accd-134">Async limitations</span></span>](async.md)
* [<span data-ttu-id="9accd-135">Versões personalizadas do SQLite</span><span class="sxs-lookup"><span data-stu-id="9accd-135">Custom SQLite versions</span></span>](custom-versions.md)
