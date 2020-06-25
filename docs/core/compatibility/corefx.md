---
title: Alterações significativas na biblioteca de classes base
description: Lista as alterações significativas nas principais bibliotecas do .NET.
ms.date: 09/20/2019
ms.openlocfilehash: 1c56358e69d0dd6e8572a41229c1b9edbcdad795
ms.sourcegitcommit: 63bb83322814f5e5e5c5b69939b14a3139a6ca7e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/25/2020
ms.locfileid: "85365604"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="10eb9-103">Principais alterações significativas nas bibliotecas do .NET</span><span class="sxs-lookup"><span data-stu-id="10eb9-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="10eb9-104">As principais bibliotecas do .NET fornecem os primitivos e outros tipos gerais usados pelo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="10eb9-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="10eb9-105">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="10eb9-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="10eb9-106">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="10eb9-106">Breaking change</span></span> | <span data-ttu-id="10eb9-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="10eb9-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="10eb9-108">Os métodos SSE e SSE2 CompareGreaterThan manipulam corretamente as entradas NaN</span><span class="sxs-lookup"><span data-stu-id="10eb9-108">SSE and SSE2 CompareGreaterThan methods properly handle NaN inputs</span></span>](#sse-and-sse2-comparegreaterthan-methods-properly-handle-nan-inputs) | <span data-ttu-id="10eb9-109">5.0</span><span class="sxs-lookup"><span data-stu-id="10eb9-109">5.0</span></span> |
| [<span data-ttu-id="10eb9-110">CounterSet. CreateCounterSetInstance agora gera InvalidOperationException se a instância já existir</span><span class="sxs-lookup"><span data-stu-id="10eb9-110">CounterSet.CreateCounterSetInstance now throws InvalidOperationException if instance already exist</span></span>](#countersetcreatecountersetinstance-now-throws-invalidoperationexception-if-instance-already-exists) | <span data-ttu-id="10eb9-111">5.0</span><span class="sxs-lookup"><span data-stu-id="10eb9-111">5.0</span></span> |
| [<span data-ttu-id="10eb9-112">Pacote Microsoft. DotNet. PlatformAbstractions removido</span><span class="sxs-lookup"><span data-stu-id="10eb9-112">Microsoft.DotNet.PlatformAbstractions package removed</span></span>](#microsoftdotnetplatformabstractions-package-removed) | <span data-ttu-id="10eb9-113">5.0</span><span class="sxs-lookup"><span data-stu-id="10eb9-113">5.0</span></span> |
| [<span data-ttu-id="10eb9-114">As APIs que relatam versão agora relatam produto e não versão de arquivo</span><span class="sxs-lookup"><span data-stu-id="10eb9-114">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="10eb9-115">3.0</span><span class="sxs-lookup"><span data-stu-id="10eb9-115">3.0</span></span> |
| [<span data-ttu-id="10eb9-116">Instâncias EncoderFallbackBuffer personalizadas não podem retornar recursivamente</span><span class="sxs-lookup"><span data-stu-id="10eb9-116">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="10eb9-117">3.0</span><span class="sxs-lookup"><span data-stu-id="10eb9-117">3.0</span></span> |
| [<span data-ttu-id="10eb9-118">Alterações de comportamento de análise e formatação de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="10eb9-118">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="10eb9-119">3.0</span><span class="sxs-lookup"><span data-stu-id="10eb9-119">3.0</span></span> |
| [<span data-ttu-id="10eb9-120">Operações de análise de ponto flutuante não falham mais ou geram uma estourexception</span><span class="sxs-lookup"><span data-stu-id="10eb9-120">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="10eb9-121">3.0</span><span class="sxs-lookup"><span data-stu-id="10eb9-121">3.0</span></span> |
| [<span data-ttu-id="10eb9-122">InvalidAsynchronousStateException movido para outro assembly</span><span class="sxs-lookup"><span data-stu-id="10eb9-122">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="10eb9-123">3.0</span><span class="sxs-lookup"><span data-stu-id="10eb9-123">3.0</span></span> |
| [<span data-ttu-id="10eb9-124">A substituição de sequências de bytes UTF-8 mal formados segue as diretrizes de Unicode</span><span class="sxs-lookup"><span data-stu-id="10eb9-124">Replacing ill-formed UTF-8 byte sequences follows Unicode guidelines</span></span>](#replacing-ill-formed-utf-8-byte-sequences-follows-unicode-guidelines) | <span data-ttu-id="10eb9-125">3.0</span><span class="sxs-lookup"><span data-stu-id="10eb9-125">3.0</span></span> |
| [<span data-ttu-id="10eb9-126">TypeDescriptionProviderAttribute movido para outro assembly</span><span class="sxs-lookup"><span data-stu-id="10eb9-126">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="10eb9-127">3.0</span><span class="sxs-lookup"><span data-stu-id="10eb9-127">3.0</span></span> |
| [<span data-ttu-id="10eb9-128">O ZipArchiveEntry não lida mais com os arquivos mortos com tamanhos de entrada inconsistentes</span><span class="sxs-lookup"><span data-stu-id="10eb9-128">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="10eb9-129">3.0</span><span class="sxs-lookup"><span data-stu-id="10eb9-129">3.0</span></span> |
| [<span data-ttu-id="10eb9-130">Tipo de exceção de serializador JSON alterado de Jsonexception para NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="10eb9-130">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="10eb9-131">3.0</span><span class="sxs-lookup"><span data-stu-id="10eb9-131">3.0</span></span> |
| [<span data-ttu-id="10eb9-132">Alteração na semântica de (String) NULL em Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="10eb9-132">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="10eb9-133">3.0</span><span class="sxs-lookup"><span data-stu-id="10eb9-133">3.0</span></span> |
| [<span data-ttu-id="10eb9-134">Os métodos JsonEncodedText. Encode têm um argumento JavaScriptEncoder adicional</span><span class="sxs-lookup"><span data-stu-id="10eb9-134">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="10eb9-135">3.0</span><span class="sxs-lookup"><span data-stu-id="10eb9-135">3.0</span></span> |
| [<span data-ttu-id="10eb9-136">Assinatura de JsonFactoryConverter. Createconverter alterada</span><span class="sxs-lookup"><span data-stu-id="10eb9-136">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="10eb9-137">3.0</span><span class="sxs-lookup"><span data-stu-id="10eb9-137">3.0</span></span> |
| [<span data-ttu-id="10eb9-138">Alterações da API jsonelement</span><span class="sxs-lookup"><span data-stu-id="10eb9-138">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="10eb9-139">3.0</span><span class="sxs-lookup"><span data-stu-id="10eb9-139">3.0</span></span> |
| [<span data-ttu-id="10eb9-140">FieldInfo. SetValue gera uma exceção para campos estáticos somente de inicialização</span><span class="sxs-lookup"><span data-stu-id="10eb9-140">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="10eb9-141">3.0</span><span class="sxs-lookup"><span data-stu-id="10eb9-141">3.0</span></span> |
| [<span data-ttu-id="10eb9-142">Campos privados adicionados aos tipos de struct internos</span><span class="sxs-lookup"><span data-stu-id="10eb9-142">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="10eb9-143">2.1</span><span class="sxs-lookup"><span data-stu-id="10eb9-143">2.1</span></span> |
| [<span data-ttu-id="10eb9-144">Alteração no valor padrão de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="10eb9-144">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="10eb9-145">2.1</span><span class="sxs-lookup"><span data-stu-id="10eb9-145">2.1</span></span> |
| [<span data-ttu-id="10eb9-146">Versões do OpenSSL no macOS</span><span class="sxs-lookup"><span data-stu-id="10eb9-146">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="10eb9-147">2.1</span><span class="sxs-lookup"><span data-stu-id="10eb9-147">2.1</span></span> |
| [<span data-ttu-id="10eb9-148">UnauthorizedAccessException gerado por FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="10eb9-148">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="10eb9-149">1.0</span><span class="sxs-lookup"><span data-stu-id="10eb9-149">1.0</span></span> |
| [<span data-ttu-id="10eb9-150">Tratamento de exceções de estado de processo corrompido não é suportado</span><span class="sxs-lookup"><span data-stu-id="10eb9-150">Handling corrupted-process-state exceptions is not supported</span></span>](#handling-corrupted-state-exceptions-is-not-supported) | <span data-ttu-id="10eb9-151">1.0</span><span class="sxs-lookup"><span data-stu-id="10eb9-151">1.0</span></span> |
| [<span data-ttu-id="10eb9-152">As propriedades UriBuilder não precedem mais os caracteres à esquerda</span><span class="sxs-lookup"><span data-stu-id="10eb9-152">UriBuilder properties no longer prepend leading characters</span></span>](#uribuilder-properties-no-longer-prepend-leading-characters) | <span data-ttu-id="10eb9-153">1.0</span><span class="sxs-lookup"><span data-stu-id="10eb9-153">1.0</span></span> |
| [<span data-ttu-id="10eb9-154">Process. StartInfo gera InvalidOperationException para processos que você não iniciou</span><span class="sxs-lookup"><span data-stu-id="10eb9-154">Process.StartInfo throws InvalidOperationException for processes you didn't start</span></span>](#processstartinfo-throws-invalidoperationexception-for-processes-you-didnt-start) | <span data-ttu-id="10eb9-155">1.0</span><span class="sxs-lookup"><span data-stu-id="10eb9-155">1.0</span></span> |

## <a name="net-50"></a><span data-ttu-id="10eb9-156">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="10eb9-156">.NET 5.0</span></span>

[!INCLUDE [sse-comparegreaterthan-intrinsics](../../../includes/core-changes/corefx/5.0/sse-comparegreaterthan-intrinsics.md)]

***

[!INCLUDE [createcountersetinstance-throws-invalidoperation](../../../includes/core-changes/corefx/5.0/createcountersetinstance-throws-invalidoperation.md)]

***

[!INCLUDE [platformabstractions-package-removed](../../../includes/core-changes/corefx/5.0/platformabstractions-package-removed.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="10eb9-157">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="10eb9-157">.NET Core 3.0</span></span>

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

[!INCLUDE[JSON serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/3.0/serializer-throws-notsupportedexception.md)]

***

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/3.0/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/3.0/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/3.0/jsonfactoryconverter-createconverter.md)]

***

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/3.0/jsonelement-api-changes.md)]

***

[!INCLUDE [FieldInfo.SetValue throws exception for static, init-only fields](~/includes/core-changes/corefx/3.0/fieldinfo-setvalue-exception.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="10eb9-158">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="10eb9-158">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="10eb9-159">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="10eb9-159">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***

[!INCLUDE [corrupted-state-exceptions](~/includes/core-changes/corefx/1.0/corrupted-state-exceptions.md)]

***

[!INCLUDE [uribuilder-behavior-changes](../../../includes/core-changes/corefx/1.0/uribuilder-behavior-changes.md)]

***

[!INCLUDE [startinfo-throws-exception](../../../includes/core-changes/corefx/1.0/startinfo-throws-exception.md)]

***
