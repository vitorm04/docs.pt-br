---
title: 'Como: criar uma associação duplex federada'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 71c970fa45d7d4ccd55fceddb2360d0aa0a768f8
ms.sourcegitcommit: a97ecb94437362b21fffc5eb3c38b6c0b4368999
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/13/2019
ms.locfileid: "68972057"
---
# <a name="how-to-create-a-duplex-federated-binding"></a>Como: criar uma associação duplex federada

<xref:System.ServiceModel.WSFederationHttpBinding>o só dá suporte aos contratos de troca de datagrama e solicitação/resposta. Para usar o contrato de troca de mensagens duplex, você deve criar uma associação personalizada. Os procedimentos a seguir mostram como fazer isso na configuração, usando a segurança do modo de mensagem para os transportes HTTP e TCP e usando a segurança de modo misto para o transporte TCP. O código de exemplo mostrando todas as 3 associações está no final deste tópico.

Você também pode criar a associação no código. Para obter uma descrição da pilha de elementos de associação a ser [criada, consulte Como: Crie uma associação personalizada usando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>Para criar uma associação personalizada de duplex federado com HTTP

1. No nó [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) associações > do arquivo de configuração, crie um elemento personalizado de >. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)

2. Dentro do [ \<elemento > personalizado](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , crie um `name` `FederationDuplexHttpMessageSecurityBinding` [ \<elemento de associação >](../../../../docs/framework/misc/binding.md) com o atributo definido como.

3. Dentro do [ \<elemento Binding >](../../../../docs/framework/misc/binding.md) , crie um [ \<elemento Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) com o `authenticationMode` atributo definido como `SecureConversation`.

4. Dentro do elemento de [ \<> de segurança](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um `authenticationMode` `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` [ \<elemento SecureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) com o atributo definido como ou.

5. Seguindo o elemento de [ \<> de segurança](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um elemento [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) vazio.

6. Seguindo o [ \<elemento > compositeDuplex](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) , crie um elemento de [ \<> de oneWay](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) vazio.

7. Seguindo o [ \<elemento oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) , crie um elemento [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) vazio.

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>Para criar uma associação personalizada de duplex federado com o modo de segurança de mensagem TCP

1. No nó [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) associações > do arquivo de configuração, crie um elemento personalizado de >. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)

2. Dentro do [ \<elemento > personalizado](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , crie um `name` `FederationDuplexTcpMessageSecurityBinding` [ \<elemento de associação >](../../../../docs/framework/misc/binding.md) com o atributo definido como.

3. Dentro do [ \<elemento Binding >](../../../../docs/framework/misc/binding.md) , crie um [ \<elemento Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) com o `authenticationMode` atributo definido como `SecureConversation`.

4. Dentro do elemento de [ \<> de segurança](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um `authenticationMode` `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` [ \<elemento SecureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) com o atributo definido como ou.

5. Seguindo o elemento de [ \<> de segurança](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um elemento [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) vazio.

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>Para criar uma associação personalizada de duplex federado com o modo de segurança mista TCP

1. No nó [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) associações > do arquivo de configuração, crie um elemento personalizado de >. [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)

2. Dentro do [ \<elemento > personalizado](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , crie um `name` `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding` [ \<elemento de associação >](../../../../docs/framework/misc/binding.md) com o atributo definido como.

3. Dentro do [ \<elemento Binding >](../../../../docs/framework/misc/binding.md) , crie um [ \<elemento Security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) com o `authenticationMode` atributo definido como `SecureConversation`.

4. Dentro do elemento de [ \<> de segurança](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um `authenticationMode` `IssuedTokenForCertificate` `IssuedTokenForSslNegotiated` [ \<elemento SecureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) com o atributo definido como ou.

5. Seguindo o elemento de [ \<> de segurança](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um elemento [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) vazio.

6. Seguindo o [ \<elemento > sslStreamSecurity](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) , crie um elemento [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) vazio.

## <a name="code-sample"></a>Exemplo de código

### <a name="sample-with-3-bindings"></a>Exemplo com 3 associações

1. Insira o código a seguir no arquivo de configuração.

## <a name="example"></a>Exemplo

```xml
<bindings>
   <customBinding>
      <binding name="FederationDuplexHttpMessageSecurityBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />
          </security>
          <compositeDuplex />
          <oneWay />
          <httpTransport />
       </binding>
<!-- duplex over https is not supported -->
       <binding name="FederationDuplexTcpMessageSecurityBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenForSslNegotiated" />
          </security>
          <tcpTransport />
       </binding>
       <binding name="FederationDuplexTcpTransportSecurityWithMessageCredentialsBinding">
<!-- duplex contract requires secure conversation with require cancellation = true -->
          <security authenticationMode="SecureConversation">
              <secureConversationBootstrap authenticationMode="IssuedTokenOverTransport" />
          </security>
<!-- requireClientCertificate = true or <windowsStreamSecurity /> can be used, but does not make sense for most scenarios -->
          <sslStreamSecurity />
          <tcpTransport />
       </binding>
    </customBinding>
</bindings>
```
