---
title: '<claimTypeRequirements> Elemento '
ms.date: 03/30/2017
ms.assetid: a26efe73-4bad-4731-8cad-27f00d54354b
ms.openlocfilehash: 236ae880fff24f7ccbf5d6c9c03c0208d446688f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085831"
---
# <a name="claimtyperequirements-element"></a>\<claimTypeRequirements > elemento
Especifica uma coleção de tipos de declaração exigidos.  
  
 Em um cenário federado, os serviços de estado os requisitos de credenciais de entrada. Por exemplo, as credenciais de entrada devem ter um determinado conjunto de tipos de declaração. Cada elemento filho nesta coleção Especifica os tipos de declarações obrigatórias e opcionais esperados para aparecer em uma credencial federada.  
  
 Um requisito de tipo de declaração consiste o URI do tipo de declaração solicitado no token emitido junto com um parâmetro booliano que indica se essa declaração de tipo é necessária no token emitido, ou é opcional.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.IssuedTokenParametersElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
- <xref:System.ServiceModel.Configuration.SecurityElementBase.IssuedTokenParameters%2A>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [Identidade e autenticação de serviço](../../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md)
- [Federação e tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [Recursos de segurança com associações personalizadas](../../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [Federação e tokens emitidos](../../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)
- [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md)
- [Associações](../../../../../docs/framework/wcf/bindings.md)
- [Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
- [Como: criar uma associação personalizada utilizando o SecurityBindingElement](../../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
- [Segurança de associação personalizada](../../../../../docs/framework/wcf/samples/custom-binding-security.md)
