---
title: Alterações significativas de criptografia
description: Lista alterações significativas relacionadas à criptografia no .NET Core.
ms.date: 04/22/2020
ms.openlocfilehash: b755876624a7709cfe08b5993655e78be9f8e1f2
ms.sourcegitcommit: 4a938327bad8b2e20cabd0f46a9dc50882596f13
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/28/2020
ms.locfileid: "92888601"
---
# <a name="cryptography-breaking-changes"></a>Alterações significativas de criptografia

As seguintes alterações significativas estão documentadas nesta página:

| Alteração significativa | Versão introduzida |
| - | :-: |
| [Valor de FeedbackSize padrão para instâncias criadas por TripleDES. Create alterado](#default-feedbacksize-value-for-instances-created-by-tripledescreate-changed) | 5.0 |
| [Não há suporte para a instanciação de implementações padrão de abstrações criptográficas](#instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported) | 5.0 |
| [Conjuntos de codificação TLS padrão para .NET no Linux](#default-tls-cipher-suites-for-net-on-linux) | 5.0 |
| [APIs de System. Security. Cryptography não têm suporte no Webassembly de mais incrivelmente](#systemsecuritycryptography-apis-not-supported-on-blazor-webassembly) | 5.0 |
| [System. Security. Cryptography. OID é funcionalmente somente init](#systemsecuritycryptographyoid-is-functionally-init-only) | 5.0 |
| [A sintaxe de certificado confiável de início não é mais suportada no Linux](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | 3.0 |
| [EnvelopedCms usa como padrão a criptografia AES-256](#envelopedcms-defaults-to-aes-256-encryption) | 3.0 |
| [O tamanho mínimo para geração de chave RSAOpenSsl aumentou](#minimum-size-for-rsaopenssl-key-generation-has-increased) | 3.0 |
| [O .NET Core 3,0 prefere o OpenSSL 1.1. x ao OpenSSL 1.0. x](#net-core-30-prefers-openssl-11x-to-openssl-10x) | 3.0 |
| [CryptoStream. Dispose transforma o bloco final somente durante a gravação](#cryptostreamdispose-transforms-final-block-only-when-writing) | 3.0 |
| [O parâmetro booliano de SignedCms. ComputeSignature é respeitado](#boolean-parameter-of-signedcmscomputesignature-is-respected) | 2.1 |

## <a name="net-50"></a>.NET 5,0

[!INCLUDE [tripledes-default-feedback-size-change](../../../includes/core-changes/cryptography/5.0/tripledes-default-feedback-size-change.md)]

***

[!INCLUDE [instantiating-default-implementations-of-cryptographic-abstractions-not-supported](../../../includes/core-changes/cryptography/5.0/instantiating-default-implementations-of-cryptographic-abstractions-not-supported.md)]

**_

[!INCLUDE [default-cipher-suites-for-tls-on-linux](../../../includes/core-changes/cryptography/5.0/default-cipher-suites-for-tls-on-linux.md)]

_*_

[!INCLUDE[Cryptography APIs not supported on Blazor WebAssembly](~/includes/core-changes/cryptography/5.0/cryptography-apis-not-supported-on-blazor-webassembly.md)]

_*_

[!INCLUDE [cryptography-oid-init-only](../../../includes/core-changes/cryptography/5.0/cryptography-oid-init-only.md)]

_*_

## <a name="net-core-30"></a>.NET Core 3.0

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

_*_

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

_*_

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

_*_

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

_*_

[!INCLUDE [CryptoStream.Dispose transforms final block only when writing](~/includes/core-changes/cryptography/3.0/cryptography-cryptostream-dispose-final-block-write.md)]

_*_

## <a name="net-core-21"></a>.NET Core 2.1

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

_**
