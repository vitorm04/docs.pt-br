---
title: Instalar o .NET Core no Alpine-.NET Core
description: Demonstra as várias maneiras de instalar SDK do .NET Core e o tempo de execução do .NET Core em Alpine Ski.
author: thraka
ms.author: adegeo
ms.date: 06/04/2020
ms.openlocfilehash: bbaf4ee9020dcd33c894b5376bf04ad65db8d378
ms.sourcegitcommit: 5fd4696a3e5791b2a8c449ccffda87f2cc2d4894
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/15/2020
ms.locfileid: "84771499"
---
# <a name="install-net-core-sdk-or-net-core-runtime-on-alpine"></a><span data-ttu-id="1b456-103">Instalar o SDK do .NET Core ou o tempo de execução do .NET Core no Alpine Ski</span><span class="sxs-lookup"><span data-stu-id="1b456-103">Install .NET Core SDK or .NET Core Runtime on Alpine</span></span>

<span data-ttu-id="1b456-104">Este artigo descreve como instalar o .NET Core em Alpine Ski.</span><span class="sxs-lookup"><span data-stu-id="1b456-104">This article describes how to install .NET Core on Alpine.</span></span> <span data-ttu-id="1b456-105">Quando uma versão do Alpineio ficar sem suporte, o .NET Core não terá mais suporte nessa versão.</span><span class="sxs-lookup"><span data-stu-id="1b456-105">When a Alpine version falls out of support, .NET Core is no longer supported with that version.</span></span> <span data-ttu-id="1b456-106">No entanto, essas instruções podem ajudá-lo a obter o .NET Core em execução nessas versões, mesmo que não haja suporte.</span><span class="sxs-lookup"><span data-stu-id="1b456-106">However, these instructions may help you to get .NET Core running on those versions, even though it isn't supported.</span></span>

[!INCLUDE [linux-intro-sdk-vs-runtime](includes/linux-intro-sdk-vs-runtime.md)]

<span data-ttu-id="1b456-107">Não há instaladores para o Alpine.</span><span class="sxs-lookup"><span data-stu-id="1b456-107">There are no installers for Alpine.</span></span> <span data-ttu-id="1b456-108">Você deve usar o [script de instalação](#scripted-install) ou seguir as instruções de [instalação manual](#manual-install) .</span><span class="sxs-lookup"><span data-stu-id="1b456-108">You must either use the [install script](#scripted-install) or follow the [manual install](#manual-install) instructions.</span></span>

## <a name="supported-distributions"></a><span data-ttu-id="1b456-109">Distribuições com suporte</span><span class="sxs-lookup"><span data-stu-id="1b456-109">Supported distributions</span></span>

<span data-ttu-id="1b456-110">A tabela a seguir é uma lista de versões do .NET Core com suporte no momento e as versões do Alpine para as quais têm suporte.</span><span class="sxs-lookup"><span data-stu-id="1b456-110">The following table is a list of currently supported .NET Core releases and the versions of Alpine they're supported on.</span></span> <span data-ttu-id="1b456-111">Essas versões permanecem com suporte até que a versão do [.NET Core atinja o fim do suporte](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) ou a versão do [Alpine alcance o fim da vida útil](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span><span class="sxs-lookup"><span data-stu-id="1b456-111">These versions remain supported until either the version of [.NET Core reaches end-of-support](https://dotnet.microsoft.com/platform/support/policy/dotnet-core) or the version of [Alpine reaches end-of-life](https://wiki.alpinelinux.org/wiki/Alpine_Linux:Releases).</span></span>

- <span data-ttu-id="1b456-112">Um ✔️ indica que a versão do Alpine ou .NET Core ainda tem suporte.</span><span class="sxs-lookup"><span data-stu-id="1b456-112">A ✔️ indicates that the version of Alpine or .NET Core is still supported.</span></span>
- <span data-ttu-id="1b456-113">Um ❌ indica que a versão do Alpine ou .NET Core não tem suporte nessa versão do Alpine.</span><span class="sxs-lookup"><span data-stu-id="1b456-113">A ❌ indicates that the version of Alpine or .NET Core isn't supported on that Alpine release.</span></span>
- <span data-ttu-id="1b456-114">Quando uma versão do Alpine e uma versão do .NET Core têm ✔️, há suporte para essa combinação de so e .NET.</span><span class="sxs-lookup"><span data-stu-id="1b456-114">When both a version of Alpine and a version of .NET Core have ✔️, that OS and .NET combination are supported.</span></span>

| <span data-ttu-id="1b456-115">Alpine</span><span class="sxs-lookup"><span data-stu-id="1b456-115">Alpine</span></span>                   | <span data-ttu-id="1b456-116">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="1b456-116">.NET Core 2.1</span></span> | <span data-ttu-id="1b456-117">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="1b456-117">.NET Core 3.1</span></span> | <span data-ttu-id="1b456-118">Versão prévia do .NET 5</span><span class="sxs-lookup"><span data-stu-id="1b456-118">.NET 5 Preview</span></span> |
|--------------------------|---------------|---------------|----------------|
| <span data-ttu-id="1b456-119">✔️ 3,12</span><span class="sxs-lookup"><span data-stu-id="1b456-119">✔️ 3.12</span></span>  | <span data-ttu-id="1b456-120">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="1b456-120">✔️ 2.1</span></span>        | <span data-ttu-id="1b456-121">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="1b456-121">✔️ 3.1</span></span>        | <span data-ttu-id="1b456-122">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="1b456-122">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="1b456-123">✔️ 3,11</span><span class="sxs-lookup"><span data-stu-id="1b456-123">✔️ 3.11</span></span>  | <span data-ttu-id="1b456-124">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="1b456-124">✔️ 2.1</span></span>        | <span data-ttu-id="1b456-125">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="1b456-125">✔️ 3.1</span></span>        | <span data-ttu-id="1b456-126">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="1b456-126">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="1b456-127">✔️ 3,10</span><span class="sxs-lookup"><span data-stu-id="1b456-127">✔️ 3.10</span></span>  | <span data-ttu-id="1b456-128">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="1b456-128">✔️ 2.1</span></span>        | <span data-ttu-id="1b456-129">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="1b456-129">✔️ 3.1</span></span>        | <span data-ttu-id="1b456-130">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="1b456-130">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="1b456-131">✔️ 3,9</span><span class="sxs-lookup"><span data-stu-id="1b456-131">✔️ 3.9</span></span>   | <span data-ttu-id="1b456-132">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="1b456-132">✔️ 2.1</span></span>        | <span data-ttu-id="1b456-133">✔️ 3,1</span><span class="sxs-lookup"><span data-stu-id="1b456-133">✔️ 3.1</span></span>        | <span data-ttu-id="1b456-134">versão prévia do ✔️ 5,0</span><span class="sxs-lookup"><span data-stu-id="1b456-134">✔️ 5.0 Preview</span></span> |
| <span data-ttu-id="1b456-135">❌3,8</span><span class="sxs-lookup"><span data-stu-id="1b456-135">❌ 3.8</span></span>   | <span data-ttu-id="1b456-136">✔️ 2,1</span><span class="sxs-lookup"><span data-stu-id="1b456-136">✔️ 2.1</span></span>        | <span data-ttu-id="1b456-137">❌3,1</span><span class="sxs-lookup"><span data-stu-id="1b456-137">❌ 3.1</span></span>        | <span data-ttu-id="1b456-138">❌visualização de 5,0</span><span class="sxs-lookup"><span data-stu-id="1b456-138">❌ 5.0 Preview</span></span> |

<span data-ttu-id="1b456-139">Não há mais suporte para as seguintes versões do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1b456-139">The following versions of .NET Core are no longer supported.</span></span> <span data-ttu-id="1b456-140">Os downloads para eles ainda permanecem publicados:</span><span class="sxs-lookup"><span data-stu-id="1b456-140">The downloads for these still remain published:</span></span>

- <span data-ttu-id="1b456-141">3.0</span><span class="sxs-lookup"><span data-stu-id="1b456-141">3.0</span></span>
- <span data-ttu-id="1b456-142">2.2</span><span class="sxs-lookup"><span data-stu-id="1b456-142">2.2</span></span>
- <span data-ttu-id="1b456-143">2,0</span><span class="sxs-lookup"><span data-stu-id="1b456-143">2.0</span></span>

## <a name="dependencies"></a><span data-ttu-id="1b456-144">Dependências</span><span class="sxs-lookup"><span data-stu-id="1b456-144">Dependencies</span></span>

<span data-ttu-id="1b456-145">O .NET Core no Alpineum Linux requer as seguintes dependências instaladas:</span><span class="sxs-lookup"><span data-stu-id="1b456-145">.NET Core on Alpine Linux requires the following dependencies installed:</span></span>

- <span data-ttu-id="1b456-146">ICU-bibliotecas</span><span class="sxs-lookup"><span data-stu-id="1b456-146">icu-libs</span></span>
- <span data-ttu-id="1b456-147">krb5-libs</span><span class="sxs-lookup"><span data-stu-id="1b456-147">krb5-libs</span></span>
- <span data-ttu-id="1b456-148">libintl</span><span class="sxs-lookup"><span data-stu-id="1b456-148">libintl</span></span>
- <span data-ttu-id="1b456-149">libssl 1.1 (Alpine v 3.9 ou superior)</span><span class="sxs-lookup"><span data-stu-id="1b456-149">libssl1.1 (Alpine v3.9 or greater)</span></span>
- <span data-ttu-id="1b456-150">libssl 1.0 (Alpine v 3.8)</span><span class="sxs-lookup"><span data-stu-id="1b456-150">libssl1.0 (Alpine v3.8)</span></span>
- <span data-ttu-id="1b456-151">libstdc++</span><span class="sxs-lookup"><span data-stu-id="1b456-151">libstdc++</span></span>
- <span data-ttu-id="1b456-152">lttng-ust</span><span class="sxs-lookup"><span data-stu-id="1b456-152">lttng-ust</span></span>
- <span data-ttu-id="1b456-153">numactl (opcional)</span><span class="sxs-lookup"><span data-stu-id="1b456-153">numactl (optional)</span></span>
- <span data-ttu-id="1b456-154">zlib</span><span class="sxs-lookup"><span data-stu-id="1b456-154">zlib</span></span>

## <a name="scripted-install"></a><span data-ttu-id="1b456-155">Instalação com script</span><span class="sxs-lookup"><span data-stu-id="1b456-155">Scripted install</span></span>

[!INCLUDE [linux-install-scripted](includes/linux-install-scripted.md)]

## <a name="manual-install"></a><span data-ttu-id="1b456-156">Instalação manual</span><span class="sxs-lookup"><span data-stu-id="1b456-156">Manual install</span></span>

[!INCLUDE [linux-install-manual](includes/linux-install-manual.md)]

## <a name="next-steps"></a><span data-ttu-id="1b456-157">Próximas etapas</span><span class="sxs-lookup"><span data-stu-id="1b456-157">Next steps</span></span>

- [<span data-ttu-id="1b456-158">Tutorial: criar um aplicativo de console com SDK do .NET Core usando Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="1b456-158">Tutorial: Create a console application with .NET Core SDK using Visual Studio Code</span></span>](../tutorials/with-visual-studio-code.md)
