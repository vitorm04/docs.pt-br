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
# <a name="core-net-libraries-breaking-changes"></a>Bibliotecas Core .NET quebrando alterações

As bibliotecas .NET principais fornecem os primitivos e outros tipos gerais usados pelo .NET Core.

As seguintes alterações de quebra estão documentadas nesta página:

| Mudança de ruptura | Versão introduzida |
| - | :-: |
| [APIs que relatam versão agora relatam produto e não versão de arquivo](#apis-that-report-version-now-report-product-and-not-file-version) | 3.0 |
| [As instâncias de EncoderFallbackBuffer personalizadas não podem recuar recursivamente](#custom-encoderfallbackbuffer-instances-cannot-fall-back-recursively) | 3.0 |
| [Formatação de pontos flutuantes e mudanças de comportamento de análise](#floating-point-formatting-and-parsing-behavior-changed) | 3.0 |
| [As operações de análise de ponto flutuante não falham mais ou lançam uma Exceção de Estouro](#floating-point-parsing-operations-no-longer-fail-or-throw-an-overflowexception) | 3.0 |
| [InvalidAsynchronousStateException mudou-se para outro conjunto](#invalidasynchronousstateexception-moved-to-another-assembly) | 3.0 |
| [Net Core 3.0 segue as melhores práticas da Unicode ao substituir sequências de bytes UTF-8 mal formadas](#net-core-30-follows-unicode-best-practices-when-replacing-ill-formed-utf-8-byte-sequences) | 3.0 |
| [TypeDescriptionProviderAttribute movido para outro conjunto](#typedescriptionproviderattribute-moved-to-another-assembly) | 3.0 |
| [ZipArchiveEntry não lida mais com arquivos com tamanhos de entrada inconsistentes](#ziparchiveentry-no-longer-handles-archives-with-inconsistent-entry-sizes) | 3.0 |
| [O tipo de exceção do serializador JSON mudou de JsonException para NotSupportedException](#json-serializer-exception-type-changed-from-jsonexception-to-notsupportedexception) | 3.0 |
| [Mudança na semântica de (string)nula em Utf8JsonWriter](#change-in-semantics-of-stringnull-in-utf8jsonwriter) | 3.0 |
| [Os métodos JsonEncodedText.Encode têm um argumento adicional do JavaScriptEncoder](#jsonencodedtextencode-methods-have-an-additional-javascriptencoder-argument) | 3.0 |
| [JsonFactoryConverter.CreateConverter assinatura alterada](#jsonfactoryconvertercreateconverter-signature-changed) | 3.0 |
| [Mudanças na API do JsonElement](#jsonelement-api-changes) | 3.0 |
| [FieldInfo.SetValue lança exceção para campos estáticos e somente somente init](#fieldinfosetvalue-throws-exception-for-static-init-only-fields) | 3.0 |
| [Campos privados adicionados aos tipos de estrutura embutidos](#private-fields-added-to-built-in-struct-types) | 2.1 |
| [Alterar o valor padrão do UseShellExecute](#change-in-default-value-of-useshellexecute) | 2.1 |
| [Versões openSSL no macOS](#openssl-versions-on-macos) | 2.1 |
| [Não autorizadoAccessException lançado por FileSystemInfo.Attributes](#unauthorizedaccessexception-thrown-by-filesysteminfoattributes) | 1.0 |

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

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE[Private fields added to built-in struct types](~/includes/core-changes/corefx/2.1/instantiate-struct.md)]

***

[!INCLUDE[Change in default value of UseShellExecute](~/includes/core-changes/corefx/2.1/process-start-changes.md)]

***

[!INCLUDE [OpenSSL versions on macOS](../../../includes/core-changes/corefx/openssl-dependencies-macos.md)]

***

## <a name="net-core-10"></a>.NET Core 1.0

[!INCLUDE [UnauthorizedAccessException thrown by FileSystemInfo.Attributes](~/includes/core-changes/corefx/1.0/filesysteminfo-attributes-exceptions.md)]

***
