---
title: Encontrando declarações em um ClaimSet
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- claims [WCF], finding in a claimset
- claims [WCF]
ms.assetid: a76ce107-aeb3-47d0-bfa9-134c53664e20
ms.openlocfilehash: 42e6ee682220913f872da337eb41f6c290082988
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59137118"
---
# <a name="finding-claims-in-a-claimset"></a><span data-ttu-id="aa85d-102">Encontrando declarações em um ClaimSet</span><span class="sxs-lookup"><span data-stu-id="aa85d-102">Finding Claims in a ClaimSet</span></span>
<span data-ttu-id="aa85d-103">Examinando o conteúdo de um <xref:System.IdentityModel.Claims.ClaimSet> para determinados tipos de declarações é uma tarefa comum ao usar a autorização baseada em declarações.</span><span class="sxs-lookup"><span data-stu-id="aa85d-103">Examining the content of a <xref:System.IdentityModel.Claims.ClaimSet> for particular types of claims is a common task when using claim-based authorization.</span></span> <span data-ttu-id="aa85d-104">Para examinar uma <xref:System.IdentityModel.Claims.ClaimSet> quanto à presença de declarações específicas, use o <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> método.</span><span class="sxs-lookup"><span data-stu-id="aa85d-104">To examine a <xref:System.IdentityModel.Claims.ClaimSet> for the presence of particular claims, use the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> method.</span></span> <span data-ttu-id="aa85d-105">Esse método fornece melhor desempenho que iterando diretamente o <xref:System.IdentityModel.Claims.ClaimSet>.</span><span class="sxs-lookup"><span data-stu-id="aa85d-105">This method provides better performance than iterating directly over the <xref:System.IdentityModel.Claims.ClaimSet>.</span></span> <span data-ttu-id="aa85d-106">O exemplo a seguir demonstra esse uso.</span><span class="sxs-lookup"><span data-stu-id="aa85d-106">The following example demonstrates this usage.</span></span> <span data-ttu-id="aa85d-107">Observe que o `claimType` e `claimRight` parâmetros podem ser `null`.</span><span class="sxs-lookup"><span data-stu-id="aa85d-107">Note that the `claimType` and `claimRight` parameters can be `null`.</span></span> <span data-ttu-id="aa85d-108">Nesse caso, os parâmetros serão corresponde a todos os tipos de declaração e de declaração de direitos.</span><span class="sxs-lookup"><span data-stu-id="aa85d-108">In that case, the parameters will match all claim types and claim rights.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa85d-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="aa85d-109">Example</span></span>  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="aa85d-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="aa85d-110">See also</span></span>

- [<span data-ttu-id="aa85d-111">Gerenciando reivindicações e autorização com o modelo de identidade</span><span class="sxs-lookup"><span data-stu-id="aa85d-111">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
