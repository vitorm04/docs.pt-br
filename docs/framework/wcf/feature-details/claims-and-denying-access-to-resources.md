---
title: Declarações e acesso negado para recursos
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
ms.openlocfilehash: 4f48c59090579f4b451f615bb792a4dcb73f6df5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59079507"
---
# <a name="claims-and-denying-access-to-resources"></a>Declarações e acesso negado para recursos
Windows Communication Foundation (WCF) oferece suporte a um mecanismo de autorização baseada em declarações. Além de permitir o acesso a recursos com base na presença de declarações, sistemas geralmente negar acesso a recursos com base na presença de declarações. Tais sistemas devem examinar o <xref:System.IdentityModel.Policy.AuthorizationContext> para declarações que resultam em acesso negado antes de procurar declarações que resultam em acesso sendo permitido.  
  
 Por exemplo, um sistema pode negar o acesso a um recurso para qualquer pessoa que tem uma declaração com um tipo de `Age`, à direita da <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>e um valor de recurso de `Under 21` apenas quando essa identidade também tem uma declaração do tipo `Name`, à direita do <xref:System.IdentityModel.Claims.Rights.Identity%2A>, e um valor de recurso de `Mallory`. Em outras palavras, o sistema nega o acesso a qualquer pessoa que é menos de 21 anos de idade e concede acesso quando o nome é Mallory. Para implementar isso corretamente semântica, é importante procurar o `Age` primeiro de declaração e determinar se a idade é menos de 21 anos de idade. Caso contrário, se Mallory em 21, em seguida, o recurso pode ter acesso somente de acordo com o `Name` de declaração.  
  
## <a name="see-also"></a>Consulte também

- [Gerenciamento de declarações e autorizações com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Declarações e tokens](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
