---
title: "Declarações e acesso negado para recursos"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 156856ddd1a4c3b1d8f77a8a61f7e0336f993839
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="claims-and-denying-access-to-resources"></a><span data-ttu-id="ebf6b-102">Declarações e acesso negado para recursos</span><span class="sxs-lookup"><span data-stu-id="ebf6b-102">Claims and Denying Access to Resources</span></span>
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]<span data-ttu-id="ebf6b-103">oferece suporte a um mecanismo de autorização baseada em declarações.</span><span class="sxs-lookup"><span data-stu-id="ebf6b-103"> supports a claims-based authorization mechanism.</span></span> <span data-ttu-id="ebf6b-104">Além de permitir acesso a recursos com base na presença de declarações, sistemas geralmente negar acesso a recursos com base na presença de declarações.</span><span class="sxs-lookup"><span data-stu-id="ebf6b-104">As well as allowing access to resources based on the presence of claims, systems often deny access to resources based on the presence of claims.</span></span> <span data-ttu-id="ebf6b-105">Tais sistemas devem examinar o <xref:System.IdentityModel.Policy.AuthorizationContext> para declarações que resultam em acesso negado antes de procurar declarações que resultam na permissão de acesso.</span><span class="sxs-lookup"><span data-stu-id="ebf6b-105">Such systems should examine the <xref:System.IdentityModel.Policy.AuthorizationContext> for claims that result in access being denied before looking for claims that result in access being allowed.</span></span>  
  
 <span data-ttu-id="ebf6b-106">Por exemplo, um sistema pode negar acesso a um recurso para qualquer pessoa que tenha uma declaração com um tipo de `Age`, à direita do <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>e um valor de recurso de `Under 21` somente quando essa identidade também tem uma declaração de tipo `Name`, à direita do <xref:System.IdentityModel.Claims.Rights.Identity%2A>, e um valor de recurso de `Mallory`.</span><span class="sxs-lookup"><span data-stu-id="ebf6b-106">For example, a system might deny access to a resource to anyone who has a claim with a type of `Age`, a right of <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>, and a resource value of `Under 21` only when that identity also has a claim of type `Name`, a right of <xref:System.IdentityModel.Claims.Rights.Identity%2A>, and a resource value of `Mallory`.</span></span> <span data-ttu-id="ebf6b-107">Ou seja, o sistema nega o acesso a qualquer pessoa que é menos de 21 anos de idade e concede acesso quando o nome é Mallory.</span><span class="sxs-lookup"><span data-stu-id="ebf6b-107">Put another way, the system denies access to anyone who is under 21 years old and grants access when the name is Mallory.</span></span> <span data-ttu-id="ebf6b-108">Para implementar isso corretamente semântica, é importante procurar o `Age` declaração primeiro e determinar se a idade é menos de 21 anos de idade.</span><span class="sxs-lookup"><span data-stu-id="ebf6b-108">To correctly implement this semantic, it is important to look for the `Age` claim first and determine whether the age is under 21 years old.</span></span> <span data-ttu-id="ebf6b-109">Caso contrário, se Mallory em 21, em seguida, o recurso pode ser concedido acesso somente de acordo com o `Name` de declaração.</span><span class="sxs-lookup"><span data-stu-id="ebf6b-109">Otherwise, if Mallory is under 21, then the resource may be granted access solely on the basis of the `Name` claim.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ebf6b-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ebf6b-110">See Also</span></span>  
 [<span data-ttu-id="ebf6b-111">Gerenciando reivindicações e autorização com o modelo de identidade</span><span class="sxs-lookup"><span data-stu-id="ebf6b-111">Managing Claims and Authorization with the Identity Model</span></span>](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [<span data-ttu-id="ebf6b-112">Declarações e tokens</span><span class="sxs-lookup"><span data-stu-id="ebf6b-112">Claims and Tokens</span></span>](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
