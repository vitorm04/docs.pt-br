---
ms.openlocfilehash: 023b7d8c5aa9d435d3493935b4439ae4262c85bb
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/15/2019
ms.locfileid: "65671505"
---
> [!CAUTION]
>  <span data-ttu-id="ddd3a-101">Segurança de Acesso do Código e Código Parcialmente Confiável</span><span class="sxs-lookup"><span data-stu-id="ddd3a-101">Code Access Security and Partially Trusted Code</span></span>  
>   
>  <span data-ttu-id="ddd3a-102">O .NET Framework fornece um mecanismo para a imposição de níveis variáveis de confiança em códigos diferentes em execução no mesmo aplicativo chamado CAS (Segurança de Acesso do Código).</span><span class="sxs-lookup"><span data-stu-id="ddd3a-102">The .NET Framework provides a mechanism for the enforcement of varying levels of trust on different code running in the same application called Code Access Security (CAS).</span></span>  <span data-ttu-id="ddd3a-103">O CAS no .NET Framework não deve ser usado como um mecanismo de imposição de limites de segurança com base na origem do código ou em outros aspectos da identidade.</span><span class="sxs-lookup"><span data-stu-id="ddd3a-103">Code Access Security in .NET Framework should not  be used as a mechanism for enforcing security boundaries based on code origination or other identity aspects.</span></span> <span data-ttu-id="ddd3a-104">Estamos atualizando nossas diretrizes para refletir que o CAS e o Código Transparente de Segurança não terão suporte como um limite de segurança com código parcialmente confiável, especialmente o código de origem desconhecida.</span><span class="sxs-lookup"><span data-stu-id="ddd3a-104">We are updating our guidance to reflect that Code Access Security and Security-Transparent Code will not be supported as a security boundary with partially trusted code, especially code of unknown origin.</span></span> <span data-ttu-id="ddd3a-105">Não aconselhamos carregar e executar códigos de origens desconhecidas sem a adoção de medidas de segurança alternativas no local.</span><span class="sxs-lookup"><span data-stu-id="ddd3a-105">We advise against loading and executing code of unknown origins without putting alternative security measures in place.</span></span>  
>   
>  <span data-ttu-id="ddd3a-106">Essa política é aplicável à todas as versões do .NET Framework, mas não é aplicável ao .NET Framework incluído no Silverlight.</span><span class="sxs-lookup"><span data-stu-id="ddd3a-106">This policy applies to all versions of .NET Framework, but does not apply to the .NET Framework included in Silverlight.</span></span>
