---
title: Como criar uma associação duplex federada
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 3ecd9e2dbeb30bb255cbf66488b50a9b20219431
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141724"
---
# <a name="how-to-create-a-duplex-federated-binding"></a>Como criar uma associação duplex federada

<xref:System.ServiceModel.WSFederationHttpBinding> só dá suporte aos contratos de troca de datagrama e solicitação/resposta. Para usar o contrato de troca de mensagens duplex, você deve criar uma associação personalizada. Os procedimentos a seguir mostram como fazer isso na configuração, usando a segurança do modo de mensagem para os transportes HTTP e TCP e usando a segurança de modo misto para o transporte TCP. O código de exemplo mostrando todas as 3 associações está no final deste tópico.

Você também pode criar a associação no código. Para obter uma descrição da pilha de elementos de associação a ser criada, consulte [como: criar uma associação personalizada usando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).

## <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>Para criar uma associação personalizada de duplex federado com HTTP

1. No [\<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) nó do arquivo de configuração, crie um\<elemento de [> personalizadobinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .

2. Dentro do elemento [\<custombinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , crie um elemento [\<Binding >](../../configure-apps/file-schema/wcf/bindings.md) com o atributo `name` definido como `FederationDuplexHttpMessageSecurityBinding`.

3. Dentro do elemento [> de associação de\<](../../configure-apps/file-schema/wcf/bindings.md) , crie um elemento de > de [segurança\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) com o atributo `authenticationMode` definido como `SecureConversation`.

4. Dentro do elemento [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um elemento [\<SecureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) com o atributo `authenticationMode` definido como `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated`.

5. Seguindo o elemento de [> de segurança\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um elemento de [> de\<compositeDuplex](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) vazio.

6. Seguindo o elemento [\<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) , crie um elemento [\<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) vazio.

7. Seguindo o elemento [\<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) , crie um elemento de [> de\<httpTransport](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) vazio.

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>Para criar uma associação personalizada de duplex federado com o modo de segurança de mensagem TCP

1. No [\<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) nó do arquivo de configuração, crie um\<elemento de [> personalizadobinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .

2. Dentro do elemento [\<custombinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , crie um elemento [\<Binding >](../../configure-apps/file-schema/wcf/bindings.md) com o atributo `name` definido como `FederationDuplexTcpMessageSecurityBinding`.

3. Dentro do elemento [> de associação de\<](../../configure-apps/file-schema/wcf/bindings.md) , crie um elemento de > de [segurança\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) com o atributo `authenticationMode` definido como `SecureConversation`.

4. Dentro do elemento [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um elemento [\<SecureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) com o atributo `authenticationMode` definido como `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated`.

5. Seguindo o elemento de [> de segurança\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um elemento de [> de\<tcpTransport](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) vazio.

## <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>Para criar uma associação personalizada de duplex federado com o modo de segurança mista TCP

1. No [\<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) nó do arquivo de configuração, crie um\<elemento de [> personalizadobinding](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) .

2. Dentro do elemento [\<custombinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) , crie um elemento [\<Binding >](../../configure-apps/file-schema/wcf/bindings.md) com o atributo `name` definido como `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.

3. Dentro do elemento [> de associação de\<](../../configure-apps/file-schema/wcf/bindings.md) , crie um elemento de > de [segurança\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) com o atributo `authenticationMode` definido como `SecureConversation`.

4. Dentro do elemento [\<security >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um elemento [\<SecureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) com o atributo `authenticationMode` definido como `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated`.

5. Seguindo o elemento de [> de segurança\<](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) , crie um elemento de [> de\<sslStreamSecurity](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) vazio.

6. Seguindo o elemento [\<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) , crie um elemento de [> tcpTransport vazio\<](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) .

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
