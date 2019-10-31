---
ms.openlocfilehash: fc315faef750d93d914104dd568078aa3fc430d4
ms.sourcegitcommit: 337bdc5a463875daf2cc6883e5a2da97d56f5000
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/24/2019
ms.locfileid: "72887722"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="dafd1-101">RSACng.VerifyHash agora retorna False para qualquer falha de verificação</span><span class="sxs-lookup"><span data-stu-id="dafd1-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

|   |   |
|---|---|
|<span data-ttu-id="dafd1-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="dafd1-102">Details</span></span>|<span data-ttu-id="dafd1-103">A partir do .NET Framework 4.6.2, esse método retornará **False** se a assinatura em si estiver incorretamente formatada.</span><span class="sxs-lookup"><span data-stu-id="dafd1-103">Starting with the .NET Framework 4.6.2, this method returns **False** if the signature itself is badly formatted.</span></span> <span data-ttu-id="dafd1-104">Agora, ele retornará false para qualquer falha de verificação. No .NET Framework 4.6 e 4.6.1, o método gera <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> se a assinatura em si está incorretamente formatada.</span><span class="sxs-lookup"><span data-stu-id="dafd1-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> if the signature itself is badly formatted.</span></span>|
|<span data-ttu-id="dafd1-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="dafd1-105">Suggestion</span></span>|<span data-ttu-id="dafd1-106">Qualquer código cuja execução dependa da identificação de <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> deverá ser executado se a validação falhar e o método retornar **False**.</span><span class="sxs-lookup"><span data-stu-id="dafd1-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=name> should instead execute if validation fails and the method returns **False**.</span></span>|
|<span data-ttu-id="dafd1-107">Escopo</span><span class="sxs-lookup"><span data-stu-id="dafd1-107">Scope</span></span>|<span data-ttu-id="dafd1-108">Secundário</span><span class="sxs-lookup"><span data-stu-id="dafd1-108">Minor</span></span>|
|<span data-ttu-id="dafd1-109">Version</span><span class="sxs-lookup"><span data-stu-id="dafd1-109">Version</span></span>|<span data-ttu-id="dafd1-110">4.6.2</span><span class="sxs-lookup"><span data-stu-id="dafd1-110">4.6.2</span></span>|
|<span data-ttu-id="dafd1-111">Digite</span><span class="sxs-lookup"><span data-stu-id="dafd1-111">Type</span></span>|<span data-ttu-id="dafd1-112">Runtime</span><span class="sxs-lookup"><span data-stu-id="dafd1-112">Runtime</span></span>|
|<span data-ttu-id="dafd1-113">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="dafd1-113">Affected APIs</span></span>|<ul><li><xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
