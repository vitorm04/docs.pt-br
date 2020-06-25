---
title: Instalar o .NET Core no Alpine-.NET Core
description: Demonstra as várias maneiras de instalar SDK do .NET Core e o tempo de execução do .NET Core em Alpine Ski.
author: adegeo
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: 92753933cbcedae28867b66293d1044f700d7baa
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324829"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-alpine"></a><span data-ttu-id="fd6ed-103">Instalar o SDK do .NET Core ou o tempo de execução do .NET Core no Alpine Ski</span><span class="sxs-lookup"><span data-stu-id="fd6ed-103">Install .NET Core SDK or .NET Core Runtime on Alpine</span></span>

<span data-ttu-id="fd6ed-104">Este artigo descreve como instalar o .NET Core em Alpine Ski.</span><span class="sxs-lookup"><span data-stu-id="fd6ed-104">This article describes how to install .NET Core on Alpine.</span></span> <span data-ttu-id="fd6ed-105">Quando uma versão do Alpineio ficar sem suporte, o .NET Core não terá mais suporte nessa versão.</span><span class="sxs-lookup"><span data-stu-id="fd6ed-105">When a Alpine version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="fd6ed-106">No entanto, essas instruções podem ajudá-lo a obter o .NET Core em execução nessas versões, mesmo que não haja suporte.</span><span class="sxs-lookup"><span data-stu-id="fd6ed-106">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

<span data-ttu-id="fd6ed-107">Não há instaladores para o Alpine.</span><span class="sxs-lookup"><span data-stu-id="fd6ed-107">There are no installers for Alpine.</span></span> <span data-ttu-id="fd6ed-108">Você deve usar o [script de instalação](#scripted-install) ou seguir as instruções de [instalação manual](#manual-install) .</span><span class="sxs-lookup"><span data-stu-id="fd6ed-108">You must either use the [install script](#scripted-install) or follow the [manual install](#manual-install) instructions.</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="fd6ed-109">Distribuições com suporte</span><span class="sxs-lookup"><span data-stu-id="fd6ed-109">Supported distributions</span></span>

<span data-ttu-id="fd6ed-110">A tabela a seguir é uma lista de versões do .NET Core com suporte no momento e as versões do Alpine para as quais têm suporte.</span><span class="sxs-lookup"><span data-stu-id="fd6ed-110">The following table is a list of currently supported .NET Core releases and the versions of Alpine they're supported on.</span></span> <span data-ttu-id="fd6ed-111">Essas versões permanecem com suporte até que a versão do [.NET Core atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do [Alpine alcance o fim da vida útil](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span><span class="sxs-lookup"><span data-stu-id="fd6ed-111">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Alpine reaches end-of-life](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span></span>

- <span data-ttu-id="fd6ed-112">Um ✔️ indica que a versão do Alpine ou .NET Core ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="fd6ed-112">A ✔️ indicates that the version of Alpine or .NET Core is still supported.</span></span>
- <span data-ttu-id="fd6ed-113">Um ❌ indica que a versão do Alpine ou .NET Core não tem suporte nessa versão do Alpine.</span><span class="sxs-lookup"><span data-stu-id="fd6ed-113">A ❌ indicates that the version of Alpine or .NET Core isn't supported on that Alpine release.</span></span>
- <span data-ttu-id="fd6ed-114">Quando uma versão do Alpine e uma versão do .NET Core têm ✔️, há suporte para essa combinação de so e .NET.</span><span class="sxs-lookup"><span data-stu-id="fd6ed-114">When both a version of Alpine and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="fd6ed-115">Alpine</span><span class="sxs-lookup"><span data-stu-id="fd6ed-115">Alpine</span></span>                   | <span data-ttu-id="fd6ed-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="fd6ed-116">.NET Core 2.1</span></span> | <span data-ttu-id="fd6ed-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="fd6ed-117">.NET Core 3.1</span></span> | <span data-ttu-id="fd6ed-118">Versão prévia do .NET 5</span><span class="sxs-lookup"><span data-stu-id="fd6ed-118">.NET 5 Preview</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="fd6ed-119">✔️ 3,12</span><span class="sxs-lookup"><span data-stu-id="fd6ed-119">✔️ 3.12</span></span>  | <span data-ttu-id="fd6ed-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="fd6ed-120">✔️ 2.1</span></span>        | <span data-ttu-id="fd6ed-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="fd6ed-121">✔️ 3.1</span></span>        | <span data-ttu-id="fd6ed-122">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="fd6ed-122">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="fd6ed-123">✔️ 3,11</span><span class="sxs-lookup"><span data-stu-id="fd6ed-123">✔️ 3.11</span></span>  | <span data-ttu-id="fd6ed-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="fd6ed-124">✔️ 2.1</span></span>        | <span data-ttu-id="fd6ed-125">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="fd6ed-125">✔️ 3.1</span></span>        | <span data-ttu-id="fd6ed-126">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="fd6ed-126">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="fd6ed-127">✔️ 3,10</span><span class="sxs-lookup"><span data-stu-id="fd6ed-127">✔️ 3.10</span></span>  | <span data-ttu-id="fd6ed-128">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="fd6ed-128">✔️ 2.1</span></span>        | <span data-ttu-id="fd6ed-129">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="fd6ed-129">✔️ 3.1</span></span>        | <span data-ttu-id="fd6ed-130">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="fd6ed-130">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="fd6ed-131">✔️ 3,9</span><span class="sxs-lookup"><span data-stu-id="fd6ed-131">✔️ 3.9</span></span>   | <span data-ttu-id="fd6ed-132">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="fd6ed-132">✔️ 2.1</span></span>        | <span data-ttu-id="fd6ed-133">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="fd6ed-133">✔️ 3.1</span></span>        | <span data-ttu-id="fd6ed-134">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="fd6ed-134">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="fd6ed-135">❌3,8</span><span class="sxs-lookup"><span data-stu-id="fd6ed-135">❌ 3.8</span></span>   | <span data-ttu-id="fd6ed-136">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="fd6ed-136">✔️ 2.1</span></span>        | <span data-ttu-id="fd6ed-137">❌3,1</span><span class="sxs-lookup"><span data-stu-id="fd6ed-137">❌ 3.1</span></span>        | <span data-ttu-id="fd6ed-138">❌visualização de 5,0</span><span class="sxs-lookup"><span data-stu-id="fd6ed-138">❌ 5.0 Preview</span></span> |

<span data-ttu-id="fd6ed-139">Não há mais suporte para as seguintes versões do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="fd6ed-139">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="fd6ed-140">Os downloads para eles ainda permanecem publicados:</span><span class="sxs-lookup"><span data-stu-id="fd6ed-140">The downloads for these still remain published:</span></span>

- <span data-ttu-id="fd6ed-141">3.0</span><span class="sxs-lookup"><span data-stu-id="fd6ed-141">3.0</span></span>
- <span data-ttu-id="fd6ed-142">2.2</span><span class="sxs-lookup"><span data-stu-id="fd6ed-142">2.2</span></span>
- <span data-ttu-id="fd6ed-143">2,0</span><span class="sxs-lookup"><span data-stu-id="fd6ed-143">2.0</span></span>

## <a name="dependencies"></a><span data-ttu-id="fd6ed-144">Dependências</span><span class="sxs-lookup"><span data-stu-id="fd6ed-144">Dependencies</span></span>

<span data-ttu-id="fd6ed-145">O .NET Core no Alpineum Linux requer as seguintes dependências instaladas:</span><span class="sxs-lookup"><span data-stu-id="fd6ed-145">.NET Core on Alpine Linux requires the following dependencies installed:</span></span>

- <span data-ttu-id="fd6ed-146">ICU-bibliotecas</span><span class="sxs-lookup"><span data-stu-id="fd6ed-146">icu-libs</span></span>
- <span data-ttu-id="fd6ed-147">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="fd6ed-147">krb5-libs</span></span>
- <span data-ttu-id="fd6ed-148">libintl</span><span class="sxs-lookup"><span data-stu-id="fd6ed-148">libintl</span></span>
- <span data-ttu-id="fd6ed-149">libssl 1.1 (Alpine v 3.9 ou superior)</span><span class="sxs-lookup"><span data-stu-id="fd6ed-149">libssl1.1 (Alpine v3.9 or greater)</span></span>
- <span data-ttu-id="fd6ed-150">libssl 1.0 (Alpine v 3.8)</span><span class="sxs-lookup"><span data-stu-id="fd6ed-150">libssl1.0 (Alpine v3.8)</span></span>
- <span data-ttu-id="fd6ed-151">libstdc++</span><span class="sxs-lookup"><span data-stu-id="fd6ed-151">libstdc++</span></span>
- <span data-ttu-id="fd6ed-152">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="fd6ed-152">lttng-ust</span></span>
- <span data-ttu-id="fd6ed-153">numactl (opcional)</span><span class="sxs-lookup"><span data-stu-id="fd6ed-153">numactl (optional)</span></span>
- <span data-ttu-id="fd6ed-154">zlib</span><span class="sxs-lookup"><span data-stu-id="fd6ed-154">zlib</span></span>

## <a name="scripted-install"></a><span data-ttu-id="fd6ed-155">Instalação com script</span><span class="sxs-lookup"><span data-stu-id="fd6ed-155">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="fd6ed-156">Instalação manual</span><span class="sxs-lookup"><span data-stu-id="fd6ed-156">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="fd6ed-157">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="fd6ed-157">Next steps</span></span>

- [<span data-ttu-id="fd6ed-158">Tutorial: criar um aplicativo de console com SDK do .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="fd6ed-158">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
