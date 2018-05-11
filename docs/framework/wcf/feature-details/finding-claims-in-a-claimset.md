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
ms.openlocfilehash: 7ca22d701277e71e509e6b291eb59a0223a0250c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="finding-claims-in-a-claimset"></a><span data-ttu-id="942fb-102">Encontrando declarações em um ClaimSet</span><span class="sxs-lookup"><span data-stu-id="942fb-102">Finding Claims in a ClaimSet</span></span>
<span data-ttu-id="942fb-103">Examinando o conteúdo de um <xref:System.IdentityModel.Claims.ClaimSet> para determinados tipos de declarações é uma tarefa comum ao usar a autorização baseada em declarações.</span><span class="sxs-lookup"><span data-stu-id="942fb-103">Examining the content of a <xref:System.IdentityModel.Claims.ClaimSet> for particular types of claims is a common task when using claim-based authorization.</span></span> <span data-ttu-id="942fb-104">Para examinar uma <xref:System.IdentityModel.Claims.ClaimSet> a presença de declarações específicas, use o <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> método.</span><span class="sxs-lookup"><span data-stu-id="942fb-104">To examine a <xref:System.IdentityModel.Claims.ClaimSet> for the presence of particular claims, use the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> method.</span></span> <span data-ttu-id="942fb-105">Esse método fornece melhor desempenho que iterando diretamente a <xref:System.IdentityModel.Claims.ClaimSet>.</span><span class="sxs-lookup"><span data-stu-id="942fb-105">This method provides better performance than iterating directly over the <xref:System.IdentityModel.Claims.ClaimSet>.</span></span> <span data-ttu-id="942fb-106">O exemplo a seguir demonstra esse uso.</span><span class="sxs-lookup"><span data-stu-id="942fb-106">The following example demonstrates this usage.</span></span> <span data-ttu-id="942fb-107">Observe que o `claimType` e `claimRight` parâmetros podem ser `null`.</span><span class="sxs-lookup"><span data-stu-id="942fb-107">Note that the `claimType` and `claimRight` parameters can be `null`.</span></span> <span data-ttu-id="942fb-108">Nesse caso, os parâmetros serão corresponde a todos os tipos de declaração e declaração de direitos.</span><span class="sxs-lookup"><span data-stu-id="942fb-108">In that case, the parameters will match all claim types and claim rights.</span></span>  
  
## <a name="example"></a><span data-ttu-id="942fb-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="942fb-109">Example</span></span>  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="942fb-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="942fb-110">See Also</span></span>  
 [<span data-ttu-id="942fb-111">Gerenciando reivindicações e autorização com o modelo de identidade</span><span class="sxs-lookup"><span data-stu-id="942fb-111">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
