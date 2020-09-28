---
title: Alterações significativas de criptografia
description: Lista alterações significativas relacionadas à criptografia no .NET Core.
ms.date: 04/22/2020
ms.openlocfilehash: 667d983fc6f2592c2169f97d328cd7947c8bcc81
ms.sourcegitcommit: 1274a1a4a4c7e2eaf56b38da76ef7cec789726ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/28/2020
ms.locfileid: "91406135"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="14317-103">Alterações significativas de criptografia</span><span class="sxs-lookup"><span data-stu-id="14317-103">Cryptography breaking changes</span></span>

<span data-ttu-id="14317-104">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="14317-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="14317-105">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="14317-105">Breaking change</span></span> | <span data-ttu-id="14317-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="14317-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="14317-107">APIs de System. Security. Cryptography não têm suporte no Webassembly de mais incrivelmente</span><span class="sxs-lookup"><span data-stu-id="14317-107">System.Security.Cryptography APIs not supported on Blazor WebAssembly</span></span>](#systemsecuritycryptography-apis-not-supported-on-blazor-webassembly) | <span data-ttu-id="14317-108">5,0</span><span class="sxs-lookup"><span data-stu-id="14317-108">5.0</span></span> |
| [<span data-ttu-id="14317-109">System. Security. Cryptography. OID é funcionalmente somente init</span><span class="sxs-lookup"><span data-stu-id="14317-109">System.Security.Cryptography.Oid is functionally init-only</span></span>](#systemsecuritycryptographyoid-is-functionally-init-only) | <span data-ttu-id="14317-110">5,0</span><span class="sxs-lookup"><span data-stu-id="14317-110">5.0</span></span> |
| [<span data-ttu-id="14317-111">A sintaxe de certificado confiável de início não é mais suportada no Linux</span><span class="sxs-lookup"><span data-stu-id="14317-111">BEGIN TRUSTED CERTIFICATE syntax no longer supported on Linux</span></span>](#begin-trusted-certificate-syntax-no-longer-supported-for-root-certificates-on-linux) | <span data-ttu-id="14317-112">3.0</span><span class="sxs-lookup"><span data-stu-id="14317-112">3.0</span></span> |
| [<span data-ttu-id="14317-113">EnvelopedCms usa como padrão a criptografia AES-256</span><span class="sxs-lookup"><span data-stu-id="14317-113">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="14317-114">3.0</span><span class="sxs-lookup"><span data-stu-id="14317-114">3.0</span></span> |
| [<span data-ttu-id="14317-115">O tamanho mínimo para geração de chave RSAOpenSsl aumentou</span><span class="sxs-lookup"><span data-stu-id="14317-115">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="14317-116">3.0</span><span class="sxs-lookup"><span data-stu-id="14317-116">3.0</span></span> |
| [<span data-ttu-id="14317-117">O .NET Core 3,0 prefere o OpenSSL 1.1. x ao OpenSSL 1.0. x</span><span class="sxs-lookup"><span data-stu-id="14317-117">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="14317-118">3.0</span><span class="sxs-lookup"><span data-stu-id="14317-118">3.0</span></span> |
| [<span data-ttu-id="14317-119">CryptoStream. Dispose transforma o bloco final somente durante a gravação</span><span class="sxs-lookup"><span data-stu-id="14317-119">CryptoStream.Dispose transforms final block only when writing</span></span>](#cryptostreamdispose-transforms-final-block-only-when-writing) | <span data-ttu-id="14317-120">3.0</span><span class="sxs-lookup"><span data-stu-id="14317-120">3.0</span></span> |
| [<span data-ttu-id="14317-121">O parâmetro booliano de SignedCms. ComputeSignature é respeitado</span><span class="sxs-lookup"><span data-stu-id="14317-121">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="14317-122">2.1</span><span class="sxs-lookup"><span data-stu-id="14317-122">2.1</span></span> |

## <a name="net-50"></a><span data-ttu-id="14317-123">.NET 5,0</span><span class="sxs-lookup"><span data-stu-id="14317-123">.NET 5.0</span></span>

[!INCLUDE[Cryptography APIs not supported on Blazor WebAssembly](~/includes/core-changes/cryptography/5.0/cryptography-apis-not-supported-on-blazor-webassembly.md)]

***

[!INCLUDE [cryptography-oid-init-only](../../../includes/core-changes/cryptography/5.0/cryptography-oid-init-only.md)]

***

## <a name="net-core-30"></a><span data-ttu-id="14317-124">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="14317-124">.NET Core 3.0</span></span>

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

## <a name="net-core-21"></a><span data-ttu-id="14317-125">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="14317-125">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
