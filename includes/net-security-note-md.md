---
ms.openlocfilehash: 3164233f1ac056de385faa119143d75d3c2dc50c
ms.sourcegitcommit: 67ebdb695fd017d79d9f1f7f35d145042d5a37f7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/20/2020
ms.locfileid: "92224338"
---
> [!CAUTION]
> <span data-ttu-id="98287-101">CAS (segurança de acesso a código) e código parcialmente confiável</span><span class="sxs-lookup"><span data-stu-id="98287-101">Code Access Security (CAS) and Partially Trusted Code</span></span>
>
> <span data-ttu-id="98287-102">O .NET Framework fornece um mecanismo para a imposição de níveis variáveis de confiança em códigos diferentes em execução no mesmo aplicativo chamado CAS (Segurança de Acesso do Código).</span><span class="sxs-lookup"><span data-stu-id="98287-102">The .NET Framework provides a mechanism for the enforcement of varying levels of trust on different code running in the same application called Code Access Security (CAS).</span></span>
>
> <span data-ttu-id="98287-103">**Não há suporte para CAS no .NET Core, no .NET 5 ou em versões posteriores. Não há suporte para CAS em versões do C# posteriores a 7,0.**</span><span class="sxs-lookup"><span data-stu-id="98287-103">**CAS is not supported in .NET Core, .NET 5, or later versions. CAS is not supported by versions of C# later than 7.0.**</span></span>
>
> <span data-ttu-id="98287-104">As CAS no .NET Framework não devem ser usadas como um mecanismo para impor limites de segurança com base na origem do código ou em outros aspectos de identidade.</span><span class="sxs-lookup"><span data-stu-id="98287-104">CAS in .NET Framework should not be used as a mechanism for enforcing security boundaries based on code origination or other identity aspects.</span></span> <span data-ttu-id="98287-105">Não há suporte para CAS e código de Security-Transparent como um limite de segurança com código parcialmente confiável, especialmente código de origem desconhecida.</span><span class="sxs-lookup"><span data-stu-id="98287-105">CAS and Security-Transparent Code are not supported as a security boundary with partially trusted code, especially code of unknown origin.</span></span> <span data-ttu-id="98287-106">Não aconselhamos carregar e executar códigos de origens desconhecidas sem a adoção de medidas de segurança alternativas no local.</span><span class="sxs-lookup"><span data-stu-id="98287-106">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span> <span data-ttu-id="98287-107">.NET Framework não emitirá patches de segurança para quaisquer explorações de elevação de privilégio que possam ser descobertas na área restrita do CAS.</span><span class="sxs-lookup"><span data-stu-id="98287-107">.NET Framework will not issue security patches for any elevation-of-privilege exploits that might be discovered against the CAS sandbox.</span></span>
>
> <span data-ttu-id="98287-108">Essa política é aplicável à todas as versões do .NET Framework, mas não é aplicável ao .NET Framework incluído no Silverlight.</span><span class="sxs-lookup"><span data-stu-id="98287-108">This policy applies to all versions of .NET Framework, but does not apply to the .NET Framework included in Silverlight.</span></span>
