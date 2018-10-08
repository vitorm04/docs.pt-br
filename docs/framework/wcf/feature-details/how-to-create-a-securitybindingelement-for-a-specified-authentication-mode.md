---
title: Como criar um SecurityBindingElement para um modo de autenticação especificado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
author: BrucePerlerMS
ms.openlocfilehash: 6204a2832bbdc0c6631903687fcd8a1c45b35d03
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850629"
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a>Como criar um SecurityBindingElement para um modo de autenticação especificado
Windows Communication Foundation (WCF) fornece vários modos pelos quais os clientes e serviços autenticam um ao outro. Você pode criar elementos de associação para esses modos de autenticação de segurança por meio de métodos estáticos no <xref:System.ServiceModel.Channels.SecurityBindingElement> classe ou por meio da configuração, conforme mostrado no exemplo a seguir.  
  
 Para obter mais informações sobre os modos de 18 autenticação, consulte [modos de autenticação de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra os métodos para criação de associações para diversos modos de autenticação.  
  
> [!NOTE]
>  Uma vez em uma instância das <xref:System.ServiceModel.Channels.SecurityBindingElement> objeto é criado, um número de propriedades é imutável, como <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> e <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>. Chamar `set` sobre essas propriedades não alterá-los.  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Modos de autenticação de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 [Como criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
