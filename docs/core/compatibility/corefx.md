---
title: Alterações significativas na biblioteca de classes base
description: Lista as alterações significativas nas principais bibliotecas do .NET.
ms.date: 07/27/2020
ms.openlocfilehash: 0667d975ce5bba5692fe5d179341235bd3c61790
ms.sourcegitcommit: 1e6439ec4d5889fc08cf3bfb4dac2b91931eb827
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/08/2020
ms.locfileid: "88024688"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="26bdf-103">Principais alterações significativas nas bibliotecas do .NET</span><span class="sxs-lookup"><span data-stu-id="26bdf-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="26bdf-104">As principais bibliotecas do .NET fornecem os primitivos e outros tipos gerais usados pelo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="26bdf-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="26bdf-105">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="26bdf-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="26bdf-106">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="26bdf-106">Breaking change</span></span> | <span data-ttu-id="26bdf-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="26bdf-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="26bdf-108">IntPtr e UIntPtr implementam IFormattable</span><span class="sxs-lookup"><span data-stu-id="26bdf-108">IntPtr and UIntPtr implement IFormattable</span></span>](#intptr-and-uintptr-implement-iformattable) | <span data-ttu-id="26bdf-109">5.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-109">5.0</span></span> |
| [<span data-ttu-id="26bdf-110">PrincipalPermissionattribute está obsoleto como erro</span><span class="sxs-lookup"><span data-stu-id="26bdf-110">PrincipalPermissionAttribute is obsolete as error</span></span>](#principalpermissionattribute-is-obsolete-as-error) | <span data-ttu-id="26bdf-111">5.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-111">5.0</span></span> |
| [<span data-ttu-id="26bdf-112">Os métodos de serialização BinaryFormatter são obsoletos e proibidos em aplicativos ASP.NET</span><span class="sxs-lookup"><span data-stu-id="26bdf-112">BinaryFormatter serialization methods are obsolete and prohibited in ASP.NET apps</span></span>](#binaryformatter-serialization-methods-are-obsolete-and-prohibited-in-aspnet-apps) | <span data-ttu-id="26bdf-113">5.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-113">5.0</span></span> |
| [<span data-ttu-id="26bdf-114">Os caminhos de código UTF-7 estão obsoletos</span><span class="sxs-lookup"><span data-stu-id="26bdf-114">UTF-7 code paths are obsolete</span></span>](#utf-7-code-paths-are-obsolete) | <span data-ttu-id="26bdf-115">5.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-115">5.0</span></span> |
| [<span data-ttu-id="26bdf-116">Vetor \<T> sempre gera NotSupportedException para tipos sem suporte</span><span class="sxs-lookup"><span data-stu-id="26bdf-116">Vector\<T> always throws NotSupportedException for unsupported types</span></span>](#vectort-always-throws-notsupportedexception-for-unsupported-types) | <span data-ttu-id="26bdf-117">5.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-117">5.0</span></span> |
| [<span data-ttu-id="26bdf-118">O ActivityIdFormat padrão é W3C</span><span class="sxs-lookup"><span data-stu-id="26bdf-118">Default ActivityIdFormat is W3C</span></span>](#default-activityidformat-is-w3c) | <span data-ttu-id="26bdf-119">5.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-119">5.0</span></span> |
| [<span data-ttu-id="26bdf-120">Alteração de comportamento para vector2. Lerp e Vector4. Lerp</span><span class="sxs-lookup"><span data-stu-id="26bdf-120">Behavior change for Vector2.Lerp and Vector4.Lerp</span></span>](#behavior-change-for-vector2lerp-and-vector4lerp) | <span data-ttu-id="26bdf-121">5.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-121">5.0</span></span> |
| [<span data-ttu-id="26bdf-122">Os métodos SSE e SSE2 CompareGreaterThan manipulam corretamente as entradas NaN</span><span class="sxs-lookup"><span data-stu-id="26bdf-122">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="26bdf-123">5.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-123">5.0</span></span> |
| [<span data-ttu-id="26bdf-124">CounterSet. CreateCounterSetInstance agora gera InvalidOperationException se a instância já existir</span><span class="sxs-lookup"><span data-stu-id="26bdf-124">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="26bdf-125">5.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-125">5.0</span></span> |
| [<span data-ttu-id="26bdf-126">Pacote Microsoft. DotNet. PlatformAbstractions removido</span><span class="sxs-lookup"><span data-stu-id="26bdf-126">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="26bdf-127">5.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-127">5.0</span></span> |
| [<span data-ttu-id="26bdf-128">As APIs que relatam versão agora relatam produto e não versão de arquivo</span><span class="sxs-lookup"><span data-stu-id="26bdf-128">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="26bdf-129">3.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-129">3.0</span></span> |
| [<span data-ttu-id="26bdf-130">Instâncias EncoderFallbackBuffer personalizadas não podem retornar recursivamente</span><span class="sxs-lookup"><span data-stu-id="26bdf-130">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="26bdf-131">3.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-131">3.0</span></span> |
| [<span data-ttu-id="26bdf-132">Alterações de comportamento de análise e formatação de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="26bdf-132">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="26bdf-133">3.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-133">3.0</span></span> |
| [<span data-ttu-id="26bdf-134">Operações de análise de ponto flutuante não falham mais ou geram uma estourexception</span><span class="sxs-lookup"><span data-stu-id="26bdf-134">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="26bdf-135">3.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-135">3.0</span></span> |
| [<span data-ttu-id="26bdf-136">InvalidAsynchronousStateException movido para outro assembly</span><span class="sxs-lookup"><span data-stu-id="26bdf-136">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="26bdf-137">3.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-137">3.0</span></span> |
| [<span data-ttu-id="26bdf-138">A substituição de sequências de bytes UTF-8 mal formados segue as diretrizes de Unicode</span><span class="sxs-lookup"><span data-stu-id="26bdf-138">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="26bdf-139">3.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-139">3.0</span></span> |
| [<span data-ttu-id="26bdf-140">TypeDescriptionProviderAttribute movido para outro assembly</span><span class="sxs-lookup"><span data-stu-id="26bdf-140">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="26bdf-141">3.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-141">3.0</span></span> |
| [<span data-ttu-id="26bdf-142">O ZipArchiveEntry não lida mais com os arquivos mortos com tamanhos de entrada inconsistentes</span><span class="sxs-lookup"><span data-stu-id="26bdf-142">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="26bdf-143">3.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-143">3.0</span></span> |
| [<span data-ttu-id="26bdf-144">FieldInfo. SetValue gera uma exceção para campos estáticos somente de inicialização</span><span class="sxs-lookup"><span data-stu-id="26bdf-144">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="26bdf-145">3.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-145">3.0</span></span> |
| [<span data-ttu-id="26bdf-146">Campos privados adicionados aos tipos de struct internos</span><span class="sxs-lookup"><span data-stu-id="26bdf-146">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="26bdf-147">2.1</span><span class="sxs-lookup"><span data-stu-id="26bdf-147">2.1</span></span> |
| [<span data-ttu-id="26bdf-148">Alteração no valor padrão de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="26bdf-148">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="26bdf-149">2.1</span><span class="sxs-lookup"><span data-stu-id="26bdf-149">2.1</span></span> |
| [<span data-ttu-id="26bdf-150">Versões do OpenSSL no macOS</span><span class="sxs-lookup"><span data-stu-id="26bdf-150">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="26bdf-151">2.1</span><span class="sxs-lookup"><span data-stu-id="26bdf-151">2.1</span></span> |
| [<span data-ttu-id="26bdf-152">UnauthorizedAccessException gerado por FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="26bdf-152">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="26bdf-153">1.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-153">1.0</span></span> |
| [<span data-ttu-id="26bdf-154">Tratamento de exceções de estado de processo corrompido não é suportado</span><span class="sxs-lookup"><span data-stu-id="26bdf-154">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="26bdf-155">1.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-155">1.0</span></span> |
| [<span data-ttu-id="26bdf-156">As propriedades UriBuilder não precedem mais os caracteres à esquerda</span><span class="sxs-lookup"><span data-stu-id="26bdf-156">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="26bdf-157">1.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-157">1.0</span></span> |
| [<span data-ttu-id="26bdf-158">Process. StartInfo gera InvalidOperationException para processos que você não iniciou</span><span class="sxs-lookup"><span data-stu-id="26bdf-158">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="26bdf-159">1.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-159">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="26bdf-160">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="26bdf-160">.NET 5.0</span></span>

[!INCLUDE [intptr-uintptr-implement-iformattable](../../../includes/core-changes/corefx/5.0/intptr-uintptr-implement-iformattable.md)]

***

[!INCLUDE [principalpermissionattribute-obsolete](../../../includes/core-changes/corefx/5.0/principalpermissionattribute-obsolete.md)]

***

[!INCLUDE [binaryformatter-serialization-obsolete](../../../includes/core-changes/corefx/5.0/binaryformatter-serialization-obsolete.md)]

***

[!INCLUDE [utf-7-code-paths-obsolete](../../../includes/core-changes/corefx/5.0/utf-7-code-paths-obsolete.md)]

***

[!INCLUDE [vectort-throws-notsupportedexception](../../../includes/core-changes/corefx/5.0/vectort-throws-notsupportedexception.md)]

***

[!INCLUDE [default-activityidformat-changed](../../../includes/core-changes/corefx/5.0/default-activityidformat-changed.md)]

***

[!INCLUDE [vector-lerp-behavior-change](../../../includes/core-changes/corefx/5.0/vector-lerp-behavior-change.md)]

***

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

***

[!INCLUDE [createcountersetinstance-throws-invalidoperation](../../../includes/core-changes/corefx/5.0/createcountersetinstance-throws-invalidoperation.md)]

***

[!INCLUDE [platformabstractions-package-removed](../../../includes/core-changes/corefx/5.0/platformabstractions-package-removed.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="26bdf-161">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-161">.NET Core 3.0</span></span>

[!INCLUDE[APIs that report version now report product and not file version](~/includes/core-changes/corefx/3.0/version-information-changes.md)]

***

[!INCLUDE[Custom EncoderFallbackBuffer instances cannot fall back recursively](~/includes/core-changes/corefx/3.0/custom-encoderfallbackbuffer-cannot-be-recursive.md)]

***

[!INCLUDE[Floating point formatting and parsing behavior changes](~/includes/core-changes/corefx/3.0/floating-point-changes.md)]

***

[!INCLUDE[Floating-point parsing operations no longer fail or throw an OverflowException](~/includes/core-changes/corefx/3.0/floating-point-parsing-does-not-overflow.md)]

***

[!INCLUDE[InvalidAsynchronousStateException moved to another assembly](~/includes/core-changes/corefx/3.0/move-invalidasynchronousstateexception.md)]

***

[!INCLUDE[NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences](~/includes/core-changes/corefx/3.0/net-core-3-0-follows-unicode-utf8-best-practices.md)]

***

[!INCLUDE[TypeDescriptionProviderAttribute moved to another assembly](~/includes/core-changes/corefx/3.0/move-typedescriptionproviderattribute.md)]

***

[!INCLUDE[ZipArchiveEntry no longer handles archives with inconsistent entry sizes](~/includes/core-changes/corefx/3.0/ziparchiveentry-and-inconsistent-entry-sizes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="26bdf-162">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="26bdf-162">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="26bdf-163">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="26bdf-163">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
