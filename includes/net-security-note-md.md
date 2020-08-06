---
ms.openlocfilehash: 8b0edd9a49ca431355ab4f57fa041c5d1756d7eb
ms.sourcegitcommit: c37e8d4642fef647ebab0e1c618ecc29ddfe2a0f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/06/2020
ms.locfileid: "87855654"
---
> [!CAUTION]
> <span data-ttu-id="fd00d-101">CAS (segurança de acesso a código) e código parcialmente confiável</span><span class="sxs-lookup"><span data-stu-id="fd00d-101">Code Access Security (CAS) and Partially Trusted Code</span></span>
>
> <span data-ttu-id="fd00d-102">O .NET Framework fornece um mecanismo para a imposição de níveis variáveis de confiança em códigos diferentes em execução no mesmo aplicativo chamado CAS (Segurança de Acesso do Código).</span><span class="sxs-lookup"><span data-stu-id="fd00d-102">The .NET Framework provides a mechanism for the enforcement of varying levels of trust on different code running in the same application called Code Access Security (CAS).</span></span>
>
> <span data-ttu-id="fd00d-103">**Não há suporte para CAS no .NET Core, no .NET 5 ou em versões posteriores. Não há suporte para CAS em versões do C# posteriores a 7,0.**</span><span class="sxs-lookup"><span data-stu-id="fd00d-103">**CAS is not supported in .NET Core, .NET 5, or later versions. CAS is not supported by versions of C# later than 7.0.**</span></span>
>
> <span data-ttu-id="fd00d-104">As CAS no .NET Framework não devem ser usadas como um mecanismo para impor limites de segurança com base na origem do código ou em outros aspectos de identidade.</span><span class="sxs-lookup"><span data-stu-id="fd00d-104">CAS in .NET Framework should not be used as a mechanism for enforcing security boundaries based on code origination or other identity aspects.</span></span> <span data-ttu-id="fd00d-105">O CAS e o código Transparent Security não têm suporte como um limite de segurança com código parcialmente confiável, especialmente código de origem desconhecida.</span><span class="sxs-lookup"><span data-stu-id="fd00d-105">CAS and Security-Transparent Code are not supported as a security boundary with partially trusted code, especially code of unknown origin.</span></span> <span data-ttu-id="fd00d-106">Não aconselhamos carregar e executar códigos de origens desconhecidas sem a adoção de medidas de segurança alternativas no local.</span><span class="sxs-lookup"><span data-stu-id="fd00d-106">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span>
>
> <span data-ttu-id="fd00d-107">Essa política é aplicável à todas as versões do .NET Framework, mas não é aplicável ao .NET Framework incluído no Silverlight.</span><span class="sxs-lookup"><span data-stu-id="fd00d-107">This policy applies to all versions of .NET Framework, but does not apply to the .NET Framework included in Silverlight.</span></span>
