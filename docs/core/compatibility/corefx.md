---
title: Alterações significativas na biblioteca de classes base
description: Lista as alterações significativas no .NET CoreFx, a biblioteca de classes base.
ms.date: 09/20/2019
ms.openlocfilehash: 7c59f2a96545e74e4099b6078ff52009740699c6
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449537"
---
# <a name="corefx-breaking-changes"></a><span data-ttu-id="3fa40-103">CoreFx alterações significativas</span><span class="sxs-lookup"><span data-stu-id="3fa40-103">CoreFx breaking changes</span></span>

<span data-ttu-id="3fa40-104">O CoreFx fornece os primitivos e outros tipos gerais usados pelo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="3fa40-104">CoreFx provides the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="3fa40-105">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="3fa40-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="3fa40-106">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="3fa40-106">Breaking change</span></span> | <span data-ttu-id="3fa40-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="3fa40-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="3fa40-108">As APIs que relatam versão agora relatam produto e não versão de arquivo</span><span class="sxs-lookup"><span data-stu-id="3fa40-108">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="3fa40-109">3.0</span><span class="sxs-lookup"><span data-stu-id="3fa40-109">3.0</span></span> |
| [<span data-ttu-id="3fa40-110">Instâncias EncoderFallbackBuffer personalizadas não podem retornar recursivamente</span><span class="sxs-lookup"><span data-stu-id="3fa40-110">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="3fa40-111">3.0</span><span class="sxs-lookup"><span data-stu-id="3fa40-111">3.0</span></span> |
| [<span data-ttu-id="3fa40-112">Alterações de comportamento de análise e formatação de ponto flutuante</span><span class="sxs-lookup"><span data-stu-id="3fa40-112">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="3fa40-113">3.0</span><span class="sxs-lookup"><span data-stu-id="3fa40-113">3.0</span></span> |
| [<span data-ttu-id="3fa40-114">Operações de análise de ponto flutuante não falham mais ou geram uma estourexception</span><span class="sxs-lookup"><span data-stu-id="3fa40-114">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="3fa40-115">3.0</span><span class="sxs-lookup"><span data-stu-id="3fa40-115">3.0</span></span> |
| [<span data-ttu-id="3fa40-116">InvalidAsynchronousStateException movido para outro assembly</span><span class="sxs-lookup"><span data-stu-id="3fa40-116">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="3fa40-117">3.0</span><span class="sxs-lookup"><span data-stu-id="3fa40-117">3.0</span></span> |
| [<span data-ttu-id="3fa40-118">O NET Core 3,0 segue as práticas recomendadas de Unicode ao substituir sequências de bytes UTF-8 malformadas</span><span class="sxs-lookup"><span data-stu-id="3fa40-118">NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences) | <span data-ttu-id="3fa40-119">3.0</span><span class="sxs-lookup"><span data-stu-id="3fa40-119">3.0</span></span> |
| [<span data-ttu-id="3fa40-120">TypeDescriptionProviderAttribute movido para outro assembly</span><span class="sxs-lookup"><span data-stu-id="3fa40-120">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="3fa40-121">3.0</span><span class="sxs-lookup"><span data-stu-id="3fa40-121">3.0</span></span> |
| [<span data-ttu-id="3fa40-122">O ZipArchiveEntry não lida mais com os arquivos mortos com tamanhos de entrada inconsistentes</span><span class="sxs-lookup"><span data-stu-id="3fa40-122">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="3fa40-123">3.0</span><span class="sxs-lookup"><span data-stu-id="3fa40-123">3.0</span></span> |
| [<span data-ttu-id="3fa40-124">Tipo de exceção de serializador JSON alterado de Jsonexception para NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="3fa40-124">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="3fa40-125">3.0</span><span class="sxs-lookup"><span data-stu-id="3fa40-125">3.0</span></span> |
| [<span data-ttu-id="3fa40-126">Alteração na semântica de (String) NULL em Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="3fa40-126">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="3fa40-127">3.0</span><span class="sxs-lookup"><span data-stu-id="3fa40-127">3.0</span></span> |
| [<span data-ttu-id="3fa40-128">Os métodos JsonEncodedText. Encode têm um argumento JavaScriptEncoder adicional</span><span class="sxs-lookup"><span data-stu-id="3fa40-128">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="3fa40-129">3.0</span><span class="sxs-lookup"><span data-stu-id="3fa40-129">3.0</span></span> |
| [<span data-ttu-id="3fa40-130">Assinatura de JsonFactoryConverter. Createconverter alterada</span><span class="sxs-lookup"><span data-stu-id="3fa40-130">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="3fa40-131">3.0</span><span class="sxs-lookup"><span data-stu-id="3fa40-131">3.0</span></span> |
| [<span data-ttu-id="3fa40-132">Alterações da API jsonelement</span><span class="sxs-lookup"><span data-stu-id="3fa40-132">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="3fa40-133">3.0</span><span class="sxs-lookup"><span data-stu-id="3fa40-133">3.0</span></span> |
| [<span data-ttu-id="3fa40-134">FieldInfo. SetValue gera uma exceção para campos estáticos somente de inicialização</span><span class="sxs-lookup"><span data-stu-id="3fa40-134">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="3fa40-135">3.0</span><span class="sxs-lookup"><span data-stu-id="3fa40-135">3.0</span></span> |
| [<span data-ttu-id="3fa40-136">Campos privados adicionados aos tipos de struct internos</span><span class="sxs-lookup"><span data-stu-id="3fa40-136">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="3fa40-137">2.1</span><span class="sxs-lookup"><span data-stu-id="3fa40-137">2.1</span></span> |
| [<span data-ttu-id="3fa40-138">Alteração no valor padrão de UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="3fa40-138">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="3fa40-139">2.1</span><span class="sxs-lookup"><span data-stu-id="3fa40-139">2.1</span></span> |
| [<span data-ttu-id="3fa40-140">UnauthorizedAccessException gerado por FileSystemInfo. Attributes</span><span class="sxs-lookup"><span data-stu-id="3fa40-140">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="3fa40-141">1.0</span><span class="sxs-lookup"><span data-stu-id="3fa40-141">1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="3fa40-142">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="3fa40-142">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="3fa40-143">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="3fa40-143">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="3fa40-144">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="3fa40-144">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***
