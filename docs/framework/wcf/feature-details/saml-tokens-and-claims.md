---
title: "Declarações e tokens de SAML"
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
helpviewer_keywords:
- WCF, federation
- federation
- issued tokens
- SAML token
ms.assetid: 930b6e34-9eab-4e95-826c-4e06659bb977
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a2b35ba4da503663a2bb92597ed193c408e7c99b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="saml-tokens-and-claims"></a>Declarações e tokens de SAML
Security asserções Markup Language (SAML) *tokens* são representações de XML de declarações. Por padrão, os tokens SAML [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usa em cenários de segurança federada é *tokens emitidos*.  
  
 Tokens SAML executar instruções que são conjuntos de declarações feitas por uma entidade sobre outra entidade. Por exemplo, em cenários de segurança federada, as instruções são feitas por um serviço de token de segurança sobre um usuário no sistema. O serviço de token de segurança assina o token SAML para indicar a veracidade das instruções contidas no token. Além disso, o token SAML é associado ao material de chave de criptografia que o usuário do token SAML prova conhecimento de. Essa prova de acordo com a terceira parte confiável que o token SAML, na verdade, é emitido para o usuário. Por exemplo, em um cenário típico:  
  
1.  Um cliente solicita um token SAML de um serviço de token de segurança de autenticação para esse serviço de token de segurança usando as credenciais do Windows.  
  
2.  O serviço de token de segurança emite um token SAML para o cliente. O token SAML é assinado com um certificado associado com o serviço de token de segurança e contém uma chave de prova criptografada para o serviço de destino.  
  
3.  O cliente também recebe uma cópia do *chave de prova*. O cliente, em seguida, apresenta o token SAML para o serviço de aplicativo (o *terceira parte confiável*) e assina a mensagem com a chave de prova.  
  
4.  A assinatura sobre o token SAML informa a terceira parte confiável que o serviço de token de segurança emitido o token. A assinatura da mensagem criada com a chave de prova informa a terceira parte confiável que o token foi emitido para o cliente.  
  
## <a name="from-claims-to-samlattributes"></a>De declarações para SamlAttributes  
 Em [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], declarações nos tokens SAML são modeladas como <xref:System.IdentityModel.Tokens.SamlAttribute> objetos, que podem ser preenchidos diretamente do <xref:System.IdentityModel.Claims.Claim> objetos, fornecidos o <xref:System.IdentityModel.Claims.Claim> objeto tem um <xref:System.IdentityModel.Claims.Claim.Right%2A> propriedade de <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> e o <xref:System.IdentityModel.Claims.Claim.Resource%2A> a propriedade é do tipo <xref:System.String>. Por exemplo:  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
>  Quando os tokens SAML são serializados em mensagens, quando eles são emitidos por um serviço de token de segurança ou quando são apresentadas pelos clientes para serviços como parte da autenticação, a cota de tamanho máximo da mensagem deve ser grande o suficiente para acomodar o token SAML e as outras partes da mensagem. Em casos normais, as cotas de tamanho de mensagem padrão são suficientes. No entanto, em casos em que um token SAML é grande porque ele contém centenas de declarações, você precisará aumentar as cotas para acomodar o token serializado. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Considerações de segurança para dados](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
## <a name="from-samlattributes-to-claims"></a>De SamlAttributes declarações  
 Quando os tokens SAML são recebidos em mensagens, as várias instruções no token de SAML são transformadas em <xref:System.IdentityModel.Policy.IAuthorizationPolicy> objetos que são colocados no <xref:System.IdentityModel.Policy.AuthorizationContext>. As declarações de cada instrução de SAML são retornadas pelo <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> propriedade o <xref:System.IdentityModel.Policy.AuthorizationContext> e pode ser examinado para determinar se é autenticar e autorizar o usuário.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IdentityModel.Policy.AuthorizationContext>  
 <xref:System.IdentityModel.Policy.IAuthorizationPolicy>  
 <xref:System.IdentityModel.Claims.ClaimSet>  
 [Federação](../../../../docs/framework/wcf/feature-details/federation.md)  
 [Como criar um cliente federado](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Como configurar as credenciais em um Serviço de Federação](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Gerenciando reivindicações e autorização com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)  
 [Declarações e tokens](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)  
 [Valores de recursos e criação de declarações](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)  
 [Como criar uma declaração personalizada](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
