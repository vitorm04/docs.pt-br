---
title: Como criar uma WSFederationHttpBinding
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: e54897d7-aa6c-46ec-a278-b2430c8c2e10
caps.latest.revision: 16
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 8962564bbefc3f43261a2979ae9765369b211f15
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2018
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>Como criar uma WSFederationHttpBinding
Em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)], o <xref:System.ServiceModel.WSFederationHttpBinding> classe ([\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) na configuração) fornece um mecanismo para expor um serviço federado. Ou seja, um serviço que exige que os clientes se autentiquem usando um token de segurança emitido por um serviço de token de segurança. Este tópico mostra como configurar um <xref:System.ServiceModel.WSFederationHttpBinding> em código e configuração. Depois que a associação é criada, você pode configurar um ponto de extremidade para usar essa associação.  
  
 As etapas básicas são descritas da seguinte maneira:  
  
1.  Selecione um modo de segurança. O <xref:System.ServiceModel.WSFederationHttpBinding> dá suporte a `Message`, que fornece segurança de ponta a ponta no nível da mensagem, mesmo em vários saltos, e `TransportWithMessageCredential`, que fornece melhor desempenho em casos onde o cliente e o serviço podem fazer uma conexão direta via HTTPS.  
  
    > [!NOTE]
    >  O <xref:System.ServiceModel.WSFederationHttpBinding> também oferece suporte a `None` como um modo de segurança. Esse modo não é seguro e é fornecido apenas para fins de depuração. Se um ponto de extremidade de serviço é implantado com um <xref:System.ServiceModel.WSFederationHttpBinding> com seu modo de segurança definido como `None`, associação de cliente resultante (gerado pelo [Ferramenta Utilitária de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)) é um <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`> com o modo de segurança `None`.  
  
     Ao contrário de outras associações fornecidas pelo sistema, não é necessário selecionar um tipo de credencial de cliente ao usar o `WSFederationHttpBinding`. Isso ocorre porque o tipo de credencial de cliente é sempre um token emitido. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] adquire um token de um emissor especificado e apresenta esse token para o serviço para autenticar o cliente.  
  
2.  Em clientes federados, defina o <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> propriedade para a URL do serviço de token de segurança. Definir o <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> para a associação a ser usada para se comunicar com o serviço de token de segurança.  
  
3.  Opcional. Definir o <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> propriedade para o URI Uniform Resource identificador () de um tipo de token. Em serviços federados, especifique o tipo de token que o serviço espera. Em clientes federados, especifique o tipo de token as solicitações do cliente do serviço de token de segurança.  
  
     Se nenhum tipo de token é especificado, os clientes geram Tokens de segurança de solicitação do WS-Trust (RSTs) sem um tipo de token URI e serviços espera que a autenticação de cliente usando um token de segurança asserções Markup Language (SAML) 1.1 por padrão.  
  
     O URI para um token SAML 1.1 é "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1".  
  
4.  Opcional. Em serviços federados, defina o <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> propriedade para a URL de metadados de um serviço de token de segurança. O ponto de extremidade de metadados permite que os clientes do serviço selecionar um par de associação/ponto de extremidade apropriado, se o serviço está configurado para publicar metadados. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] publicação de metadados, consulte [metadados de publicação](../../../../docs/framework/wcf/feature-details/publishing-metadata.md).  
  
 Você também pode definir outras propriedades, incluindo o tipo de chave usado como uma chave de prova no token emitido, o conjunto de algoritmos para usar entre o cliente e o serviço se negociar ou especifique explicitamente as credenciais do serviço, qualquer específica declarações do serviço espera que o token emitido contenha e quaisquer elementos XML adicionais que devem ser adicionados à solicitação, que o cliente envia ao serviço de token de segurança.  
  
> [!NOTE]
>  O `NegotiateServiceCredential` propriedade só é relevante quando o `SecurityMode` é definido como `Message`. Se `SecurityMode` é definido como `TransportWithMessageCredential`, em seguida, o `NegotiateServiceCredential` propriedade será ignorada.  
  
### <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>Para configurar uma WSFederationHttpBinding no código  
  
1.  Criar uma instância do <xref:System.ServiceModel.WSFederationHttpBinding>.  
  
2.  Definir o <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> propriedade <xref:System.ServiceModel.WSFederationHttpSecurityMode> ou <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> conforme necessário. Se um conjunto de algoritmos de <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A> é necessário, defina o <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> propriedade para um valor obtido <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.  
  
3.  Definir o <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> propriedade conforme apropriado.  
  
4.  Definir o <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> propriedade <xref:System.IdentityModel.Tokens.SecurityKeyType> `SymmetricKey` ou.`AsymmetricKey` conforme necessário.  
  
5.  Definir o <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> propriedade para o valor apropriado. Se nenhum valor for definido, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] padrão é "http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1", que indica os tokens SAML 1.1.  
  
6.  Necessário no cliente se nenhum emissor local for especificado; opcional no serviço. Criar um <xref:System.ServiceModel.EndpointAddress> que contém as informações de endereço e a identidade do serviço de token de segurança e atribua o <xref:System.ServiceModel.EndpointAddress> de instância para o <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> propriedade.  
  
7.  Necessário no cliente se nenhum emissor local for especificado; não usado no serviço. Criar um <xref:System.ServiceModel.Channels.Binding> para o `SecurityTokenService` e atribua o <xref:System.ServiceModel.Channels.Binding> de instância para o <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> propriedade.  
  
8.  Não usado no cliente; opcional no serviço. Criar um <xref:System.ServiceModel.EndpointAddress> instância para os metadados do serviço de token de segurança e atribuí-la para o `IssuerMetadataAddress` propriedade.  
  
9. Opcional no cliente e o serviço. Criar e adicionar um ou mais <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> instâncias para a coleção retornada pelo <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A> propriedade.  
  
10. Opcional no cliente e o serviço. Criar e adicionar um ou mais <xref:System.Xml.XmlElement> instâncias para a coleção retornada pelo <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A> propriedade.  
  
### <a name="to-create-a-federated-endpoint-in-configuration"></a>Para criar um ponto de extremidade federado na configuração  
  
1.  Criar um [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) como um filho de [ \<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elemento no arquivo de configuração do aplicativo.  
  
2.  Criar um [ \<associação >](../../../../docs/framework/misc/binding.md) elemento como um filho do [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) e defina o `name` de atributo para um valor apropriado.  
  
3.  Criar um `<security>` elemento como um filho de [ \<associação >](../../../../docs/framework/misc/binding.md) elemento.  
  
4.  Definir o `mode` atributo no `<security>` elemento com um valor de `Message` ou `TransportWithMessageCredential`, conforme necessário.  
  
5.  Criar um `<message>` elemento como um filho de `<security>` elemento.  
  
6.  Opcional. Definir o `algorithmSuite` atributo no `<message>` elemento com um valor apropriado. O padrão é `Basic256`.  
  
7.  Opcional. Se uma chave assimétrica de prova é necessária, defina o `issuedKeyType` atributo do `<message>` elemento `AsymmetricKey`. O padrão é `SymmetricKey`.  
  
8.  Opcional. Definir o `issuedTokenType` atributo no `<message>` elemento.  
  
9. Necessário no cliente se nenhum emissor local for especificado; opcional no serviço. Criar um `<issuer>` elemento como um filho de `<message>` elemento.  
  
10. Definir o `address` de atributo para o `<issuer>` elemento e especifique o endereço no qual o serviço de token de segurança aceita solicitações de token.  
  
11. Opcional. Adicionar um `<identity>` elemento filho e especifique a identidade do serviço de token de segurança  
  
12. Para obter mais informações, consulte [autenticação e identidade de serviço](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
13. Necessário no cliente se nenhum emissor local for especificado; não usado no serviço. Criar um [ \<associação >](../../../../docs/framework/misc/binding.md) elemento na seção de associações que pode ser usado para se comunicar com o serviço de token de segurança. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] criar uma associação, consulte [como: especificar uma associação de serviço na configuração](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).  
  
14. Especificar a associação criada na etapa anterior, definindo o `binding` e `bindingConfiguration` atributos do `<issuer>` elemento.  
  
15. Não usado no cliente; opcional no serviço. Criar um `<issuerMetadata>` elemento como um filho de <`message`> elemento. Em seguida, em um `address` atributo no `<issuerMetadata>` elemento, especifique o endereço no qual o serviço de token de segurança é publicar seus metadados. Opcionalmente, adicione um `<identity>` elemento filho e especifique a identidade do serviço de token de segurança.  
  
16. Opcional no cliente e o serviço. Adicionar um `<claimTypeRequirements>` elemento como um filho de `<message>` elemento. Especificar declarações obrigatórias e opcionais que o serviço depende adicionando [ \<Adicionar >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) elementos para o `<claimTypeRequirements>` tipo de elemento e especificando a declaração com o `claimType` atributo. Especifique se uma declaração fornecida é obrigatório ou opcional definindo o `isOptional` atributo.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir mostra o código para configurar um `WSFederationHttpBinding` imperativa.  
  
 [!code-csharp[c_FederationBinding#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)] 
 [!code-vb[c_FederationBinding#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]  
  
## <a name="see-also"></a>Consulte também  
 [Federação](../../../../docs/framework/wcf/feature-details/federation.md)  
 [Exemplo de federação](../../../../docs/framework/wcf/samples/federation-sample.md)  
 [Como: desabilitar sessões seguras em um WSFederationHttpBinding](../../../../docs/framework/wcf/feature-details/how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
