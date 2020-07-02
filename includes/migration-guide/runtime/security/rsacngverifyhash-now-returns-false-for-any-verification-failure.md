---
ms.openlocfilehash: fa5cf2280cdd9535962568a6272d047d261eeba5
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/01/2020
ms.locfileid: "85621016"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="86ae6-101">RSACng.VerifyHash agora retorna False para qualquer falha de verificação</span><span class="sxs-lookup"><span data-stu-id="86ae6-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

#### <a name="details"></a><span data-ttu-id="86ae6-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="86ae6-102">Details</span></span>

<span data-ttu-id="86ae6-103">A partir do .NET Framework 4.6.2, esse método retornará **False** se a assinatura em si estiver incorretamente formatada.</span><span class="sxs-lookup"><span data-stu-id="86ae6-103">Starting with the .NET Framework 4.6.2, this method returns **False** if the signature itself is badly formatted.</span></span> <span data-ttu-id="86ae6-104">Agora, ele retornará false para qualquer falha de verificação. No .NET Framework 4.6 e 4.6.1, o método gera <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> se a assinatura em si está incorretamente formatada.</span><span class="sxs-lookup"><span data-stu-id="86ae6-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> if the signature itself is badly formatted.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="86ae6-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="86ae6-105">Suggestion</span></span>

<span data-ttu-id="86ae6-106">Qualquer código cuja execução dependa da identificação de <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> deverá ser executado se a validação falhar e o método retornar **False**.</span><span class="sxs-lookup"><span data-stu-id="86ae6-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> should instead execute if validation fails and the method returns **False**.</span></span>

| <span data-ttu-id="86ae6-107">Name</span><span class="sxs-lookup"><span data-stu-id="86ae6-107">Name</span></span>    | <span data-ttu-id="86ae6-108">Valor</span><span class="sxs-lookup"><span data-stu-id="86ae6-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="86ae6-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="86ae6-109">Scope</span></span>   |<span data-ttu-id="86ae6-110">Secundária</span><span class="sxs-lookup"><span data-stu-id="86ae6-110">Minor</span></span>|
|<span data-ttu-id="86ae6-111">Versão</span><span class="sxs-lookup"><span data-stu-id="86ae6-111">Version</span></span>|<span data-ttu-id="86ae6-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="86ae6-112">4.6.2</span></span>|
|<span data-ttu-id="86ae6-113">Type</span><span class="sxs-lookup"><span data-stu-id="86ae6-113">Type</span></span>|<span data-ttu-id="86ae6-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="86ae6-114">Runtime</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="86ae6-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="86ae6-115">Affected APIs</span></span>

-<xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType></li></ul>|
