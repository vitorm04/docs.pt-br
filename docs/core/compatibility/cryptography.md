---
title: Alterações significativas de criptografia
description: Lista alterações significativas relacionadas à criptografia no .NET Core.
ms.date: 04/22/2020
ms.openlocfilehash: f7d580938fb7620728b8ff7f67412c9f5bbbb6c3
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88557991"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="9ee1c-103">Alterações significativas de criptografia</span><span class="sxs-lookup"><span data-stu-id="9ee1c-103">Cryptography breaking changes</span></span>

<span data-ttu-id="9ee1c-104">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="9ee1c-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="9ee1c-105">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="9ee1c-105">Breaking change</span></span> | <span data-ttu-id="9ee1c-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="9ee1c-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="9ee1c-107">System. Security. Cryptography. OID é funcionalmente somente init</span><span class="sxs-lookup"><span data-stu-id="9ee1c-107">System.Security.Cryptography.Oid is functionally init-only</span></span>](#systemsecuritycryptographyoid-is-functionally-init-only) | <span data-ttu-id="9ee1c-108">5.0</span><span class="sxs-lookup"><span data-stu-id="9ee1c-108">5.0</span></span> |
| [<span data-ttu-id="9ee1c-109">A sintaxe de certificado confiável de início não é mais suportada no Linux</span><span class="sxs-lookup"><span data-stu-id="9ee1c-109">BEGIN TRUSTED CERTIFICATE syntax no longer supported on Linux</span></span>](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | <span data-ttu-id="9ee1c-110">3.0</span><span class="sxs-lookup"><span data-stu-id="9ee1c-110">3.0</span></span> |
| [<span data-ttu-id="9ee1c-111">EnvelopedCms usa como padrão a criptografia AES-256</span><span class="sxs-lookup"><span data-stu-id="9ee1c-111">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="9ee1c-112">3.0</span><span class="sxs-lookup"><span data-stu-id="9ee1c-112">3.0</span></span> |
| [<span data-ttu-id="9ee1c-113">O tamanho mínimo para geração de chave RSAOpenSsl aumentou</span><span class="sxs-lookup"><span data-stu-id="9ee1c-113">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="9ee1c-114">3.0</span><span class="sxs-lookup"><span data-stu-id="9ee1c-114">3.0</span></span> |
| [<span data-ttu-id="9ee1c-115">O .NET Core 3,0 prefere o OpenSSL 1.1. x ao OpenSSL 1.0. x</span><span class="sxs-lookup"><span data-stu-id="9ee1c-115">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="9ee1c-116">3.0</span><span class="sxs-lookup"><span data-stu-id="9ee1c-116">3.0</span></span> |
| [<span data-ttu-id="9ee1c-117">O parâmetro booliano de SignedCms. ComputeSignature é respeitado</span><span class="sxs-lookup"><span data-stu-id="9ee1c-117">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="9ee1c-118">2.1</span><span class="sxs-lookup"><span data-stu-id="9ee1c-118">2.1</span></span> |

## <a name="net-50"></a><span data-ttu-id="9ee1c-119">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="9ee1c-119">.NET 5.0</span></span>

[!INCLUDE [cryptography-oid-init-only](../../../includes/core-changes/cryptography/5.0/cryptography-oid-init-only.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="9ee1c-120">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="9ee1c-120">.NET Core 3.0</span></span>

[!INCLUDE [begin-trusted-cert-linux](~/includes/core-changes/cryptography/3.0/begin-trusted-cert-linux.md)]

***

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="9ee1c-121">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="9ee1c-121">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
