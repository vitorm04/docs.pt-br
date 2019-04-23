---
title: 'Como: criar uma associação duplex federada'
ms.date: 03/30/2017
ms.assetid: 4331d2bc-5455-492a-9189-634a82597726
ms.openlocfilehash: 510faa0b1d791b1d164c55e9fa32daafa559d56c
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59346230"
---
# <a name="how-to-create-a-duplex-federated-binding"></a>Como: criar uma associação duplex federada
<xref:System.ServiceModel.WSFederationHttpBinding> suporta apenas os contratos de troca de mensagem de datagrama e solicitação/resposta. Para usar o contrato de troca de mensagens duplex, você deve criar uma associação personalizada. Os procedimentos a seguir mostram como fazer isso na configuração, usando a segurança de modo de mensagem para os transportes HTTP e TCP e usando a segurança de modo misto para o transporte TCP. Código de exemplo que mostra todas as associações de 3 está no final deste tópico.  
  
 Você também pode criar a associação no código. Para obter uma descrição da pilha de elementos de associação para criar, consulte [como: Criar uma associação personalizada utilizando o SecurityBindingElement](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-binding-using-the-securitybindingelement.md).  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-http"></a>Para criar uma associação personalizada duplex federada com HTTP  
  
1. No [ \<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) nó do arquivo de configuração, crie um [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elemento.  
  
2. Dentro de [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elemento, criar uma [ \<associação >](../../../../docs/framework/misc/binding.md) elemento com o `name` atributo definido como `FederationDuplexHttpMessageSecurityBinding`.  
  
3. Dentro de [ \<associação >](../../../../docs/framework/misc/binding.md) elemento, criar uma [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento com o `authenticationMode` atributo definido como `SecureConversation`.  
  
4. Dentro de [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento, criar uma [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) elemento com o `authenticationMode` atributo definido como `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated`.  
  
5. Seguindo a [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento, criar vazio [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) elemento.  
  
6. Seguindo a [ \<compositeDuplex >](../../../../docs/framework/configure-apps/file-schema/wcf/compositeduplex.md) elemento, criar vazio [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) elemento.  
  
7. Seguindo a [ \<oneWay >](../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md) elemento, criar vazio [ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md) elemento.  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-message-security-mode"></a>Para criar uma associação personalizada duplex federada com o modo de segurança de mensagem TCP  
  
1. No [ \<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) nó do arquivo de configuração, crie um [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elemento.   
  
2. Dentro de [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elemento, criar uma [ \<associação >](../../../../docs/framework/misc/binding.md) elemento com o `name` atributo definido como `FederationDuplexTcpMessageSecurityBinding`.  
  
3. Dentro de [ \<associação >](../../../../docs/framework/misc/binding.md) elemento, criar uma [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento com o `authenticationMode` atributo definido como `SecureConversation`.  
  
4. Dentro de [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento, criar uma [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) elemento com o `authenticationMode` atributo definido como `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated`.  
  
5. Seguindo a [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento, criar vazio [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) elemento.  
  
### <a name="to-create-a-duplex-federated-custom-binding-with-tcp-mixed-security-mode"></a>Para criar um duplex federada associação personalizada com o modo de segurança mista de TCP  
  
1. No [ \<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) nó do arquivo de configuração, crie um [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elemento.   
  
2. Dentro de [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) elemento, criar uma [ \<associação >](../../../../docs/framework/misc/binding.md) elemento com o `name` atributo definido como `FederationDuplexTcpTransportSecurityWithMessageCredentialBinding`.  
  
3. Dentro de [ \<associação >](../../../../docs/framework/misc/binding.md) elemento, criar uma [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento com o `authenticationMode` atributo definido como `SecureConversation`.  
  
4. Dentro de [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento, criar uma [ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) elemento com o `authenticationMode` atributo definido como `IssuedTokenForCertificate` ou `IssuedTokenForSslNegotiated`.  
  
5. Seguindo a [ \<segurança >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) elemento, criar vazio [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) elemento.  
  
6. Seguindo a [ \<sslStreamSecurity >](../../../../docs/framework/configure-apps/file-schema/wcf/sslstreamsecurity.md) elemento, criar vazio [ \<tcpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/tcptransport.md) elemento.  
  
## <a name="code-sample"></a>Exemplo de código  
  
#### <a name="sample-with-3-bindings"></a>Exemplo com associações de 3  
  
1. Insira o código a seguir em seu arquivo de configuração.  
  
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
