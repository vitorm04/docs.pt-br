---
title: Como criar um SecurityBindingElement para um modo de autenticação especificado
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 70c3e371be3af5f03ea85f1681155c2590d42373
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a>Como criar um SecurityBindingElement para um modo de autenticação especificado
Windows Communication Foundation (WCF) fornece vários modos pelos quais os clientes e serviços autenticam um ao outro. Você pode criar elementos de associação para esses modos de autenticação de segurança usando os métodos estáticos no <xref:System.ServiceModel.Channels.SecurityBindingElement> classe ou por meio de configuração, conforme mostrado no exemplo a seguir.  
  
 Para obter mais informações sobre os modos de 18 autenticação, consulte [modos de autenticação SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra os métodos para criação de associações para diversos modos de autenticação.  
  
> [!NOTE]
>  Uma vez em uma instância do <xref:System.ServiceModel.Channels.SecurityBindingElement> objeto é criado, um número de propriedades é imutável, como <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> e <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>. Chamando `set` essas propriedades não alterá-los.  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Modos de autenticação de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 [Como criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
