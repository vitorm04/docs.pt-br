---
title: "Como criar um SecurityBindingElement para um modo de autenticação especificado"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: a7c7747a-5b8c-463f-8493-7266dac75066
caps.latest.revision: "9"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 29cbe3c10ac68d508dc22781e46a6041f2d7eab7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-securitybindingelement-for-a-specified-authentication-mode"></a>Como criar um SecurityBindingElement para um modo de autenticação especificado
[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]fornece vários modos pelos quais os clientes e serviços autenticam um ao outro. Você pode criar elementos de associação para esses modos de autenticação de segurança usando os métodos estáticos no <xref:System.ServiceModel.Channels.SecurityBindingElement> classe ou por meio de configuração, conforme mostrado no exemplo a seguir.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]os modos de 18 autenticação, consulte [modos de autenticação SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra os métodos para criação de associações para diversos modos de autenticação.  
  
> [!NOTE]
>  Uma vez em uma instância do <xref:System.ServiceModel.Channels.SecurityBindingElement> objeto é criado, um número de propriedades é imutável, como <xref:System.ServiceModel.Security.Tokens.IssuedSecurityTokenParameters.KeyType%2A> e <xref:System.ServiceModel.Channels.SecurityBindingElement.MessageSecurityVersion%2A>. Chamando `set` essas propriedades não alterá-los.  
  
 [!code-csharp[c_CustomBindingsAuthMode#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#2)]
 [!code-vb[c_CustomBindingsAuthMode#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Modos de autenticação de SecurityBindingElement](../../../../docs/framework/wcf/feature-details/securitybindingelement-authentication-modes.md)  
 [Como criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md)
