---
ms.openlocfilehash: 7d60578ac2913037e1cdeda329f06f9a4986574d
ms.sourcegitcommit: d55e14eb63588830c0ba1ea95a24ce6c57ef8c8c
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/11/2019
ms.locfileid: "67857494"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="fb778-101">RSACng.VerifyHash agora retorna False para qualquer falha de verificação</span><span class="sxs-lookup"><span data-stu-id="fb778-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

|   |   |
|---|---|
|<span data-ttu-id="fb778-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="fb778-102">Details</span></span>|<span data-ttu-id="fb778-103">A partir do .NET Framework 4.6.2, esse método retornará <strong>False</strong> se a assinatura em si estiver incorretamente formatada.</span><span class="sxs-lookup"><span data-stu-id="fb778-103">Starting with the .NET Framework 4.6.2, this method returns <strong>False</strong> if the signature itself is badly formatted.</span></span> <span data-ttu-id="fb778-104">Agora, ele retornará false para qualquer falha de verificação. No .NET Framework 4.6 e 4.6.1, o método gera <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> se a assinatura em si está incorretamente formatada.</span><span class="sxs-lookup"><span data-stu-id="fb778-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> if the signature itself is badly formatted.</span></span>|
|<span data-ttu-id="fb778-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="fb778-105">Suggestion</span></span>|<span data-ttu-id="fb778-106">Qualquer código cuja execução dependa da identificação de <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> deverá ser executado se a validação falhar e o método retornar <strong>False</strong>.</span><span class="sxs-lookup"><span data-stu-id="fb778-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> should instead execute if validation fails and the method returns <strong>False</strong>.</span></span>|
|<span data-ttu-id="fb778-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="fb778-107">Scope</span></span>|<span data-ttu-id="fb778-108">Secundário</span><span class="sxs-lookup"><span data-stu-id="fb778-108">Minor</span></span>|
|<span data-ttu-id="fb778-109">Versão</span><span class="sxs-lookup"><span data-stu-id="fb778-109">Version</span></span>|<span data-ttu-id="fb778-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="fb778-110">4.6.2</span></span>|
|<span data-ttu-id="fb778-111">Tipo</span><span class="sxs-lookup"><span data-stu-id="fb778-111">Type</span></span>|<span data-ttu-id="fb778-112">Tempo de execução</span><span class="sxs-lookup"><span data-stu-id="fb778-112">Runtime</span></span>|
|<span data-ttu-id="fb778-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="fb778-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|

