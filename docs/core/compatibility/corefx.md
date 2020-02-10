---
title: Alterações significativas na biblioteca de classes base
description: Lista as alterações significativas no .NET CoreFx, a biblioteca de classes base.
ms.date: 09/20/2019
ms.openlocfilehash: 9e8a00abfae8bf8f5301a4879cb5274492a2b6fd
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/09/2020
ms.locfileid: "77093078"
---
# <a name="corefx-breaking-changes"></a>CoreFx alterações significativas

O CoreFx fornece os primitivos e outros tipos gerais usados pelo .NET Core.

As seguintes alterações significativas estão documentadas nesta página:

- [As APIs que relatam versão agora relatam produto e não versão de arquivo](#apis-that-report-version-now-report-product-and-not-file-version)
- [Instâncias EncoderFallbackBuffer personalizadas não podem retornar recursivamente](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively)
- [Alterações de comportamento de análise e formatação de ponto flutuante](#floating-point-formatting-and-parsing-behavior-changed)
- [Operações de análise de ponto flutuante não falham mais ou geram uma estourexception](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception)
- [InvalidAsynchronousStateException movido para outro assembly](#invalidasynchronousstateexception-moved-to-another-assembly)
- [O NET Core 3,0 segue as práticas recomendadas de Unicode ao substituir sequências de bytes UTF-8 malformadas](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences)
- [TypeDescriptionProviderAttribute movido para outro assembly](#typedescriptionproviderattribute-moved-to-another-assembly)
- [O ZipArchiveEntry não lida mais com os arquivos mortos com tamanhos de entrada inconsistentes](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes)
- [Tipo de exceção de serializador JSON alterado de Jsonexception para NotSupportedException](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception)
- [Alteração na semântica de (String) NULL em Utf8JsonWriter](#change-in-semantics-of-stringnull-in-utf8jsonwriter)
- [Os métodos JsonEncodedText. Encode têm um argumento JavaScriptEncoder adicional](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument)
- [Assinatura de JsonFactoryConverter. Createconverter alterada](#jsonfactoryconvertercreateconverter-signature-changed)
- [Alterações da API jsonelement](#jsonelement-api-changes)
- [Campos privados adicionados aos tipos de struct internos](#private-fields-added-to-built-in-struct-types)
- [Alteração no valor padrão de UseShellExecute](#change-in-default-value-of-useshellexecute)

## <a name="net-core-30"></a>.NET Core 3.0

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

## <a name="net-core-30-preview-9"></a>.NET Core 3,0 Preview 9

[!INCLUDE[JSON serializer exception type changed from JsonException to NotSupportedException](~/includes/core-changes/corefx/3.0/serializer-throws-notsupportedexception.md)]

***

## <a name="net-core-30-preview-8"></a>.NET Core 3,0 Preview 8

[!INCLUDE[Change in semantics of (string)null in Utf8JsonWriter](~/includes/core-changes/corefx/3.0/change-in-null-in-utf8jsonwriter.md)]

***

[!INCLUDE[JsonEncodedText.Encode methods have an additional JavaScriptEncoder argument](~/includes/core-changes/corefx/3.0/jsonencodedtext-encode-has-additional-argument.md)]

***

[!INCLUDE[JsonFactoryConverter.CreateConverter signature changed](~/includes/core-changes/corefx/3.0/jsonfactoryconverter-createconverter.md)]

***

## <a name="net-core-30-preview-7"></a>.NET Core 3,0 Preview 7

[!INCLUDE[JsonElement API changes](~/includes/core-changes/corefx/3.0/jsonelement-api-changes.md)]

***

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***
