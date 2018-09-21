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
ms.openlocfilehash: 16b93126157ff129d5e0b815bc951873e7fa760d
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46525533"
---
# <a name="how-to-create-a-wsfederationhttpbinding"></a>Como criar uma WSFederationHttpBinding

No Windows Communication Foundation (WCF), o <xref:System.ServiceModel.WSFederationHttpBinding> classe ([\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) na configuração) fornece um mecanismo para expor um serviço federado. Ou seja, um serviço que exige que os clientes autentiquem usando um token de segurança emitido por um serviço de token de segurança. Este tópico mostra como configurar um <xref:System.ServiceModel.WSFederationHttpBinding> no código e configuração. Depois que a associação é criada, você pode configurar um ponto de extremidade para usar essa associação.

 As etapas básicas são descritas da seguinte maneira:

1. Selecione um modo de segurança. O <xref:System.ServiceModel.WSFederationHttpBinding> suporta `Message`, que fornece segurança de ponta a ponta no nível da mensagem, até mesmo em vários saltos, e `TransportWithMessageCredential`, que fornece um melhor desempenho em casos em que o cliente e o serviço podem fazer uma conexão direta ao longo HTTPS.

    > [!NOTE]
    > O <xref:System.ServiceModel.WSFederationHttpBinding> também dá suporte a `None` como um modo de segurança. Esse modo não é seguro e é fornecido apenas para fins de depuração. Se um ponto de extremidade de serviço é implantado com um <xref:System.ServiceModel.WSFederationHttpBinding> com seu modo de segurança definido como `None`, a associação de cliente resultante (gerado pelo [ferramenta Utilitário de metadados ServiceModel (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)) é um <xref:System.ServiceModel.WSHttpBinding> com um modo de segurança do `None`.

     Ao contrário de outras associações fornecidas pelo sistema, não é necessário selecionar um tipo de credencial de cliente ao usar o `WSFederationHttpBinding`. Isso ocorre porque o tipo de credencial de cliente é sempre um token emitido. O WCF adquire um token de um emissor especificado e apresenta esse token para o serviço para autenticar o cliente.

2. Em clientes federados, defina o <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> propriedade para a URL do serviço de token de segurança. Defina o <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> para associação a ser usada para se comunicar com o serviço de token de segurança.

3. Opcional. Defina o <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> propriedade para o URI Uniform Resource Identifier () de um tipo de token. Em serviços federados, especifique o tipo de token que o serviço espera. Em clientes federados, especifique o tipo de token as solicitações de cliente do serviço de token de segurança.

     Se nenhum tipo de token for especificado, clientes geram Tokens de segurança de solicitação do WS-Trust (RSTs) sem um URI de tipo de token e serviços de esperar que a autenticação de cliente usando um token de segurança asserções Markup Language (SAML) 1.1 por padrão.

     O URI para um token SAML 1.1 é `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`.

4. Opcional. Em serviços federados, defina o <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerMetadataAddress%2A> propriedade para a URL de metadados de um serviço de token de segurança. O ponto de extremidade de metadados permite que os clientes do serviço selecionar um par de associação/ponto de extremidade apropriado, se o serviço estiver configurado para publicar os metadados. Para obter mais informações sobre metadados de publicação, consulte [metadados de publicação](publishing-metadata.md).

 Você também pode definir outras propriedades, incluindo o tipo de chave usado como uma chave de prova no token emitido, o pacote de algoritmos a ser usado entre o cliente e o serviço se negociar ou especificar explicitamente a credencial de serviço, quaisquer declarações específicas do serviço espera que o token emitido contenha e quaisquer elementos XML adicionais que devem ser adicionados à solicitação, que o cliente envia ao serviço de token de segurança.

> [!NOTE]
>  O `NegotiateServiceCredential` propriedade só é relevante quando o `SecurityMode` é definido como `Message`. Se `SecurityMode` é definido como `TransportWithMessageCredential`, em seguida, a `NegotiateServiceCredential` propriedade será ignorada.

## <a name="to-configure-a-wsfederationhttpbinding-in-code"></a>Configurar um WSFederationHttpBinding no código

1. Criar uma instância da <xref:System.ServiceModel.WSFederationHttpBinding>.

2. Defina as <xref:System.ServiceModel.WSFederationHttpSecurity.Mode%2A> propriedade para <xref:System.ServiceModel.WSFederationHttpSecurityMode> ou <xref:System.ServiceModel.WSFederationHttpSecurityMode.Message> conforme necessário. Se um pacote de algoritmos diferente de <xref:System.ServiceModel.Security.SecurityAlgorithmSuite.Basic256%2A> é necessário, defina a <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.AlgorithmSuite%2A> propriedade para um valor obtido da <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>.

3. Defina o <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.NegotiateServiceCredential%2A> propriedade conforme apropriado.

4. Defina as <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedKeyType%2A> propriedade para <xref:System.IdentityModel.Tokens.SecurityKeyType> `SymmetricKey` ou.`AsymmetricKey` conforme necessário.

5. Defina o <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuedTokenType%2A> propriedade para o valor apropriado. Se nenhum valor for definido, o WCF usará como padrão `http://docs.oasis-open.org/wss/oasis-wss-saml-token-profile-1.1#SAMLV1.1`, que indica os tokens SAML 1.1.

6. Necessário no cliente, se nenhum emissor local for especificado; opcional no serviço. Criar uma <xref:System.ServiceModel.EndpointAddress> que contém as informações de endereço e a identidade do serviço de token de segurança e atribua os <xref:System.ServiceModel.EndpointAddress> da instância para o <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerAddress%2A> propriedade.

7. Necessário no cliente, se nenhum emissor local for especificado; não usado no serviço. Criar uma <xref:System.ServiceModel.Channels.Binding> para o `SecurityTokenService` e atribua a <xref:System.ServiceModel.Channels.Binding> da instância para o <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.IssuerBinding%2A> propriedade.

8. Não usado no cliente; opcional no serviço. Criar uma <xref:System.ServiceModel.EndpointAddress> de instância para os metadados do serviço de token de segurança e o atribui a `IssuerMetadataAddress` propriedade.

9. Opcional no cliente e o serviço. Criar e adicionar um ou mais <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement> instâncias para a coleção retornada pela <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A> propriedade.

10. Opcional no cliente e o serviço. Criar e adicionar um ou mais <xref:System.Xml.XmlElement> instâncias para a coleção retornada pela <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.TokenRequestParameters%2A> propriedade.

## <a name="to-create-a-federated-endpoint-in-configuration"></a>Para criar um ponto de extremidade federado na configuração

1. Criar um [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) como um filho de [ \<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elemento no arquivo de configuração do aplicativo.

2. Criar uma [ \<associação >](../../../../docs/framework/misc/binding.md) elemento como um filho [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md) e defina o `name` de atributo para um valor apropriado.

3. Criar uma `<security>` elemento como um filho de [ \<associação >](../../../../docs/framework/misc/binding.md) elemento.

4. Defina a `mode` atributo o `<security>` elemento em um valor de `Message` ou `TransportWithMessageCredential`, conforme necessário.

5. Criar uma `<message>` elemento como um filho de `<security>` elemento.

6. Opcional. Defina a `algorithmSuite` atributo a `<message>` elemento com um valor apropriado. O padrão é `Basic256`.

7. Opcional. Se uma chave de prova assimétrica for necessária, defina o `issuedKeyType` atributo o `<message>` elemento a ser `AsymmetricKey`. O padrão é `SymmetricKey`.

8. Opcional. Defina a `issuedTokenType` atributo a `<message>` elemento.

9. Necessário no cliente, se nenhum emissor local for especificado; opcional no serviço. Criar uma `<issuer>` elemento como um filho de `<message>` elemento.

10. Defina as `address` de atributo para o `<issuer>` elemento e especifique o endereço no qual o serviço de token de segurança aceita solicitações de token.

11. Opcional. Adicionar um `<identity>` elemento filho e especifique a identidade do serviço de token de segurança

12. Para obter mais informações, consulte [identidade de serviço e autenticação](service-identity-and-authentication.md).

13. Necessário no cliente, se nenhum emissor local for especificado; não usado no serviço. Criar uma [ \<associação >](../../../../docs/framework/misc/binding.md) elemento na seção de associações que pode ser usado para se comunicar com o serviço de token de segurança. Para obter mais informações sobre como criar uma associação, consulte [como: especificar uma associação de serviço na configuração](../../../../docs/framework/wcf/how-to-specify-a-service-binding-in-configuration.md).

14. Especificar a associação criada na etapa anterior, definindo o `binding` e `bindingConfiguration` atributos do `<issuer>` elemento.

15. Não usado no cliente; opcional no serviço. Criar uma `<issuerMetadata>` elemento como um filho de <`message`> elemento. Em seguida, em um `address` atributo a `<issuerMetadata>` elemento, especifique o endereço no qual o serviço de token de segurança é publicar seus metadados. Opcionalmente, adicione um `<identity>` elemento filho e especifique a identidade do serviço de token de segurança.

16. Opcional no cliente e o serviço. Adicionar um `<claimTypeRequirements>` elemento como um filho de `<message>` elemento. Especificar declarações obrigatórias e opcionais que o serviço se baseia em adicionando [ \<Adicionar >](../../../../docs/framework/configure-apps/file-schema/wcf/add-of-claimtyperequirements.md) elementos para o `<claimTypeRequirements>` tipo de elemento e especificando a declaração com o `claimType` atributo. Especifique se uma determinada declaração é obrigatório ou opcional, definindo o `isOptional` atributo.

## <a name="example"></a>Exemplo

O exemplo de código a seguir mostra o código para configurar um `WSFederationHttpBinding` imperativa.

[!code-csharp[c_FederationBinding#2](~/samples/snippets/csharp/VS_Snippets_CFX/c_federationbinding/cs/source.cs#2)]
[!code-vb[c_FederationBinding#2](~/samples/snippets/visualbasic/VS_Snippets_CFX/c_federationbinding/vb/source.vb#2)]

## <a name="see-also"></a>Consulte também

- [Federação](federation.md)
- [Exemplo de federação](../../../../docs/framework/wcf/samples/federation-sample.md)
- [Como: desabilitar sessões seguras em um WSFederationHttpBinding](how-to-disable-secure-sessions-on-a-wsfederationhttpbinding.md)