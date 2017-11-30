---
title: Como configurar um emissor local
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
ms.assetid: 15263371-514e-4ea6-90fb-14b4939154cd
caps.latest.revision: "11"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 413f534bacd1f5551cd3b5d7c83e3722104fa0c1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-configure-a-local-issuer"></a>Como configurar um emissor local
Este tópico descreve como configurar um cliente para usar um emissor local para tokens emitidos.  
  
 Geralmente, quando um cliente se comunica com um serviço federado, o serviço Especifica o endereço do serviço de token é esperado para emitir o token que o cliente usará para se autenticar para o serviço federado de segurança de. Em determinadas situações, o cliente pode ser configurado para usar um *emissor local*.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]usa um emissor local em casos em que o endereço do emissor de uma associação federada é http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous ou `null`. Nesses casos, você deve configurar o <xref:System.ServiceModel.Description.ClientCredentials> com o endereço do emissor local e a associação a ser usado para se comunicar com esse emissor.  
  
> [!NOTE]
>  Se o <xref:System.ServiceModel.Description.ClientCredentials.SupportInteractive%2A> propriedade o `ClientCredentials` classe é definida como `true`, um endereço do emissor local não for especificado e o endereço do emissor especificado pelo [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) ou outros associação federada é http://schemas.xmlsoap.org/ws/2005/05/identity/issuer/self, http://schemas.microsoft.com/2005/12/ServiceModel/Addressing/Anonymous, ou `null`, em seguida, o Windows [!INCLUDE[infocard](../../../../includes/infocard-md.md)] emissor é usado.  
  
### <a name="to-configure-the-local-issuer-in-code"></a>Para configurar o emissor local no código  
  
1.  Criar uma variável de tipo<xref:System.ServiceModel.Security.IssuedTokenClientCredential>  
  
2.  Defina a variável para a instância retornada do <xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A> propriedade o `ClientCredentials` classe. Essa instância é retornada pelo <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> propriedade do cliente (herdado de <xref:System.ServiceModel.ClientBase%601>) ou o <xref:System.ServiceModel.ChannelFactory.Credentials%2A> propriedade o <xref:System.ServiceModel.ChannelFactory>:  
  
     [!code-csharp[c_CreateSTS#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#9)]
     [!code-vb[c_CreateSTS#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#9)]  
  
3.  Definir o <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerAddress%2A> propriedade para uma nova instância do <xref:System.ServiceModel.EndpointAddress>, com o endereço do emissor local como um argumento para o construtor.  
  
     [!code-csharp[c_CreateSTS#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#10)]
     [!code-vb[c_CreateSTS#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#10)]  
  
     Como alternativa, crie um novo <xref:System.Uri> instância como um argumento para o construtor.  
  
     [!code-csharp[c_CreateSTS#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#11)]
     [!code-vb[c_CreateSTS#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#11)]  
  
     O `addressHeaders` parâmetro é uma matriz de <xref:System.ServiceModel.Channels.AddressHeader> instâncias, conforme mostrado.  
  
     [!code-csharp[c_CreateSTS#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#12)]
     [!code-vb[c_CreateSTS#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#12)]  
  
4.  Define a associação para o emissor local usando o <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerBinding%2A> propriedade.  
  
     [!code-csharp[c_CreateSTS#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#13)]
     [!code-vb[c_CreateSTS#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#13)]  
  
5.  Opcional. Adicionar comportamentos de ponto de extremidade configurado para o emissor local, adicionando desses comportamentos a coleção retornada pelo <xref:System.ServiceModel.Security.IssuedTokenClientCredential.LocalIssuerChannelBehaviors%2A> propriedade.  
  
     [!code-csharp[c_CreateSTS#14](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_creatests/cs/source.cs#14)]
     [!code-vb[c_CreateSTS#14](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_creatests/vb/source.vb#14)]  
  
### <a name="to-configure-the-local-issuer-in-configuration"></a>Para configurar o emissor local na configuração  
  
1.  Criar um [ \<localIssuer >](../../../../docs/framework/configure-apps/file-schema/wcf/localissuer.md) elemento como um filho de [ \<issuedToken >](../../../../docs/framework/configure-apps/file-schema/wcf/issuedtoken.md) que é um filho do elemento a [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elemento em um comportamento de ponto de extremidade.  
  
2.  Definir o `address` de atributo para o endereço do emissor local que aceita solicitações de token.  
  
3.  Definir o `binding` e `bindingConfiguration` atributos com valores que fazem referência a ligação apropriada para usar ao se comunicar com o ponto de extremidade do emissor local.  
  
4.  Opcional. Definido o [ \<identidade >](../../../../docs/framework/configure-apps/file-schema/wcf/identity.md) elemento como um filho de <`localIssuer`> elemento e especifique as informações de identidade para o emissor local.  
  
5.  Opcional. Definido o [ \<cabeçalhos >](../../../../docs/framework/configure-apps/file-schema/wcf/headers.md) elemento como um filho de <`localIssuer`> elemento e especificar cabeçalhos adicionais que são necessárias para tratar corretamente o emissor local.  
  
## <a name="net-framework-security"></a>Segurança do .NET Framework  
 Observe que, se um endereço do emissor e a associação especificadas para uma associação de determinado, o emissor local não é usado para pontos de extremidade que utilizam essa associação. Clientes que pretende usar sempre o emissor local devem garantir que eles não usam essa associação ou que eles modificar a associação para que o endereço do emissor é `null`.  
  
## <a name="see-also"></a>Consulte também  
 [Como: configurar as credenciais em um serviço de Federação](../../../../docs/framework/wcf/feature-details/how-to-configure-credentials-on-a-federation-service.md)  
 [Como: criar um cliente federado](../../../../docs/framework/wcf/feature-details/how-to-create-a-federated-client.md)  
 [Como: criar uma WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-create-a-wsfederationhttpbinding.md)
