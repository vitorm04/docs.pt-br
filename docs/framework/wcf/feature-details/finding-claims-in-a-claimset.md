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
ms.openlocfilehash: 1954da20d382630f965582fcc01bbaf72665720a
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/09/2020
ms.locfileid: "84595447"
---
# <a name="finding-claims-in-a-claimset"></a><span data-ttu-id="9271c-102">Encontrando declarações em um ClaimSet</span><span class="sxs-lookup"><span data-stu-id="9271c-102">Finding Claims in a ClaimSet</span></span>
<span data-ttu-id="9271c-103">Examinar o conteúdo de um <xref:System.IdentityModel.Claims.ClaimSet> para tipos específicos de declarações é uma tarefa comum ao usar a autorização baseada em declarações.</span><span class="sxs-lookup"><span data-stu-id="9271c-103">Examining the content of a <xref:System.IdentityModel.Claims.ClaimSet> for particular types of claims is a common task when using claim-based authorization.</span></span> <span data-ttu-id="9271c-104">Para examinar um <xref:System.IdentityModel.Claims.ClaimSet> para a presença de declarações específicas, use o <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> método.</span><span class="sxs-lookup"><span data-stu-id="9271c-104">To examine a <xref:System.IdentityModel.Claims.ClaimSet> for the presence of particular claims, use the <xref:System.IdentityModel.Claims.ClaimSet.FindClaims%2A> method.</span></span> <span data-ttu-id="9271c-105">Esse método fornece melhor desempenho do que iterar diretamente sobre o <xref:System.IdentityModel.Claims.ClaimSet> .</span><span class="sxs-lookup"><span data-stu-id="9271c-105">This method provides better performance than iterating directly over the <xref:System.IdentityModel.Claims.ClaimSet>.</span></span> <span data-ttu-id="9271c-106">O exemplo a seguir demonstra esse uso.</span><span class="sxs-lookup"><span data-stu-id="9271c-106">The following example demonstrates this usage.</span></span> <span data-ttu-id="9271c-107">Observe que os `claimType` `claimRight` parâmetros e podem ser `null` .</span><span class="sxs-lookup"><span data-stu-id="9271c-107">Note that the `claimType` and `claimRight` parameters can be `null`.</span></span> <span data-ttu-id="9271c-108">Nesse caso, os parâmetros corresponderão a todos os tipos de declaração e direitos de declaração.</span><span class="sxs-lookup"><span data-stu-id="9271c-108">In that case, the parameters will match all claim types and claim rights.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9271c-109">Exemplo</span><span class="sxs-lookup"><span data-stu-id="9271c-109">Example</span></span>  
 [!code-csharp[c_FindClaimsPerf#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_findclaimsperf/cs/c_findclaimsperf.cs#2)]
 [!code-vb[c_FindClaimsPerf#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_findclaimsperf/vb/c_findclaimsperf.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="9271c-110">Confira também</span><span class="sxs-lookup"><span data-stu-id="9271c-110">See also</span></span>

- [<span data-ttu-id="9271c-111">Gerenciamento de declarações e autorizações com o modelo de identidade</span><span class="sxs-lookup"><span data-stu-id="9271c-111">Managing Claims and Authorization with the Identity Model</span></span>](managing-claims-and-authorization-with-the-identity-model.md)
