---
title: 'Como: criar uma WSFederationHttpBinding'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: e54897d7-aa6c-46ec-a278-b2430c8c2e10
ms.openlocfilehash: 9728c908331d5eabcff04d094e7fcbe42f636963
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911217"
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>Como: criar uma WSFederationHttpBinding

No Windows Communication Foundation (WCF), a <xref:System.ServiceModel.WSFederationHttpBinding> classe ([\<WSFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) na configuração) fornece um mecanismo para expor um serviço federado. Ou seja, um serviço que exige que os clientes se autentiquem usando um token de segurança emitido por um serviço de token de segurança. Este tópico mostra como configurar um <xref:System.ServiceModel.WSFederationHttpBinding> no código e na configuração. Depois que a associação é criada, você pode configurar um ponto de extremidade para usar essa associação.

 As etapas básicas são descritas a seguir:

1. Selecione um modo de segurança. O <xref:System.ServiceModel.WSFederationHttpBinding> oferece `Message`suporte, que fornece segurança de ponta a ponta no nível de mensagem, mesmo entre vários saltos e `TransportWithMessageCredential`, que fornece melhor desempenho em casos em que o cliente e o serviço podem fazer uma conexão direta HTTPS.

    > [!NOTE]
    > O <xref:System.ServiceModel.WSFederationHttpBinding> também dá `None` suporte como modo de segurança. Esse modo não é seguro e é fornecido apenas para fins de depuração. Se um ponto de extremidade de serviço for <xref:System.ServiceModel.WSFederationHttpBinding> implantado com um com `None`seu modo de segurança definido como, a associação de cliente resultante (gerada pela [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)é um <xref:System.ServiceModel.WSHttpBinding> com um modo de segurança de `None`.

     Ao contrário de outras associações fornecidas pelo sistema, não é necessário selecionar um tipo de credencial de cliente ao `WSFederationHttpBinding`usar o. Isso ocorre porque o tipo de credencial do cliente é sempre um token emitido. O WCF adquire um token de um emissor especificado e apresenta esse token ao serviço para autenticar o cliente.

2. Em clientes federados, defina a <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> Propriedade como a URL do serviço de token de segurança. <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> Defina como a associação a ser usada para se comunicar com o serviço de token de segurança.

3. Opcional. Defina a <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> propriedade para o Uniform Resource Identifier (URI) de um tipo de token. Em serviços federados, especifique o tipo de token que o serviço espera. Em clientes federados, especifique o tipo de token que o cliente solicita do serviço de token de segurança.

     Se nenhum tipo de token for especificado, os clientes gerarão tokens de segurança de solicitação WS-Trust (RSTs) sem um URI de tipo de token e os serviços esperam a autenticação de cliente usando um token 1,1 SAML (Security Asserts Markup Language) por padrão.

     O URI para um token SAML 1,1 é `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.

4. Opcional. Em serviços federados, defina a <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> Propriedade como a URL de metadados de um serviço de token de segurança. O ponto de extremidade de metadados permite que os clientes do serviço selecionem um par de ligação/ponto de extremidade apropriado, se o serviço estiver configurado para publicar metadados. Para obter mais informações sobre como publicar metadados, consulte [publicando metadados](publishing-metadata.md).

 Você também pode definir outras propriedades, incluindo o tipo de chave usada como uma chave de prova no token emitido, o conjunto de algoritmos a ser usado entre o cliente e o serviço, se deseja negociar ou especificar explicitamente a credencial do serviço, qualquer declaração específica do serviço Espera que o token emitido contenha e quaisquer elementos XML adicionais que devam ser adicionados à solicitação que o cliente envia para o serviço de token de segurança.

> [!NOTE]
> A `NegotiateServiceCredential` propriedade só é relevante quando o `SecurityMode` é definido como `Message`. Se `SecurityMode` for definido como `TransportWithMessageCredential`, a `NegotiateServiceCredential` propriedade será ignorada.

## <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>Para configurar um WSFederationHttpBinding no código

1. Crie uma instância do <xref:System.ServiceModel.WSFederationHttpBinding>.

2. Defina a <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> Propriedade como <xref:System.ServiceModel.WSFederationHttpSecurityMode> ou <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> conforme necessário. Se um conjunto de algoritmos <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A> diferente de for necessário, <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> defina a propriedade como um valor <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>obtido de.

3. Defina a <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> Propriedade conforme apropriado.

4. Defina a <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> Propriedade como <xref:System.IdentityModel.Tokens.SecurityKeyType> `SymmetricKey` ou.`AsymmetricKey` conforme necessário.

5. Defina a <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> propriedade para o valor apropriado. Se nenhum valor for definido, o WCF usa como `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`padrão o, que indica tokens SAML 1,1.

6. Necessário no cliente se nenhum emissor local for especificado; opcional no serviço. Crie um <xref:System.ServiceModel.EndpointAddress> que contenha as informações de endereço e identidade do serviço de token de segurança <xref:System.ServiceModel.EndpointAddress> e atribua a <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> instância à propriedade.

7. Necessário no cliente se nenhum emissor local for especificado; Não usado no serviço. Crie um <xref:System.ServiceModel.Channels.Binding> para o `SecurityTokenService` <xref:System.ServiceModel.Channels.Binding> e<xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> atribua a instância à propriedade.

8. Não usado no cliente; opcional no serviço. Crie uma <xref:System.ServiceModel.EndpointAddress> instância para os metadados do serviço de token de segurança e atribua-a `IssuerMetadataAddress` à propriedade.

9. Opcional no cliente e no serviço. Crie e adicione uma ou mais <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> instâncias à coleção retornada <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A> pela propriedade.

10. Opcional no cliente e no serviço. Crie e adicione uma ou mais <xref:System.Xml.XmlElement> instâncias à coleção retornada <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A> pela propriedade.

## <a name="to-create-a-federated-endpoint-in-configuration"></a>Para criar um ponto de extremidade federado na configuração

1. Crie um [ \<> WSFederationHttpBinding](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) como [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) um filho do elemento bindings > no arquivo de configuração do aplicativo.

2. Crie um [ \<](../../../../docs/framework/misc/binding.md) elemento de > de associação como um filho de [ \<WSFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) e `name` defina o atributo como um valor apropriado.

3. Crie um `<security>` elemento como um filho [ \<](../../../../docs/framework/misc/binding.md) do elemento de > de associação.

4. Defina o `mode` `<security>` atributo no elemento como um valor de `Message` ou `TransportWithMessageCredential`, conforme necessário.

5. Crie um `<message>` elemento como um filho `<security>` do elemento.

6. Opcional. Defina o `algorithmSuite` atributo `<message>` no elemento com um valor apropriado. O padrão é `Basic256`.

7. Opcional. Se uma chave `<message>` de prova assimétrica for necessária, `issuedKeyType` defina o atributo do elemento `AsymmetricKey`como. O padrão é `SymmetricKey`.

8. Opcional. Defina o `issuedTokenType` atributo `<message>` no elemento.

9. Necessário no cliente se nenhum emissor local for especificado; opcional no serviço. Crie um `<issuer>` elemento como um filho `<message>` do elemento.

10. Defina o `address` atributo para o `<issuer>` elemento e especifique o endereço no qual o serviço de token de segurança aceita solicitações de token.

11. Opcional. Adicionar um `<identity>` elemento filho e especificar a identidade do serviço de token de segurança

12. Para obter mais informações, consulte [identidade de serviço e autenticação](service-identity-and-authentication.md).

13. Necessário no cliente se nenhum emissor local for especificado; Não usado no serviço. Crie um [ \<](../../../../docs/framework/misc/binding.md) elemento de > de associação na seção de associações que pode ser usado para se comunicar com o serviço de token de segurança. Para obter mais informações sobre como criar uma associação [, consulte Como: Especifique uma associação de serviço na](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md)configuração.

14. Especifique a associação criada na etapa anterior definindo os `binding` atributos e `bindingConfiguration` do `<issuer>` elemento.

15. Não usado no cliente; opcional no serviço. Crie um `<issuerMetadata>` elemento como um filho do elemento <`message`>. Em seguida, em `address` um atributo `<issuerMetadata>` no elemento, especifique o endereço no qual o serviço de token de segurança é para publicar seus metadados. Opcionalmente, adicione um `<identity>` elemento filho e especifique a identidade do serviço de token de segurança.

16. Opcional no cliente e no serviço. Adicione um `<claimTypeRequirements>` elemento como um filho `<message>` do elemento. Especifique as declarações obrigatórias e opcionais nas quais o serviço depende [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) adicionando elementos de > ao `<claimTypeRequirements>` elemento e especificando o tipo de declaração com `claimType` o atributo. Especifique se uma determinada declaração é necessária ou opcional definindo o `isOptional` atributo.

## <a name="example"></a>Exemplo

O exemplo de código a seguir mostra o código para `WSFederationHttpBinding` configurar um imperativo.

[!code-csharp[c_FederationBinding#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)]
[!code-vb[c_FederationBinding#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]

## <a name="see-also"></a>Consulte também

- [Federação](federation.md)
- [Exemplo de federação](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Como: Desabilitar sessões seguras em um WSFederationHttpBinding](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
