---
title: Alterações significativas de criptografia
description: Lista alterações significativas relacionadas à criptografia no .NET Core.
ms.date: 04/22/2020
ms.openlocfilehash: 6f37e5caacadc276562e63a728162c6b26f2e435
ms.sourcegitcommit: ff5a4eb5cffbcac9521bc44a907a118cd7e8638d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/17/2020
ms.locfileid: "92159541"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="a1541-103">Alterações significativas de criptografia</span><span class="sxs-lookup"><span data-stu-id="a1541-103">Cryptography breaking changes</span></span>

<span data-ttu-id="a1541-104">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="a1541-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="a1541-105">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="a1541-105">Breaking change</span></span> | <span data-ttu-id="a1541-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="a1541-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="a1541-107">Não há suporte para a instanciação de implementações padrão de abstrações criptográficas</span><span class="sxs-lookup"><span data-stu-id="a1541-107">Instantiating default implementations of cryptographic abstractions is not supported</span></span>](#instantiating-default-implementations-of-cryptographic-abstractions-is-not-supported) | <span data-ttu-id="a1541-108">5.0</span><span class="sxs-lookup"><span data-stu-id="a1541-108">5.0</span></span> |
| [<span data-ttu-id="a1541-109">Conjuntos de codificação TLS padrão para .NET no Linux</span><span class="sxs-lookup"><span data-stu-id="a1541-109">Default TLS cipher suites for .NET on Linux</span></span>](#default-tls-cipher-suites-for-net-on-linux) | <span data-ttu-id="a1541-110">5.0</span><span class="sxs-lookup"><span data-stu-id="a1541-110">5.0</span></span> |
| [<span data-ttu-id="a1541-111">APIs de System. Security. Cryptography não têm suporte no Webassembly de mais incrivelmente</span><span class="sxs-lookup"><span data-stu-id="a1541-111">System.Security.Cryptography APIs not supported on Blazor WebAssembly</span></span>](#systemsecuritycryptography-apis-not-supported-on-blazor-webassembly) | <span data-ttu-id="a1541-112">5.0</span><span class="sxs-lookup"><span data-stu-id="a1541-112">5.0</span></span> |
| [<span data-ttu-id="a1541-113">System. Security. Cryptography. OID é funcionalmente somente init</span><span class="sxs-lookup"><span data-stu-id="a1541-113">System.Security.Cryptography.Oid is functionally init-only</span></span>](#systemsecuritycryptographyoid-is-functionally-init-only) | <span data-ttu-id="a1541-114">5.0</span><span class="sxs-lookup"><span data-stu-id="a1541-114">5.0</span></span> |
| [<span data-ttu-id="a1541-115">A sintaxe de certificado confiável de início não é mais suportada no Linux</span><span class="sxs-lookup"><span data-stu-id="a1541-115">BEGIN TRUSTED CERTIFICATE syntax no longer supported on Linux</span></span>](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | <span data-ttu-id="a1541-116">3.0</span><span class="sxs-lookup"><span data-stu-id="a1541-116">3.0</span></span> |
| [<span data-ttu-id="a1541-117">EnvelopedCms usa como padrão a criptografia AES-256</span><span class="sxs-lookup"><span data-stu-id="a1541-117">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="a1541-118">3.0</span><span class="sxs-lookup"><span data-stu-id="a1541-118">3.0</span></span> |
| [<span data-ttu-id="a1541-119">O tamanho mínimo para geração de chave RSAOpenSsl aumentou</span><span class="sxs-lookup"><span data-stu-id="a1541-119">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="a1541-120">3.0</span><span class="sxs-lookup"><span data-stu-id="a1541-120">3.0</span></span> |
| [<span data-ttu-id="a1541-121">O .NET Core 3,0 prefere o OpenSSL 1.1. x ao OpenSSL 1.0. x</span><span class="sxs-lookup"><span data-stu-id="a1541-121">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="a1541-122">3.0</span><span class="sxs-lookup"><span data-stu-id="a1541-122">3.0</span></span> |
| [<span data-ttu-id="a1541-123">CryptoStream. Dispose transforma o bloco final somente durante a gravação</span><span class="sxs-lookup"><span data-stu-id="a1541-123">CryptoStream.Dispose transforms final block only when writing</span></span>](#cryptostreamdispose-transforms-final-block-only-when-writing) | <span data-ttu-id="a1541-124">3.0</span><span class="sxs-lookup"><span data-stu-id="a1541-124">3.0</span></span> |
| [<span data-ttu-id="a1541-125">O parâmetro booliano de SignedCms. ComputeSignature é respeitado</span><span class="sxs-lookup"><span data-stu-id="a1541-125">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="a1541-126">2.1</span><span class="sxs-lookup"><span data-stu-id="a1541-126">2.1</span></span> |

## <a name="net-50"></a><span data-ttu-id="a1541-127">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="a1541-127">.NET 5.0</span></span>

[!INCLUDE [instantiating-default-implementations-of-cryptographic-abstractions-not-supported](../../../includes/core-changes/cryptography/5.0/instantiating-default-implementations-of-cryptographic-abstractions-not-supported.md)]

***

[!INCLUDE [default-cipher-suites-for-tls-on-linux](../../../includes/core-changes/cryptography/5.0/default-cipher-suites-for-tls-on-linux.md)]

***

[!INCLUDE[Cryptography APIs not supported on Blazor WebAssembly](~/includes/core-changes/cryptography/5.0/cryptography-apis-not-supported-on-blazor-webassembly.md)]

***

[!INCLUDE [cryptography-oid-init-only](../../../includes/core-changes/cryptography/5.0/cryptography-oid-init-only.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="a1541-128">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="a1541-128">.NET Core 3.0</span></span>

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

***

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

[!INCLUDE [CryptoStream.Dispose transforms final block only when writing](~/includes/core-changes/cryptography/3.0/cryptography-cryptostream-dispose-final-block-write.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="a1541-129">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="a1541-129">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
