---
ms.openlocfilehash: b7b16e39fa5df9732fa769f2bcd3696dff3b2a49
ms.sourcegitcommit: cbacb5d2cebbf044547f6af6e74a9de866800985
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/05/2020
ms.locfileid: "89496879"
---
### <a name="rsacngverifyhash-now-returns-false-for-any-verification-failure"></a><span data-ttu-id="fe1c2-101">RSACng.VerifyHash agora retorna False para qualquer falha de verificação</span><span class="sxs-lookup"><span data-stu-id="fe1c2-101">RSACng.VerifyHash now returns False for any verification failure</span></span>

#### <a name="details"></a><span data-ttu-id="fe1c2-102">Detalhes</span><span class="sxs-lookup"><span data-stu-id="fe1c2-102">Details</span></span>

<span data-ttu-id="fe1c2-103">A partir do .NET Framework 4.6.2, esse método retornará **False** se a assinatura em si estiver incorretamente formatada.</span><span class="sxs-lookup"><span data-stu-id="fe1c2-103">Starting with the .NET Framework 4.6.2, this method returns **False** if the signature itself is badly formatted.</span></span> <span data-ttu-id="fe1c2-104">Agora, ele retornará false para qualquer falha de verificação. No .NET Framework 4.6 e 4.6.1, o método gera <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> se a assinatura em si está incorretamente formatada.</span><span class="sxs-lookup"><span data-stu-id="fe1c2-104">It now returns false for any verification failure.In the .NET Framework 4.6 and 4.6.1, the method throws a <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> if the signature itself is badly formatted.</span></span>

#### <a name="suggestion"></a><span data-ttu-id="fe1c2-105">Sugestão</span><span class="sxs-lookup"><span data-stu-id="fe1c2-105">Suggestion</span></span>

<span data-ttu-id="fe1c2-106">Qualquer código cuja execução dependa da identificação de <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> deverá ser executado se a validação falhar e o método retornar **False**.</span><span class="sxs-lookup"><span data-stu-id="fe1c2-106">Any code whose execution depends on handling the <xref:System.Security.Cryptography.CryptographicException?displayProperty=fullName> should instead execute if validation fails and the method returns **False**.</span></span>

| <span data-ttu-id="fe1c2-107">Nome</span><span class="sxs-lookup"><span data-stu-id="fe1c2-107">Name</span></span>    | <span data-ttu-id="fe1c2-108">Valor</span><span class="sxs-lookup"><span data-stu-id="fe1c2-108">Value</span></span>       |
|:--------|:------------|
| <span data-ttu-id="fe1c2-109">Escopo</span><span class="sxs-lookup"><span data-stu-id="fe1c2-109">Scope</span></span>   |<span data-ttu-id="fe1c2-110">Secundária</span><span class="sxs-lookup"><span data-stu-id="fe1c2-110">Minor</span></span>|
|<span data-ttu-id="fe1c2-111">Versão</span><span class="sxs-lookup"><span data-stu-id="fe1c2-111">Version</span></span>|<span data-ttu-id="fe1c2-112">4.6.2</span><span class="sxs-lookup"><span data-stu-id="fe1c2-112">4.6.2</span></span>|
|<span data-ttu-id="fe1c2-113">Tipo</span><span class="sxs-lookup"><span data-stu-id="fe1c2-113">Type</span></span>|<span data-ttu-id="fe1c2-114">Runtime</span><span class="sxs-lookup"><span data-stu-id="fe1c2-114">Runtime</span></span>|

#### <a name="affected-apis"></a><span data-ttu-id="fe1c2-115">APIs afetadas</span><span class="sxs-lookup"><span data-stu-id="fe1c2-115">Affected APIs</span></span>

- <xref:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)?displayProperty=nameWithType>

<!--

#### Affected APIs

- `M:System.Security.Cryptography.RSACng.VerifyHash(System.Byte[],System.Byte[],System.Security.Cryptography.HashAlgorithmName,System.Security.Cryptography.RSASignaturePadding)`

-->
