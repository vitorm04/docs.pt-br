---
title: Biblioteca de classe base quebrando mudanças
description: Lista as alterações de quebra nas bibliotecas .NET principais.
ms.date: 09/20/2019
ms.openlocfilehash: 8cf90ca2bc8736101c1cb8d327a93d100148937b
ms.sourcegitcommit: 348bb052d5cef109a61a3d5253faa5d7167d55ac
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/22/2020
ms.locfileid: "82021833"
---
# <a name="core-net-libraries-breaking-changes"></a><span data-ttu-id="23a5e-103">Bibliotecas Core .NET quebrando alterações</span><span class="sxs-lookup"><span data-stu-id="23a5e-103">Core .NET libraries breaking changes</span></span>

<span data-ttu-id="23a5e-104">As bibliotecas .NET principais fornecem os primitivos e outros tipos gerais usados pelo .NET Core.</span><span class="sxs-lookup"><span data-stu-id="23a5e-104">The core .NET libraries provide the primitives and other general types used by .NET Core.</span></span>

<span data-ttu-id="23a5e-105">As seguintes alterações de quebra estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="23a5e-105">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="23a5e-106">Mudança de ruptura</span><span class="sxs-lookup"><span data-stu-id="23a5e-106">Breaking change</span></span> | <span data-ttu-id="23a5e-107">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="23a5e-107">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="23a5e-108">APIs que relatam versão agora relatam produto e não versão de arquivo</span><span class="sxs-lookup"><span data-stu-id="23a5e-108">APIs that report version now report product and not file version</span></span>](#apis-that-report-version-now-report-product-and-not-file-version) | <span data-ttu-id="23a5e-109">3.0</span><span class="sxs-lookup"><span data-stu-id="23a5e-109">3.0</span></span> |
| [<span data-ttu-id="23a5e-110">As instâncias de EncoderFallbackBuffer personalizadas não podem recuar recursivamente</span><span class="sxs-lookup"><span data-stu-id="23a5e-110">Custom EncoderFallbackBuffer instances cannot fall back recursively</span></span>](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | <span data-ttu-id="23a5e-111">3.0</span><span class="sxs-lookup"><span data-stu-id="23a5e-111">3.0</span></span> |
| [<span data-ttu-id="23a5e-112">Formatação de pontos flutuantes e mudanças de comportamento de análise</span><span class="sxs-lookup"><span data-stu-id="23a5e-112">Floating point formatting and parsing behavior changes</span></span>](#floating-point-formatting-and-parsing-behavior-changed) | <span data-ttu-id="23a5e-113">3.0</span><span class="sxs-lookup"><span data-stu-id="23a5e-113">3.0</span></span> |
| [<span data-ttu-id="23a5e-114">As operações de análise de ponto flutuante não falham mais ou lançam uma Exceção de Estouro</span><span class="sxs-lookup"><span data-stu-id="23a5e-114">Floating-point parsing operations no longer fail or throw an OverflowException</span></span>](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | <span data-ttu-id="23a5e-115">3.0</span><span class="sxs-lookup"><span data-stu-id="23a5e-115">3.0</span></span> |
| [<span data-ttu-id="23a5e-116">InvalidAsynchronousStateException mudou-se para outro conjunto</span><span class="sxs-lookup"><span data-stu-id="23a5e-116">InvalidAsynchronousStateException moved to another assembly</span></span>](#invalidasynchronousstateexception-moved-to-another-assembly) | <span data-ttu-id="23a5e-117">3.0</span><span class="sxs-lookup"><span data-stu-id="23a5e-117">3.0</span></span> |
| [<span data-ttu-id="23a5e-118">Net Core 3.0 segue as melhores práticas da Unicode ao substituir sequências de bytes UTF-8 mal formadas</span><span class="sxs-lookup"><span data-stu-id="23a5e-118">NET Core 3.0 follows Unicode best practices when replacing ill-formed UTF-8 byte sequences</span></span>](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences) | <span data-ttu-id="23a5e-119">3.0</span><span class="sxs-lookup"><span data-stu-id="23a5e-119">3.0</span></span> |
| [<span data-ttu-id="23a5e-120">TypeDescriptionProviderAttribute movido para outro conjunto</span><span class="sxs-lookup"><span data-stu-id="23a5e-120">TypeDescriptionProviderAttribute moved to another assembly</span></span>](#typedescriptionproviderattribute-moved-to-another-assembly) | <span data-ttu-id="23a5e-121">3.0</span><span class="sxs-lookup"><span data-stu-id="23a5e-121">3.0</span></span> |
| [<span data-ttu-id="23a5e-122">ZipArchiveEntry não lida mais com arquivos com tamanhos de entrada inconsistentes</span><span class="sxs-lookup"><span data-stu-id="23a5e-122">ZipArchiveEntry no longer handles archives with inconsistent entry sizes</span></span>](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | <span data-ttu-id="23a5e-123">3.0</span><span class="sxs-lookup"><span data-stu-id="23a5e-123">3.0</span></span> |
| [<span data-ttu-id="23a5e-124">O tipo de exceção do serializador JSON mudou de JsonException para NotSupportedException</span><span class="sxs-lookup"><span data-stu-id="23a5e-124">JSON serializer exception type changed from JsonException to NotSupportedException</span></span>](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | <span data-ttu-id="23a5e-125">3.0</span><span class="sxs-lookup"><span data-stu-id="23a5e-125">3.0</span></span> |
| [<span data-ttu-id="23a5e-126">Mudança na semântica de (string)nula em Utf8JsonWriter</span><span class="sxs-lookup"><span data-stu-id="23a5e-126">Change in semantics of (string)null in Utf8JsonWriter</span></span>](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | <span data-ttu-id="23a5e-127">3.0</span><span class="sxs-lookup"><span data-stu-id="23a5e-127">3.0</span></span> |
| [<span data-ttu-id="23a5e-128">Os métodos JsonEncodedText.Encode têm um argumento adicional do JavaScriptEncoder</span><span class="sxs-lookup"><span data-stu-id="23a5e-128">JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument</span></span>](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | <span data-ttu-id="23a5e-129">3.0</span><span class="sxs-lookup"><span data-stu-id="23a5e-129">3.0</span></span> |
| [<span data-ttu-id="23a5e-130">JsonFactoryConverter.CreateConverter assinatura alterada</span><span class="sxs-lookup"><span data-stu-id="23a5e-130">JsonFactoryConverter.CreateConverter signature changed</span></span>](#jsonfactoryconvertercreateconverter-signature-changed) | <span data-ttu-id="23a5e-131">3.0</span><span class="sxs-lookup"><span data-stu-id="23a5e-131">3.0</span></span> |
| [<span data-ttu-id="23a5e-132">Mudanças na API do JsonElement</span><span class="sxs-lookup"><span data-stu-id="23a5e-132">JsonElement API changes</span></span>](#jsonelement-api-changes) | <span data-ttu-id="23a5e-133">3.0</span><span class="sxs-lookup"><span data-stu-id="23a5e-133">3.0</span></span> |
| [<span data-ttu-id="23a5e-134">FieldInfo.SetValue lança exceção para campos estáticos e somente somente init</span><span class="sxs-lookup"><span data-stu-id="23a5e-134">FieldInfo.SetValue throws exception for static, init-only fields</span></span>](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | <span data-ttu-id="23a5e-135">3.0</span><span class="sxs-lookup"><span data-stu-id="23a5e-135">3.0</span></span> |
| [<span data-ttu-id="23a5e-136">Campos privados adicionados aos tipos de estrutura embutidos</span><span class="sxs-lookup"><span data-stu-id="23a5e-136">Private fields added to built-in struct types</span></span>](#private-fields-added-to-built-in-struct-types) | <span data-ttu-id="23a5e-137">2.1</span><span class="sxs-lookup"><span data-stu-id="23a5e-137">2.1</span></span> |
| [<span data-ttu-id="23a5e-138">Alterar o valor padrão do UseShellExecute</span><span class="sxs-lookup"><span data-stu-id="23a5e-138">Change in default value of UseShellExecute</span></span>](#change-in-default-value-of-useshellexecute) | <span data-ttu-id="23a5e-139">2.1</span><span class="sxs-lookup"><span data-stu-id="23a5e-139">2.1</span></span> |
| [<span data-ttu-id="23a5e-140">Versões openSSL no macOS</span><span class="sxs-lookup"><span data-stu-id="23a5e-140">OpenSSL versions on macOS</span></span>](#openssl-versions-on-macos) | <span data-ttu-id="23a5e-141">2.1</span><span class="sxs-lookup"><span data-stu-id="23a5e-141">2.1</span></span> |
| [<span data-ttu-id="23a5e-142">Não autorizadoAccessException lançado por FileSystemInfo.Attributes</span><span class="sxs-lookup"><span data-stu-id="23a5e-142">UnauthorizedAccessException thrown by FileSystemInfo.Attributes</span></span>](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | <span data-ttu-id="23a5e-143">1.0</span><span class="sxs-lookup"><span data-stu-id="23a5e-143">1.0</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="23a5e-144">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="23a5e-144">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="23a5e-145">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="23a5e-145">.NET Core 2.1</span></span>

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a><span data-ttu-id="23a5e-146">.NET Core 1.0</span><span class="sxs-lookup"><span data-stu-id="23a5e-146">.NET Core 1.0</span></span>

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***
