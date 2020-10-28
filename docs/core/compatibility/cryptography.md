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
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="d80c8-103">Alterações significativas de criptografia</span><span class="sxs-lookup"><span data-stu-id="d80c8-103">Cryptography breaking changes</span></span>

<span data-ttu-id="d80c8-104">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="d80c8-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="d80c8-105">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="d80c8-105">Breaking change</span></span> | <span data-ttu-id="d80c8-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="d80c8-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="d80c8-107">Valor de FeedbackSize padrão para instâncias criadas por TripleDES. Create alterado</span><span class="sxs-lookup"><span data-stu-id="d80c8-107">Default FeedbackSize value for instances created by TripleDES.Create changed</span></span>](#default-feedbacksize-value-for-instances-created-by-tripledescreate-changed) | <span data-ttu-id="d80c8-108">5.0</span><span class="sxs-lookup"><span data-stu-id="d80c8-108">5.0</span></span> |
| [<span data-ttu-id="d80c8-109">Não há suporte para a instanciação de implementações padrão de abstrações criptográficas</span><span class="sxs-lookup"><span data-stu-id="d80c8-109">Instantiating default implementations of cryptographic abstractions is not supported</span></span>](#instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported) | <span data-ttu-id="d80c8-110">5.0</span><span class="sxs-lookup"><span data-stu-id="d80c8-110">5.0</span></span> |
| [<span data-ttu-id="d80c8-111">Conjuntos de codificação TLS padrão para .NET no Linux</span><span class="sxs-lookup"><span data-stu-id="d80c8-111">Default TLS cipher suites for .NET on Linux</span></span>](#default-tls-cipher-suites-for-net-on-linux) | <span data-ttu-id="d80c8-112">5.0</span><span class="sxs-lookup"><span data-stu-id="d80c8-112">5.0</span></span> |
| [<span data-ttu-id="d80c8-113">APIs de System. Security. Cryptography não têm suporte no Webassembly de mais incrivelmente</span><span class="sxs-lookup"><span data-stu-id="d80c8-113">System.Security.Cryptography APIs not supported on Blazor WebAssembly</span></span>](#systemsecuritycryptography-apis-not-supported-on-blazor-webassembly) | <span data-ttu-id="d80c8-114">5.0</span><span class="sxs-lookup"><span data-stu-id="d80c8-114">5.0</span></span> |
| [<span data-ttu-id="d80c8-115">System. Security. Cryptography. OID é funcionalmente somente init</span><span class="sxs-lookup"><span data-stu-id="d80c8-115">System.Security.Cryptography.Oid is functionally init-only</span></span>](#systemsecuritycryptographyoid-is-functionally-init-only) | <span data-ttu-id="d80c8-116">5.0</span><span class="sxs-lookup"><span data-stu-id="d80c8-116">5.0</span></span> |
| [<span data-ttu-id="d80c8-117">A sintaxe de certificado confiável de início não é mais suportada no Linux</span><span class="sxs-lookup"><span data-stu-id="d80c8-117">BEGIN TRUSTED CERTIFICATE syntax no longer supported on Linux</span></span>](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | <span data-ttu-id="d80c8-118">3.0</span><span class="sxs-lookup"><span data-stu-id="d80c8-118">3.0</span></span> |
| [<span data-ttu-id="d80c8-119">EnvelopedCms usa como padrão a criptografia AES-256</span><span class="sxs-lookup"><span data-stu-id="d80c8-119">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="d80c8-120">3.0</span><span class="sxs-lookup"><span data-stu-id="d80c8-120">3.0</span></span> |
| [<span data-ttu-id="d80c8-121">O tamanho mínimo para geração de chave RSAOpenSsl aumentou</span><span class="sxs-lookup"><span data-stu-id="d80c8-121">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="d80c8-122">3.0</span><span class="sxs-lookup"><span data-stu-id="d80c8-122">3.0</span></span> |
| [<span data-ttu-id="d80c8-123">O .NET Core 3,0 prefere o OpenSSL 1.1. x ao OpenSSL 1.0. x</span><span class="sxs-lookup"><span data-stu-id="d80c8-123">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="d80c8-124">3.0</span><span class="sxs-lookup"><span data-stu-id="d80c8-124">3.0</span></span> |
| [<span data-ttu-id="d80c8-125">CryptoStream. Dispose transforma o bloco final somente durante a gravação</span><span class="sxs-lookup"><span data-stu-id="d80c8-125">CryptoStream.Dispose transforms final block only when writing</span></span>](#cryptostreamdispose-transforms-final-block-only-when-writing) | <span data-ttu-id="d80c8-126">3.0</span><span class="sxs-lookup"><span data-stu-id="d80c8-126">3.0</span></span> |
| [<span data-ttu-id="d80c8-127">O parâmetro booliano de SignedCms. ComputeSignature é respeitado</span><span class="sxs-lookup"><span data-stu-id="d80c8-127">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="d80c8-128">2.1</span><span class="sxs-lookup"><span data-stu-id="d80c8-128">2.1</span></span> |

## <a name="net-50"></a><span data-ttu-id="d80c8-129">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="d80c8-129">.NET 5.0</span></span>

[!INCLUDE [tripledes-default-feedback-size-change](../../../includes/core-changes/cryptography/5.0/tripledes-default-feedback-size-change.md)]

***

[!INCLUDE [instantiating-default-implementations-of-cryptographic-abstractions-not-supported](../../../includes/core-changes/cryptography/5.0/instantiating-default-implementations-of-cryptographic-abstractions-not-supported.md)]

<span data-ttu-id="d80c8-130">\*\*_</span><span class="sxs-lookup"><span data-stu-id="d80c8-130">\*\*_</span></span>

[!INCLUDE [default-cipher-suites-for-tls-on-linux](../../../includes/core-changes/cryptography/5.0/default-cipher-suites-for-tls-on-linux.md)]

_*_

[!INCLUDE[Cryptography APIs not supported on Blazor WebAssembly](~/includes/core-changes/cryptography/5.0/cryptography-apis-not-supported-on-blazor-webassembly.md)]

_*_

[!INCLUDE [cryptography-oid-init-only](../../../includes/core-changes/cryptography/5.0/cryptography-oid-init-only.md)]

_*_

## <a name="net-core-30"></a><span data-ttu-id="d80c8-131">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="d80c8-131">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="d80c8-132">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="d80c8-132">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

<span data-ttu-id="d80c8-133">_\*\*</span><span class="sxs-lookup"><span data-stu-id="d80c8-133">_\*\*</span></span>
