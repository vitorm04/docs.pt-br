---
title: Declarações e tokens de SAML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
- issued tokens
- SAML token
ms.assetid: 930b6e34-9eab-4e95-826c-4e06659bb977
ms.openlocfilehash: f1f7a15d1457390bf77f5e53c7fd657304725df6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59218206"
---
# <a name="saml-tokens-and-claims"></a>Declarações e tokens de SAML
Declarações de marcação linguagem SAML (Security) *tokens* são representações XML de declarações. Por padrão, são tokens SAML que usa o Windows Communication Foundation (WCF) em cenários de segurança federada *tokens emitidos*.  
  
 Tokens SAML executam instruções que são conjuntos de declarações feitas por uma entidade sobre outra entidade. Por exemplo, em cenários de segurança federada, as instruções são feitas por um serviço de token de segurança sobre um usuário no sistema. O serviço de token de segurança assina o token SAML para indicar a veracidade das instruções contidas no token. Além disso, o token SAML é associado com material de chave de criptografia que o usuário do token SAML prova conhecimento de. Essa prova de acordo com a terceira parte confiável que o token SAML foi, na verdade, emitidos para que o usuário. Por exemplo, em um cenário típico:  
  
1.  Um cliente solicita um token SAML de um serviço de token de segurança, autenticação para esse serviço de token de segurança por meio de credenciais do Windows.  
  
2.  O serviço de token de segurança emite um token SAML para o cliente. O token SAML é assinado com um certificado associado com o serviço de token de segurança e contém uma chave de prova criptografada para o serviço de destino.  
  
3.  O cliente também recebe uma cópia do *chave de prova*. O cliente, em seguida, apresenta o token SAML para o serviço de aplicativo (o *terceira*) e assina a mensagem com essa chave de prova.  
  
4.  A assinatura ao longo do token SAML informa a terceira parte confiável que o serviço de token de segurança o token emitido. A assinatura da mensagem criada com a chave de prova informa a terceira parte confiável que o token foi emitido para o cliente.  
  
## <a name="from-claims-to-samlattributes"></a>De declarações para SamlAttributes  
 No WCF, as declarações em tokens SAML são modeladas como <xref:System.IdentityModel.Tokens.SamlAttribute> objetos, que podem ser preenchidos diretamente de <xref:System.IdentityModel.Claims.Claim> objetos, fornecidos a <xref:System.IdentityModel.Claims.Claim> objeto tem uma <xref:System.IdentityModel.Claims.Claim.Right%2A> propriedade de <xref:System.IdentityModel.Claims.Rights.PossessProperty%2A> e o <xref:System.IdentityModel.Claims.Claim.Resource%2A> é de propriedade do tipo <xref:System.String>. Por exemplo:  
  
 [!code-csharp[c_CreateSTS#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#8)]
 [!code-vb[c_CreateSTS#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#8)]  
  
> [!NOTE]
>  Quando os tokens SAML são serializados em mensagens, quando eles são emitidos por um serviço de token de segurança ou quando eles forem apresentados pelos clientes para serviços como parte da autenticação, a cota de tamanho máximo da mensagem deve ser grande o suficiente para acomodar o token SAML e as outras partes da mensagem. Em casos normais, as cotas padrão de tamanho da mensagem são suficientes. No entanto, nos casos em que um token SAML é grande porque ela contém centenas de declarações, talvez você precise aumentar as cotas para acomodar o token serializado. Para obter mais informações, consulte [considerações sobre segurança para dados](../../../../docs/framework/wcf/feature-details/security-considerations-for-data.md).  
  
## <a name="from-samlattributes-to-claims"></a>De SamlAttributes em declarações  
 Quando os tokens SAML são recebidos em mensagens, as várias declarações no token SAML são transformadas em <xref:System.IdentityModel.Policy.IAuthorizationPolicy> objetos que são colocados no <xref:System.IdentityModel.Policy.AuthorizationContext>. As declarações de cada instrução SAML são retornadas pelo <xref:System.IdentityModel.Policy.AuthorizationContext.ClaimSets%2A> propriedade do <xref:System.IdentityModel.Policy.AuthorizationContext> e pode ser examinado para determinar se deve autenticar e autorizar o usuário.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.IdentityModel.Policy.AuthorizationContext>
- <xref:System.IdentityModel.Policy.IAuthorizationPolicy>
- <xref:System.IdentityModel.Claims.ClaimSet>
- [Federação](../../../../docs/framework/wcf/feature-details/federation.md)
- [Como: criar um cliente federado](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)
- [Como: configurar credenciais em um serviço de federação](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)
- [Gerenciamento de declarações e autorizações com o modelo de identidade](../../../../docs/framework/wcf/feature-details/managing-claims-and-authorization-with-the-identity-model.md)
- [Declarações e tokens](../../../../docs/framework/wcf/feature-details/claims-and-tokens.md)
- [Valores de recursos e criação de declarações](../../../../docs/framework/wcf/feature-details/claim-creation-and-resource-values.md)
- [Como: criar uma declaração personalizada](../../../../docs/framework/wcf/extending/how-to-create-a-custom-claim.md)
