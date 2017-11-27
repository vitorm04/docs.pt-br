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
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2b94c8b77cd659438ec26129137dd9b8cab056b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="claims-and-denying-access-to-resources"></a>Declarações e acesso negado para recursos
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]oferece suporte a um mecanismo de autorização baseada em declarações. Além de permitir acesso a recursos com base na presença de declarações, sistemas geralmente negar acesso a recursos com base na presença de declarações. Tais sistemas devem examinar o <xref:System.IdentityModel.Policy.AuthorizationContext> para declarações que resultam em acesso negado antes de procurar declarações que resultam na permissão de acesso.  
  
 Por exemplo, um sistema pode negar acesso a um recurso para qualquer pessoa que tenha uma declaração com um tipo de `Age`, à direita do <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>e um valor de recurso de `Under 21` somente quando essa identidade também tem uma declaração de tipo `Name`, à direita do <xref:System.IdentityModel.Claims.Rights.Identity%2A>, e um valor de recurso de `Mallory`. Ou seja, o sistema nega o acesso a qualquer pessoa que é menos de 21 anos de idade e concede acesso quando o nome é Mallory. Para implementar isso corretamente semântica, é importante procurar o `Age` declaração primeiro e determinar se a idade é menos de 21 anos de idade. Caso contrário, se Mallory em 21, em seguida, o recurso pode ser concedido acesso somente de acordo com o `Name` de declaração.  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Declarações e Tokens](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
