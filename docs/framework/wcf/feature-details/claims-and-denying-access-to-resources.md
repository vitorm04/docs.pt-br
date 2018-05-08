---
title: Declarações e acesso negado para recursos
ms.date: 03/30/2017
helpviewer_keywords:
- claims [WCF], denying access to resources
ms.assetid: 145ebb41-680e-4256-b14c-1efb4af1e982
ms.openlocfilehash: a53affe5e21b5ef532e7094eed032b44f5a5ea7c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="claims-and-denying-access-to-resources"></a>Declarações e acesso negado para recursos
Windows Communication Foundation (WCF) oferece suporte a um mecanismo de autorização baseada em declarações. Além de permitir acesso a recursos com base na presença de declarações, sistemas geralmente negar acesso a recursos com base na presença de declarações. Tais sistemas devem examinar o <xref:System.IdentityModel.Policy.AuthorizationContext> para declarações que resultam em acesso negado antes de procurar declarações que resultam na permissão de acesso.  
  
 Por exemplo, um sistema pode negar acesso a um recurso para qualquer pessoa que tenha uma declaração com um tipo de `Age`, à direita do <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A>e um valor de recurso de `Under 21` somente quando essa identidade também tem uma declaração de tipo `Name`, à direita do <xref:System.IdentityModel.Claims.Rights.Identity%2A>, e um valor de recurso de `Mallory`. Ou seja, o sistema nega o acesso a qualquer pessoa que é menos de 21 anos de idade e concede acesso quando o nome é Mallory. Para implementar isso corretamente semântica, é importante procurar o `Age` declaração primeiro e determinar se a idade é menos de 21 anos de idade. Caso contrário, se Mallory em 21, em seguida, o recurso pode ser concedido acesso somente de acordo com o `Name` de declaração.  
  
## <a name="see-also"></a>Consulte também  
 [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Declarações e tokens](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
