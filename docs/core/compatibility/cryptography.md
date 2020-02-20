---
title: Alterações significativas de criptografia
description: Lista alterações significativas relacionadas à criptografia no .NET Core.
ms.date: 02/10/2020
ms.openlocfilehash: c25eefa8e3ee01ed7a1df4ec4aa9225f2c347a4d
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/19/2020
ms.locfileid: "77449201"
---
# <a name="cryptography-breaking-changes"></a><span data-ttu-id="98788-103">Alterações significativas de criptografia</span><span class="sxs-lookup"><span data-stu-id="98788-103">Cryptography breaking changes</span></span>

<span data-ttu-id="98788-104">As seguintes alterações significativas estão documentadas nesta página:</span><span class="sxs-lookup"><span data-stu-id="98788-104">The following breaking changes are documented on this page:</span></span>

| <span data-ttu-id="98788-105">Alteração significativa</span><span class="sxs-lookup"><span data-stu-id="98788-105">Breaking change</span></span> | <span data-ttu-id="98788-106">Versão introduzida</span><span class="sxs-lookup"><span data-stu-id="98788-106">Version introduced</span></span> |
| - | :-: |
| [<span data-ttu-id="98788-107">EnvelopedCms usa como padrão a criptografia AES-256</span><span class="sxs-lookup"><span data-stu-id="98788-107">EnvelopedCms defaults to AES-256 encryption</span></span>](#envelopedcms-defaults-to-aes-256-encryption) | <span data-ttu-id="98788-108">3.0</span><span class="sxs-lookup"><span data-stu-id="98788-108">3.0</span></span> |
| [<span data-ttu-id="98788-109">O tamanho mínimo para geração de chave RSAOpenSsl aumentou</span><span class="sxs-lookup"><span data-stu-id="98788-109">Minimum size for RSAOpenSsl key generation has increased</span></span>](#minimum-size-for-rsaopenssl-key-generation-has-increased) | <span data-ttu-id="98788-110">3.0</span><span class="sxs-lookup"><span data-stu-id="98788-110">3.0</span></span> |
| [<span data-ttu-id="98788-111">O .NET Core 3,0 prefere o OpenSSL 1.1. x ao OpenSSL 1.0. x</span><span class="sxs-lookup"><span data-stu-id="98788-111">.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x</span></span>](#net-core-30-prefers-openssl-11x-to-openssl-10x) | <span data-ttu-id="98788-112">3.0</span><span class="sxs-lookup"><span data-stu-id="98788-112">3.0</span></span> |
| [<span data-ttu-id="98788-113">Melhor validação de argumento no Construtor Pkcs8PrivateKeyInfo</span><span class="sxs-lookup"><span data-stu-id="98788-113">Better argument validation in the Pkcs8PrivateKeyInfo constructor</span></span>](#better-argument-validation-in-the-pkcs8privatekeyinfo-constructor) | <span data-ttu-id="98788-114">3.0</span><span class="sxs-lookup"><span data-stu-id="98788-114">3.0</span></span> |
| [<span data-ttu-id="98788-115">O parâmetro booliano de SignedCms. ComputeSignature é respeitado</span><span class="sxs-lookup"><span data-stu-id="98788-115">Boolean parameter of SignedCms.ComputeSignature is respected</span></span>](#boolean-parameter-of-signedcmscomputesignature-is-respected) | <span data-ttu-id="98788-116">2.1</span><span class="sxs-lookup"><span data-stu-id="98788-116">2.1</span></span> |

## <a name="net-core-30"></a><span data-ttu-id="98788-117">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="98788-117">.NET Core 3.0</span></span>

[!INCLUDE[EnvelopedCms defaults to AES-256 encryption](~/includes/core-changes/cryptography/3.0/envelopedcms-defaults-to-aes256.md)]

***

[!INCLUDE[Minimum size for RSAOpenSsl key generation has increased](~/includes/core-changes/cryptography/3.0/minimum-rsaopenssl-key-size-change.md)]

***

[!INCLUDE[.NET Core 3.0 prefers OpenSSL 1.1.x to OpenSSL 1.0.x](~/includes/core-changes/cryptography/3.0/net-core-3-0-prefers-openssl-1-1-x.md)]

***

[!INCLUDE[Better argument validation in the Pkcs8PrivateKeyInfo constructor](~/includes/core-changes/cryptography/3.0/better-argument-validation-in-pkcs8privatekeyinfo-ctor.md)]

***

## <a name="net-core-21"></a><span data-ttu-id="98788-118">.NET Core 2.1</span><span class="sxs-lookup"><span data-stu-id="98788-118">.NET Core 2.1</span></span>

[!INCLUDE [Boolean parameter of SignedCms.ComputeSignature is respected](~/includes/core-changes/cryptography/2.1/compute-signature-silent-parameter.md)]

***
