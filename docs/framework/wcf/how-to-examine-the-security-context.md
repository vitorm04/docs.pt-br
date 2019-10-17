---
title: Como examinar o contexto de segurança
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- ServiceSecurityContext class
- WCF, security
- Claimset class
ms.assetid: 389b5a57-4175-4bc0-ada0-fc750d51149f
ms.openlocfilehash: 328d47a583a4f047fd54589a82d339de2cb1a16f
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/15/2019
ms.locfileid: "72320984"
---
# <a name="how-to-examine-the-security-context"></a>Como examinar o contexto de segurança
Ao programar serviços Windows Communication Foundation (WCF), o contexto de segurança do serviço permite que você determine detalhes sobre as credenciais do cliente e as declarações usadas para autenticar com o serviço. Isso é feito usando as propriedades da classe <xref:System.ServiceModel.ServiceSecurityContext>.  
  
 Por exemplo, você pode recuperar a identidade do cliente atual usando o <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> ou a propriedade <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>. Para determinar se o cliente é anônimo, use a propriedade <xref:System.ServiceModel.ServiceSecurityContext.IsAnonymous%2A>.  
  
 Você também pode determinar quais declarações estão sendo feitas em nome do cliente Iterando pela coleção de declarações na propriedade <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A>.  
  
### <a name="to-get-the-current-security-context"></a>Para obter o contexto de segurança atual  
  
- Acesse a propriedade estática <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> para obter o contexto de segurança atual. Examine qualquer uma das propriedades do contexto atual da referência.  
  
### <a name="to-determine-the-identity-of-the-caller"></a>Para determinar a identidade do chamador  
  
1. Imprima o valor das propriedades <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> e <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>.  
  
### <a name="to-parse-the-claims-of-a-caller"></a>Para analisar as declarações de um chamador  
  
1. Retornar a classe <xref:System.IdentityModel.Policy.AuthorizationContext> atual. Use a propriedade <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> para retornar o contexto de segurança do serviço atual e, em seguida, retorne o `AuthorizationContext` usando a propriedade <xref:System.ServiceModel.ServiceSecurityContext.AuthorizationContext%2A>.  
  
2. Analise a coleção de objetos <xref:System.IdentityModel.Claims.ClaimSet> retornados pela propriedade <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> da classe <xref:System.IdentityModel.Policy.AuthorizationContext>.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir imprime os valores das propriedades <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> e <xref:System.ServiceModel.ServiceSecurityContext.PrimaryIdentity%2A> do contexto de segurança atual e a propriedade <xref:System.IdentityModel.Claims.Claim.ClaimType%2A>, o valor do recurso da declaração e a propriedade <xref:System.IdentityModel.Claims.Claim.Right%2A> de cada declaração no contexto de segurança atual.  
  
 [!code-csharp[c_PrincipalPermissionAttribute#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_principalpermissionattribute/cs/source.cs#4)]
 [!code-vb[c_PrincipalPermissionAttribute#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_principalpermissionattribute/vb/source.vb#4)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 O código usa os seguintes namespaces:  
  
- <xref:System>  
  
- <xref:System.ServiceModel>  
  
- <xref:System.IdentityModel.Policy>  
  
- <xref:System.IdentityModel.Claims>  
  
## <a name="see-also"></a>Consulte também

- [Protegendo serviços](securing-services.md)
- [Autenticação e identidade de serviço](./feature-details/service-identity-and-authentication.md)
