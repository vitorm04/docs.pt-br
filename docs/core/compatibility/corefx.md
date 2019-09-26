---
title: CoreFx alterações significativas – .NET Core
description: Lista as alterações significativas no .NET CoreFx, a biblioteca de classes base.
ms.date: 09/20/2019
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3838bcd7c127860a8307fe31bd85ed5addffb59e
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71272708"
---
# <a name="corefx-breaking-changes"></a><span data-ttu-id="9479e-103">CoreFx alterações significativas</span><span class="sxs-lookup"><span data-stu-id="9479e-103">CoreFx breaking changes</span></span>

> [!IMPORTANT]
> <span data-ttu-id="9479e-104">Este artigo está em construção.</span><span class="sxs-lookup"><span data-stu-id="9479e-104">This article is under construction.</span></span> <span data-ttu-id="9479e-105">Esta não é uma lista completa de alterações significativas do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9479e-105">This is not a complete list of .NET Core breaking changes.</span></span> <span data-ttu-id="9479e-106">Para obter mais informações sobre as alterações significativas no .NET Core, você pode examinar os problemas individuais de [alterações significativas](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) no repositório dotnet/docs no github.</span><span class="sxs-lookup"><span data-stu-id="9479e-106">For more information on .NET Core breaking changes, you can examine individual [breaking changes issues](https://github.com/dotnet/docs/issues?q=is%3Aissue+is%3Aopen+label%3Abreaking-change) in the dotnet/docs repository on GitHub.</span></span>

<span data-ttu-id="9479e-107">A seguir está uma lista de alterações significativas de CoreFx pela versão do .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9479e-107">The following is a list of CoreFx breaking changes by .NET Core version.</span></span> <span data-ttu-id="9479e-108">O CoreFx fornece os primitivos e outros tipos gerais usados pelo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9479e-108">CoreFx provides the primitives and other general types used by .NET Core.</span></span>

## <a name="net-core-30-preview-7"></a><span data-ttu-id="9479e-109">.NET Core 3,0 Preview 7</span><span class="sxs-lookup"><span data-stu-id="9479e-109">.NET Core 3.0 Preview 7</span></span>

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/jsonelement-api-changes.md)]

## <a name="net-core-30-preview-8"></a><span data-ttu-id="9479e-110">.NET Core 3,0 Preview 8</span><span class="sxs-lookup"><span data-stu-id="9479e-110">.NET Core 3.0 Preview 8</span></span>

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/jsonfactoryconverter-createconverter.md)]

## <a name="net-core-30-preview-9"></a><span data-ttu-id="9479e-111">.NET Core 3,0 Preview 9</span><span class="sxs-lookup"><span data-stu-id="9479e-111">.NET Core 3.0 Preview 9</span></span>

[!INCLUDE[Json serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/serializer-throws-notsupportedexception.md)]

## <a name="net-core-30"></a><span data-ttu-id="9479e-112">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9479e-112">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/floating-point-changes.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/ziparchiveentry-and-inconsistent-entry-sizes.md)]
