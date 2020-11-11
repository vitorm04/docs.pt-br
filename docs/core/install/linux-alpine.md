---
title: Instalar o .NET no Alpine-.NET
description: Demonstra as várias maneiras de instalar o SDK do .NET e o tempo de execução do .NET na Alpine.
author: adegeo
ms.author: adegeo
ms.date: 11/10/2020
ms.openlocfilehash: 29901cc24ddd4bbe8200a36765ddd29f501394c0
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/11/2020
ms.locfileid: "94506789"
---
# <a name="install-the-net-sdk-or-the-net-runtime-on-alpine"></a><span data-ttu-id="29129-103">Instalar o SDK do .NET ou o tempo de execução do .NET em Alpine Ski</span><span class="sxs-lookup"><span data-stu-id="29129-103">Install the .NET SDK or the .NET Runtime on Alpine</span></span>

<span data-ttu-id="29129-104">Este artigo descreve como instalar o .NET em Alpine Ski.</span><span class="sxs-lookup"><span data-stu-id="29129-104">This article describes how to install .NET on Alpine.</span></span> <span data-ttu-id="29129-105">Quando uma versão do Alpineio ficar sem suporte, o .NET não terá mais suporte com essa versão.</span><span class="sxs-lookup"><span data-stu-id="29129-105">When an Alpine version falls out of support, .NET is no longer supported with that version.</span></span> <span data-ttu-id="29129-106">No entanto, essas instruções podem ajudá-lo a obter o .NET em execução nessas versões, mesmo que não haja suporte.</span><span class="sxs-lookup"><span data-stu-id="29129-106">However, these instructions may help you to get .NET running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

<span data-ttu-id="29129-107">Não há instaladores para o Alpine.</span><span class="sxs-lookup"><span data-stu-id="29129-107">There are no installers for Alpine.</span></span> <span data-ttu-id="29129-108">Você deve usar o [script de instalação](#scripted-install) ou seguir as instruções de [instalação manual](#manual-install) .</span><span class="sxs-lookup"><span data-stu-id="29129-108">You must either use the [install script](#scripted-install) or follow the [manual install](#manual-install) instructions.</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="29129-109">Distribuições com suporte</span><span class="sxs-lookup"><span data-stu-id="29129-109">Supported distributions</span></span>

<span data-ttu-id="29129-110">A tabela a seguir é uma lista de versões do .NET com suporte no momento e as versões do Alpine para as quais têm suporte.</span><span class="sxs-lookup"><span data-stu-id="29129-110">The following table is a list of currently supported .NET releases and the versions of Alpine they're supported on.</span></span> <span data-ttu-id="29129-111">Essas versões permanecem com suporte até que a versão do [.net atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do [Alpine alcance o fim da vida útil](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span><span class="sxs-lookup"><span data-stu-id="29129-111">These versions remain supported until either the version of [.NET reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Alpine reaches end-of-life](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span></span>

- <span data-ttu-id="29129-112">Um ✔️ indica que a versão do Alpine ou .NET ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="29129-112">A ✔️ indicates that the version of Alpine or .NET is still supported.</span></span>
- <span data-ttu-id="29129-113">Um ❌ indica que a versão do Alpine ou do .net não tem suporte nessa versão do Alpine.</span><span class="sxs-lookup"><span data-stu-id="29129-113">A ❌ indicates that the version of Alpine or .NET isn't supported on that Alpine release.</span></span>
- <span data-ttu-id="29129-114">Quando uma versão do Alpine e uma versão do .NET têm ✔️, há suporte para essa combinação de so e .NET.</span><span class="sxs-lookup"><span data-stu-id="29129-114">When both a version of Alpine and a version of .NET have ✔️, that OS and .NET combination is supported.</span></span>

| <span data-ttu-id="29129-115">Alpine</span><span class="sxs-lookup"><span data-stu-id="29129-115">Alpine</span></span>  | <span data-ttu-id="29129-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="29129-116">.NET Core 2.1</span></span> | <span data-ttu-id="29129-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="29129-117">.NET Core 3.1</span></span> | <span data-ttu-id="29129-118">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="29129-118">.NET 5.0</span></span> |
|-------- |---------------|---------------|----------------|
| <span data-ttu-id="29129-119">✔️ 3,12</span><span class="sxs-lookup"><span data-stu-id="29129-119">✔️ 3.12</span></span> | <span data-ttu-id="29129-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="29129-120">✔️ 2.1</span></span>        | <span data-ttu-id="29129-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="29129-121">✔️ 3.1</span></span>        | <span data-ttu-id="29129-122">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="29129-122">✔️ 5.0</span></span> |
| <span data-ttu-id="29129-123">✔️ 3,11</span><span class="sxs-lookup"><span data-stu-id="29129-123">✔️ 3.11</span></span> | <span data-ttu-id="29129-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="29129-124">✔️ 2.1</span></span>        | <span data-ttu-id="29129-125">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="29129-125">✔️ 3.1</span></span>        | <span data-ttu-id="29129-126">✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="29129-126">✔️ 5.0</span></span> |
| <span data-ttu-id="29129-127">✔️ 3,10</span><span class="sxs-lookup"><span data-stu-id="29129-127">✔️ 3.10</span></span> | <span data-ttu-id="29129-128">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="29129-128">✔️ 2.1</span></span>        | <span data-ttu-id="29129-129">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="29129-129">✔️ 3.1</span></span>        | <span data-ttu-id="29129-130">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="29129-130">❌ 5.0</span></span> |
| <span data-ttu-id="29129-131">❌ 3,9</span><span class="sxs-lookup"><span data-stu-id="29129-131">❌ 3.9</span></span>  | <span data-ttu-id="29129-132">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="29129-132">✔️ 2.1</span></span>        | <span data-ttu-id="29129-133">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="29129-133">✔️ 3.1</span></span>        | <span data-ttu-id="29129-134">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="29129-134">❌ 5.0</span></span> |
| <span data-ttu-id="29129-135">❌ 3,8</span><span class="sxs-lookup"><span data-stu-id="29129-135">❌ 3.8</span></span>  | <span data-ttu-id="29129-136">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="29129-136">✔️ 2.1</span></span>        | <span data-ttu-id="29129-137">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="29129-137">✔️ 3.1</span></span>        | <span data-ttu-id="29129-138">❌ 5,0</span><span class="sxs-lookup"><span data-stu-id="29129-138">❌ 5.0</span></span> |

<span data-ttu-id="29129-139">Não há mais suporte para as seguintes versões do .NET.</span><span class="sxs-lookup"><span data-stu-id="29129-139">The following versions of .NET are no longer supported.</span></span> <span data-ttu-id="29129-140">Os downloads para eles ainda permanecem publicados:</span><span class="sxs-lookup"><span data-stu-id="29129-140">The downloads for these still remain published:</span></span>

- <span data-ttu-id="29129-141">3.0</span><span class="sxs-lookup"><span data-stu-id="29129-141">3.0</span></span>
- <span data-ttu-id="29129-142">2.2</span><span class="sxs-lookup"><span data-stu-id="29129-142">2.2</span></span>
- <span data-ttu-id="29129-143">2.0</span><span class="sxs-lookup"><span data-stu-id="29129-143">2.0</span></span>

## <a name="dependencies"></a><span data-ttu-id="29129-144">Dependências</span><span class="sxs-lookup"><span data-stu-id="29129-144">Dependencies</span></span>

<span data-ttu-id="29129-145">O .NET no Alpineum Linux requer as seguintes dependências instaladas:</span><span class="sxs-lookup"><span data-stu-id="29129-145">.NET on Alpine Linux requires the following dependencies installed:</span></span>

- <span data-ttu-id="29129-146">ICU-bibliotecas</span><span class="sxs-lookup"><span data-stu-id="29129-146">icu-libs</span></span>
- <span data-ttu-id="29129-147">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="29129-147">krb5-libs</span></span>
- <span data-ttu-id="29129-148">libgcc</span><span class="sxs-lookup"><span data-stu-id="29129-148">libgcc</span></span>
- <span data-ttu-id="29129-149">libintl</span><span class="sxs-lookup"><span data-stu-id="29129-149">libintl</span></span>
- <span data-ttu-id="29129-150">libssl 1.1 (Alpine v 3.9 ou superior)</span><span class="sxs-lookup"><span data-stu-id="29129-150">libssl1.1 (Alpine v3.9 or greater)</span></span>
- <span data-ttu-id="29129-151">libssl 1.0 (Alpine v 3.8 ou inferior)</span><span class="sxs-lookup"><span data-stu-id="29129-151">libssl1.0 (Alpine v3.8 or lower)</span></span>
- <span data-ttu-id="29129-152">libstdc++</span><span class="sxs-lookup"><span data-stu-id="29129-152">libstdc++</span></span>
- <span data-ttu-id="29129-153">zlib</span><span class="sxs-lookup"><span data-stu-id="29129-153">zlib</span></span>

## <a name="scripted-install"></a><span data-ttu-id="29129-154">Instalação com script</span><span class="sxs-lookup"><span data-stu-id="29129-154">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="29129-155">Instalação manual</span><span class="sxs-lookup"><span data-stu-id="29129-155">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="29129-156">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="29129-156">Next steps</span></span>

- [<span data-ttu-id="29129-157">Tutorial: criar um aplicativo de console com o SDK do .NET usando o Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="29129-157">Tutorial: Create a console application with .NET SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
