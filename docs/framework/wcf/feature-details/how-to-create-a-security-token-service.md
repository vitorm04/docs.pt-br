---
title: "Como criar um serviço de token de segurança"
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
ms.assetid: 98e82101-4cff-4bb8-a220-f7abed3556e5
caps.latest.revision: "12"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: bfb1acc5c1c665ebd410b0a49e8f357e5b9458f3
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-security-token-service"></a>Como criar um serviço de token de segurança
Um serviço de token de segurança implementa o protocolo definido na especificação WS-Trust. Esse protocolo define os formatos de mensagem e padrões de troca de mensagem para a emissão, renovação, cancelando e validar tokens de segurança. Um serviço de token de segurança fornece um ou mais desses recursos. Este tópico é o cenário mais comum: implementação de emissão de token.  
  
## <a name="issuing-tokens"></a>Emissão de Tokens  
 WS-Trust define os formatos de mensagem, com base no `RequestSecurityToken` elemento do esquema de linguagem XSD de definição de esquema XML, e `RequestSecurityTokenResponse` elemento do esquema XSD para a execução de emissão de token. Além disso, ele define os associados ação Uniform Resource Identifiers (URIs). A ação associado a URI de `RequestSecurityToken` mensagem é http://schemas.xmlsoap.org/ws/2005/02/trust/RST/Issue. A ação associado a URI de `RequestSecurityTokenResponse` mensagem é http://schemas.xmlsoap.org/ws/2005/02/trust/RSTR/Issue.  
  
### <a name="request-message-structure"></a>Estrutura de mensagens de solicitação  
 A estrutura de mensagens de solicitação de problema normalmente consiste dos seguintes itens:  
  
-   Um tipo de solicitação URI com um valor de http://schemas.xmlsoap.org/ws/2005/02/trust/Issue.  
  
-   Um tipo de token URI. Para tokens de segurança asserções Markup Language (SAML) 1.1, o valor desse URI é http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1.  
  
-   Um valor de tamanho de chave que indica o número de bits na chave a ser associado com o token emitido.  
  
-   Um tipo de chave URI. Para chaves simétricas, o valor desse URI é http://schemas.xmlsoap.org/ws/2005/02/trust/SymmetricKey.  
  
 Além disso, alguns dos outros itens podem estar presentes:  
  
-   Material de chave fornecido pelo cliente.  
  
-   Informações de escopo que indica o serviço de destino que será usado com o token emitido.  
  
 O serviço de token de segurança usa as informações na mensagem de solicitação de problema quando ele cria a mensagem de resposta do problema.  
  
## <a name="response-message-structure"></a>Estrutura de mensagens de resposta  
 A estrutura de mensagens de resposta de problema normalmente é constituído dos itens a seguir;  
  
-   O token de segurança emitido, por exemplo, uma asserção SAML 1.1.  
  
-   Um token de prova associado ao token de segurança. Para chaves simétricas, isso geralmente é um formato criptografado do material de chave.  
  
-   Referências para o token de segurança emitido. Normalmente, o serviço de token de segurança retorna uma referência que pode ser usada quando o token emitido é exibido em uma mensagem subsequente enviada pelo cliente e outro que pode ser usada quando o token não está presente nas mensagens subsequentes.  
  
 Além disso, alguns dos outros itens podem estar presentes:  
  
-   Material de chave fornecido pelo serviço de token de segurança.  
  
-   O algoritmo necessário para calcular a chave compartilhada.  
  
-   Informações de tempo de vida do token emitido.  
  
## <a name="processing-request-messages"></a>Mensagens de solicitação de processamento  
 O serviço de token de segurança processa a solicitação de problema examinando as várias partes da mensagem de solicitação e garantir que ele pode emitir um token que atende à solicitação. O serviço de token de segurança deve determinar o seguinte antes de ele constrói o token a ser emitido:  
  
-   A solicitação é realmente uma solicitação para um token a ser emitido.  
  
-   O serviço de token de segurança dá suporte ao tipo de token solicitado.  
  
-   O solicitante está autorizado a fazer a solicitação.  
  
-   O serviço de token de segurança pode atender às expectativas do solicitante em relação ao material de chave.  
  
 Duas partes essenciais de construção de um token de determinar qual chave para assinar o token com e quais para criptografar a chave compartilhada com. O token precisa ser assinado para que quando o cliente apresenta o token para o serviço de destino, que o serviço pode determinar que o token foi emitido por um serviço de token de segurança que ele confia. O material da chave deve ser criptografada de forma que o serviço de destino pode descriptografar o material de chave.  
  
 Assinatura de uma asserção SAML envolve a criação de um <xref:System.IdentityModel.Tokens.SigningCredentials> instância. O construtor para essa classe usa o seguinte:  
  
-   Um <xref:System.IdentityModel.Tokens.SecurityKey> para a chave a ser usado para assinar a asserção SAML.  
  
-   Uma cadeia de caracteres que identifica o algoritmo de assinatura para uso.  
  
-   Uma cadeia de caracteres que identifica o algoritmo de digest para uso.  
  
-   Opcionalmente, um <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> que identifica a chave a ser usado para assinar a asserção.  
  
 [!code-csharp[c_CreateSTS#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#1)]
 [!code-vb[c_CreateSTS#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#1)]  
  
 Criptografar a chave compartilhada envolve colocar o material da chave e criptografá-los com uma chave que o serviço de destino pode usar para descriptografar a chave compartilhada. Normalmente, a chave pública do serviço de destino é usada.  
  
 [!code-csharp[c_CreateSTS#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#2)]
 [!code-vb[c_CreateSTS#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#2)]  
  
 Além disso, um <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> para a chave criptografada é necessária.  
  
 [!code-csharp[c_CreateSTS#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#3)]
 [!code-vb[c_CreateSTS#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#3)]  
  
 Isso <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier> é usado para criar um `SamlSubject` como parte do `SamlToken`.  
  
 [!code-csharp[c_CreateSTS#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#4)]
 [!code-vb[c_CreateSTS#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#4)]  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Federação exemplo](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="creating-response-messages"></a>Criar mensagens de resposta  
 Depois que o serviço de token de segurança processa a solicitação de problema e constrói o token a ser emitido junto com a chave de prova, a mensagem de resposta deve ser construído, inclusive pelo menos o token solicitado, o token de prova e as referências de token emitidas. O token emitido é normalmente uma <xref:System.IdentityModel.Tokens.SamlSecurityToken> criado a partir de <xref:System.IdentityModel.Tokens.SamlAssertion>, conforme mostrado no exemplo a seguir.  
  
 [!code-csharp[c_CreateSTS#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#5)]
 [!code-vb[c_CreateSTS#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#5)]  
  
 No caso em que o serviço de token de segurança fornece o material de chave compartilhado, o token de prova é construído com a criação de um <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>.  
  
 [!code-csharp[c_CreateSTS#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#6)]
 [!code-vb[c_CreateSTS#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#6)]  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]como criar o token de prova quando o cliente e o token de segurança de serviço ambos fornecem material de chave para a chave compartilhada, consulte [federação exemplo](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
 As referências de tokens emitidas são construídas com a criação de instâncias da <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause> classe.  
  
 [!code-csharp[c_CreateSTS#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#7)]
 [!code-vb[c_CreateSTS#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#7)]  
  
 Esses vários valores, em seguida, são serializados em mensagem de resposta retornada ao cliente.  
  
## <a name="example"></a>Exemplo  
 Para obter o código completo para um serviço de token de segurança, consulte [federação exemplo](../../../../docs/framework/wcf/samples/federation-sample.md).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.IdentityModel.Tokens.SigningCredentials>  
 <xref:System.IdentityModel.Tokens.SecurityKey>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifier>  
 <xref:System.IdentityModel.Tokens.SamlSecurityToken>  
 <xref:System.IdentityModel.Tokens.SamlAssertion>  
 <xref:System.ServiceModel.Security.Tokens.BinarySecretSecurityToken>  
 <xref:System.IdentityModel.Tokens.SecurityKeyIdentifierClause>  
 [Exemplo de Federação](../../../../docs/framework/wcf/samples/federation-sample.md)
