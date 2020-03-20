---
ms.openlocfilehash: fc315faef750d93d914104dd568078aa3fc430d4
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/15/2020
ms.locfileid: "72887722"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="857d1-101">RSACng.VerifyHash agora retorna False para qualquer falha de verificação</span><span class="sxs-lookup"><span data-stu-id="857d1-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

|   |   |
|---|---|
|<span data-ttu-id="857d1-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="857d1-102">Details</span></span>|<span data-ttu-id="857d1-103">A partir do .NET Framework 4.6.2, esse método retornará **False** se a assinatura em si estiver incorretamente formatada.</span><span class="sxs-lookup"><span data-stu-id="857d1-103">Starting with the .NET Framework 4.6.2, this method returns **False** if the signature itself is badly formatted.</span></span> <span data-ttu-id="857d1-104">Agora, ele retornará false para qualquer falha de verificação. No .NET Framework 4.6 e 4.6.1, o método gera <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> se a assinatura em si está incorretamente formatada.</span><span class="sxs-lookup"><span data-stu-id="857d1-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> if the signature itself is badly formatted.</span></span>|
|<span data-ttu-id="857d1-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="857d1-105">Suggestion</span></span>|<span data-ttu-id="857d1-106">Qualquer código cuja execução dependa da identificação de <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> deverá ser executado se a validação falhar e o método retornar **False**.</span><span class="sxs-lookup"><span data-stu-id="857d1-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> should instead execute if validation fails and the method returns **False**.</span></span>|
|<span data-ttu-id="857d1-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="857d1-107">Scope</span></span>|<span data-ttu-id="857d1-108">Secundária</span><span class="sxs-lookup"><span data-stu-id="857d1-108">Minor</span></span>|
|<span data-ttu-id="857d1-109">Versão</span><span class="sxs-lookup"><span data-stu-id="857d1-109">Version</span></span>|<span data-ttu-id="857d1-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="857d1-110">4.6.2</span></span>|
|<span data-ttu-id="857d1-111">Type</span><span class="sxs-lookup"><span data-stu-id="857d1-111">Type</span></span>|<span data-ttu-id="857d1-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="857d1-112">Runtime</span></span>|
|<span data-ttu-id="857d1-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="857d1-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
