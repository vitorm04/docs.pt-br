---
title: Como criar uma WSFederationHttpBinding
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF, federation
- federation
ms.assetid: e54897d7-aa6c-46ec-a278-b2430c8c2e10
ms.openlocfilehash: c3ce90c74ae61dfcbfc0b05fc17b25fe0118e071
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141697"
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>Como criar uma WSFederationHttpBinding

No Windows Communication Foundation (WCF), a classe <xref:System.ServiceModel.WSFederationHttpBinding> ([\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) na configuração) fornece um mecanismo para expor um serviço federado. Ou seja, um serviço que exige que os clientes se autentiquem usando um token de segurança emitido por um serviço de token de segurança. Este tópico mostra como configurar um <xref:System.ServiceModel.WSFederationHttpBinding> no código e na configuração. Depois que a associação é criada, você pode configurar um ponto de extremidade para usar essa associação.

 As etapas básicas são descritas a seguir:

1. Selecione um modo de segurança. O <xref:System.ServiceModel.WSFederationHttpBinding> dá suporte a `Message`, que fornece segurança de ponta a ponta no nível de mensagem, mesmo entre vários saltos e `TransportWithMessageCredential`, que fornece melhor desempenho em casos em que o cliente e o serviço podem fazer uma conexão direta via HTTPS.

    > [!NOTE]
    > O <xref:System.ServiceModel.WSFederationHttpBinding> também dá suporte a `None` como modo de segurança. Esse modo não é seguro e é fornecido apenas para fins de depuração. Se um ponto de extremidade de serviço for implantado com um <xref:System.ServiceModel.WSFederationHttpBinding> com seu modo de segurança definido como `None`, a associação de cliente resultante (gerada pela [ferramenta de utilitário de metadados ServiceModel (svcutil. exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)) é uma <xref:System.ServiceModel.WSHttpBinding> com um modo de segurança de `None`.

     Ao contrário de outras associações fornecidas pelo sistema, não é necessário selecionar um tipo de credencial de cliente ao usar o `WSFederationHttpBinding`. Isso ocorre porque o tipo de credencial do cliente é sempre um token emitido. O WCF adquire um token de um emissor especificado e apresenta esse token ao serviço para autenticar o cliente.

2. Em clientes federados, defina a propriedade <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> como a URL do serviço de token de segurança. Defina o <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> como a associação a ser usada para se comunicar com o serviço de token de segurança.

3. Opcional. Defina a propriedade <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> como o Uniform Resource Identifier (URI) de um tipo de token. Em serviços federados, especifique o tipo de token que o serviço espera. Em clientes federados, especifique o tipo de token que o cliente solicita do serviço de token de segurança.

     Se nenhum tipo de token for especificado, os clientes gerarão tokens de segurança de solicitação WS-Trust (RSTs) sem um URI de tipo de token e os serviços esperam a autenticação de cliente usando um token 1,1 SAML (Security Asserts Markup Language) por padrão.

     O URI para um token 1,1 SAML é `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.

4. Opcional. Em serviços federados, defina a propriedade <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> como a URL de metadados de um serviço de token de segurança. O ponto de extremidade de metadados permite que os clientes do serviço selecionem um par de ligação/ponto de extremidade apropriado, se o serviço estiver configurado para publicar metadados. Para obter mais informações sobre como publicar metadados, consulte [publicando metadados](publishing-metadata.md).

 Você também pode definir outras propriedades, incluindo o tipo de chave usada como uma chave de prova no token emitido, o conjunto de algoritmos a ser usado entre o cliente e o serviço, se deseja negociar ou especificar explicitamente a credencial do serviço, qualquer declaração específica do serviço Espera que o token emitido contenha e quaisquer elementos XML adicionais que devam ser adicionados à solicitação que o cliente envia para o serviço de token de segurança.

> [!NOTE]
> A propriedade `NegotiateServiceCredential` só é relevante quando a `SecurityMode` é definida como `Message`. Se `SecurityMode` for definido como `TransportWithMessageCredential`, a propriedade `NegotiateServiceCredential` será ignorada.

## <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>Para configurar um WSFederationHttpBinding no código

1. Crie uma instância do <xref:System.ServiceModel.WSFederationHttpBinding>.

2. Defina a propriedade <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> como <xref:System.ServiceModel.WSFederationHttpSecurityMode> ou <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> conforme necessário. Se um conjunto de algoritmos diferente de <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A> for necessário, defina a propriedade <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> como um valor obtido de <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.

3. Defina a propriedade <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> conforme apropriado.

4. Defina a propriedade <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> como <xref:System.IdentityModel.Tokens.SecurityKeyType>`SymmetricKey` ou.`AsymmetricKey` conforme necessário.

5. Defina a propriedade <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> como o valor apropriado. Se nenhum valor for definido, o WCF usa como padrão `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`, que indica tokens SAML 1,1.

6. Necessário no cliente se nenhum emissor local for especificado; opcional no serviço. Crie um <xref:System.ServiceModel.EndpointAddress> que contenha as informações de endereço e identidade do serviço de token de segurança e atribua a instância de <xref:System.ServiceModel.EndpointAddress> à propriedade <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A>.

7. Necessário no cliente se nenhum emissor local for especificado; Não usado no serviço. Crie um <xref:System.ServiceModel.Channels.Binding> para o `SecurityTokenService` e atribua a instância de <xref:System.ServiceModel.Channels.Binding> à propriedade <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A>.

8. Não usado no cliente; opcional no serviço. Crie uma instância de <xref:System.ServiceModel.EndpointAddress> para os metadados do serviço de token de segurança e atribua-o à propriedade `IssuerMetadataAddress`.

9. Opcional no cliente e no serviço. Crie e adicione uma ou mais instâncias de <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> à coleção retornada pela propriedade <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>.

10. Opcional no cliente e no serviço. Crie e adicione uma ou mais instâncias de <xref:System.Xml.XmlElement> à coleção retornada pela propriedade <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A>.

## <a name="to-create-a-federated-endpoint-in-configuration"></a>Para criar um ponto de extremidade federado na configuração

1. Crie um [\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) como um filho do elemento [\<bindings >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) no arquivo de configuração do aplicativo.

2. Crie um elemento de [> de associação de\<](../../configure-apps/file-schema/wcf/bindings.md) como um filho de [\<WSFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) e defina o atributo `name` como um valor apropriado.

3. Crie um elemento `<security>` como um filho do elemento [> de associação de\<](../../configure-apps/file-schema/wcf/bindings.md) .

4. Defina o atributo `mode` no elemento `<security>` como um valor de `Message` ou `TransportWithMessageCredential`, conforme necessário.

5. Crie um elemento `<message>` como um filho do elemento `<security>`.

6. Opcional. Defina o atributo `algorithmSuite` no elemento `<message>` com um valor apropriado. O padrão é `Basic256`.

7. Opcional. Se uma chave de prova assimétrica for necessária, defina o atributo `issuedKeyType` do elemento `<message>` como `AsymmetricKey`. O padrão é `SymmetricKey`.

8. Opcional. Defina o atributo `issuedTokenType` no elemento `<message>`.

9. Necessário no cliente se nenhum emissor local for especificado; opcional no serviço. Crie um elemento `<issuer>` como um filho do elemento `<message>`.

10. Defina o atributo `address` como o elemento `<issuer>` e especifique o endereço no qual o serviço de token de segurança aceita solicitações de token.

11. Opcional. Adicionar um `<identity>` elemento filho e especificar a identidade do serviço de token de segurança

12. Para obter mais informações, consulte [identidade de serviço e autenticação](service-identity-and-authentication.md).

13. Necessário no cliente se nenhum emissor local for especificado; Não usado no serviço. Crie um elemento de [> de associação de\<](../../configure-apps/file-schema/wcf/bindings.md) na seção de associações que pode ser usada para se comunicar com o serviço de token de segurança. Para obter mais informações sobre como criar uma associação, consulte [como especificar uma associação de serviço na configuração](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).

14. Especifique a associação criada na etapa anterior definindo os atributos `binding` e `bindingConfiguration` do elemento `<issuer>`.

15. Não usado no cliente; opcional no serviço. Crie um elemento `<issuerMetadata>` como um filho do elemento <`message`>. Em seguida, em um atributo `address` no elemento `<issuerMetadata>`, especifique o endereço no qual o serviço de token de segurança deve publicar seus metadados. Opcionalmente, adicione um elemento filho `<identity>` e especifique a identidade do serviço de token de segurança.

16. Opcional no cliente e no serviço. Adicione um elemento `<claimTypeRequirements>` como um filho do elemento `<message>`. Especifique as declarações obrigatórias e opcionais nas quais o serviço depende adicionando [\<adicionar elementos >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) ao elemento `<claimTypeRequirements>` e especificando o tipo de declaração com o atributo `claimType`. Especifique se uma determinada declaração é necessária ou opcional definindo o atributo `isOptional`.

## <a name="example"></a>Exemplo

O exemplo de código a seguir mostra o código para configurar um `WSFederationHttpBinding` imperativo.

[!code-csharp[c_FederationBinding#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)]
[!code-vb[c_FederationBinding#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]

## <a name="see-also"></a>Consulte também

- [Federação](federation.md)
- [Exemplo de federação](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Como: desabilitar sessões seguras em um WSFederationHttpBinding](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)
