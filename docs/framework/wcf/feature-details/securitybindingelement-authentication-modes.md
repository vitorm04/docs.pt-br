---
title: SecurityBindingElement Authentication Modes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 12300bf4-c730-4405-9f65-d286f68b5a43
ms.openlocfilehash: d6831452370b672a6c02ace31dc05ef07ca48154
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/16/2019
ms.locfileid: "74141646"
---
# <a name="securitybindingelement-authentication-modes"></a>SecurityBindingElement Authentication Modes
O Windows Communication Foundation (WCF) fornece vários modos pelos quais os clientes e serviços se autenticam entre si. Você pode criar elementos de associação de segurança para esses modos de autenticação usando métodos estáticos na classe <xref:System.ServiceModel.Channels.SecurityBindingElement> ou por meio da configuração. Este tópico descreve brevemente os 18 modos de autenticação.  
  
 Para obter um exemplo de como usar o elemento para um dos modos de autenticação, consulte [como: criar um SecurityBindingElement para um modo de autenticação especificado](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="basic-configuration-programming"></a>Programação de configuração básica  
 O procedimento a seguir descreve como definir o modo de autenticação em um arquivo de configuração.  
  
#### <a name="to-set-the-authentication-mode-in-configuration"></a>Para definir o modo de autenticação na configuração  
  
1. Para o elemento [\<bindings >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) , adicione um [\<CustomBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
2. Como um elemento filho, adicione um elemento de [> de associação de\<](../../configure-apps/file-schema/wcf/bindings.md) ao elemento `<customBinding>`.  
  
3. Adicione um elemento `<security>` ao elemento `<binding>`.  
  
4. Defina o atributo `authenticationMode` como um dos valores descritos abaixo. Por exemplo, o código a seguir define o modo como `AnonymousForCertificate`.  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="SecureCustomBinding">  
         <security authenticationMode ="AnonymousForCertificate" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
#### <a name="to-set-the-mode-programmatically"></a>Para definir o modo programaticamente  
  
1. Determine o tipo de retorno, que pode ser um dos seguintes: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>ou <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
2. Chame o método estático apropriado da classe <xref:System.ServiceModel.Channels.SecurityBindingElement>. Por exemplo, o código a seguir chama o método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A>.  
  
     [!code-csharp[c_CustomBindingsAuthMode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#3)]
     [!code-vb[c_CustomBindingsAuthMode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#3)]  
  
3. Use o elemento de associação para criar a associação personalizada. Para obter mais informações, consulte [associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="mode-descriptions"></a>Descrições de modo  
  
### <a name="anonymousforcertificate"></a>AnonymousForCertificate  
 Com esse modo de autenticação, o cliente é anônimo e o serviço é autenticado usando um certificado X. 509. O elemento de associação de segurança é um <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> retornado pelo método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A>. Como alternativa, defina o atributo `authenticationMode` do elemento <`security`> como `AnonymousForCertificate`.  
  
### <a name="anonymousforsslnegotiated"></a>AnonymousForSslNegotiated  
 Com esse modo de autenticação, o cliente é anônimo e o serviço é autenticado usando um certificado X. 509 que é negociado em tempo de execução. O elemento de associação de segurança é um <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> retornado pelo método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> quando um valor de `false` é passado para o primeiro parâmetro. Como alternativa, defina o atributo `authenticationMode` como `AnonymousForSslNegotiated`.  
  
### <a name="certificateovertransport"></a>CertificateOverTransport  
 Com esse modo de autenticação, o cliente é autenticado usando um certificado X. 509 que aparece na camada SOAP como um token de suporte de endosso; ou seja, um token que assina a assinatura da mensagem. O serviço é autenticado usando um certificado X. 509 na camada de transporte. O elemento de associação de segurança é um <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> retornado pelo método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateCertificateOverTransportBindingElement%2A>. Como alternativa, defina o atributo `authenticationMode` como `CertificateOverTransport`.  
  
### <a name="issuedtoken"></a>IssuedToken  
 Com esse modo de autenticação, o cliente não se autentica no serviço, como tal; em vez disso, o cliente é autenticado em um serviço de token de segurança e recebe um token SAML, que ele apresenta ao servidor para provar seu conhecimento de uma chave compartilhada. O serviço não é autenticado para o cliente, como tal, mas o serviço de token de segurança criptografa a chave compartilhada como parte do token emitido para que apenas o serviço possa descriptografar a chave. O elemento de associação de segurança é um <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> retornado pelo método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A>. Como alternativa, defina o atributo `authenticationMode` como `IssuedToken`.  
  
### <a name="issuedtokenforcertificate"></a>IssuedTokenForCertificate  
 Com esse modo de autenticação, o cliente não se autentica no serviço, como tal; em vez disso, o cliente é autenticado em um serviço de token de segurança e recebe um token SAML, que ele apresenta ao servidor para provar seu conhecimento de uma chave compartilhada. O token emitido aparece na camada SOAP como um token de suporte de endosso ou um token de portador; ou seja, um token que assina a assinatura da mensagem. O serviço é autenticado no cliente usando um certificado X. 509. O elemento de associação de segurança é um <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> retornado pelo método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A>. Como alternativa, defina o atributo `authenticationMode` como `IssuedTokenForCertificate`.  
  
### <a name="issuedtokenforsslnegotiated"></a>IssuedTokenForSslNegotiated  
 Com esse modo de autenticação, o cliente não se autentica no serviço, como tal; em vez disso, o cliente é autenticado em um serviço de token de segurança e recebe um token SAML, que ele apresenta ao servidor para provar seu conhecimento de uma chave compartilhada. O token emitido aparece na camada SOAP como um token de suporte de endosso ou um token de portador; ou seja, um token que assina a assinatura da mensagem. O serviço é autenticado usando um certificado X. 509. O elemento de associação de segurança é um <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> retornado pelo método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A>. Como alternativa, defina o atributo `authenticationMode` como `IssuedTokenForSslnegotiated`.  
  
### <a name="issuedtokenovertransport"></a>IssuedTokenOverTransport  
 Com esse modo de autenticação, o cliente não se autentica no serviço, como tal; em vez disso, o cliente é autenticado em um serviço de token de segurança e recebe um token SAML, que ele apresenta ao servidor para provar seu conhecimento de uma chave compartilhada. O token emitido aparece na camada SOAP como um token de suporte de endosso ou um token de portador; ou seja, um token que assina a assinatura da mensagem. O serviço é autenticado usando um certificado X. 509 na camada de transporte. O elemento de associação de segurança é um `TransportSecurityBindingElement` retornado pelo método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A>. Como alternativa, defina o atributo `authenticationMode` como `IssuedTokenOverTransport`.  
  
### <a name="kerberos"></a>Kerberos  
 Com esse modo de autenticação, o cliente é autenticado no serviço usando um tíquete Kerberos. Esse mesmo tíquete também fornece autenticação de servidor. O elemento de associação de segurança é um `SymmetricSecurityBindingElement` retornado pelo método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A>. Como alternativa, defina o atributo `authenticationMode` como `Kerberos`.  
  
> [!NOTE]
> Para usar esse modo de autenticação, a conta de serviço deve ser associada a um SPN (nome da entidade de serviço). Para fazer isso, execute o serviço na conta de serviço de rede ou na conta sistema LOCAL. Como alternativa, use a ferramenta SetSpn. exe para criar um SPN para a conta de serviço. Em ambos os casos, o cliente deve usar o SPN correto no elemento [\<serviceprincipalname >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) ou usando o Construtor <xref:System.ServiceModel.EndpointAddress>. Para obter mais informações, consulte [identidade de serviço e autenticação](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
> [!NOTE]
> Quando o modo de autenticação de `Kerberos` é usado, os níveis de representação <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> e <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> não têm suporte.  
  
### <a name="kerberosovertransport"></a>KerberosOverTransport  
 Com esse modo de autenticação, o cliente é autenticado no serviço usando um tíquete Kerberos. O token Kerberos é exibido na camada SOAP como um token de suporte de endosso; ou seja, um token que assina a assinatura da mensagem. O serviço é autenticado usando um certificado X. 509 na camada de transporte. O elemento de associação de segurança é um `TransportSecurityBindingElement` retornado pelo método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosOverTransportBindingElement%2A>. Como alternativa, defina o atributo `authenticationMode` como `KerberosOverTransport`.  
  
> [!NOTE]
> Para usar esse modo de autenticação, a conta de serviço deve ser associada a um SPN. Para fazer isso, execute o serviço na conta de serviço de rede ou na conta sistema LOCAL. Como alternativa, use a ferramenta SetSpn. exe para criar um SPN para a conta de serviço. Em ambos os casos, o cliente deve usar o SPN correto no elemento [\<serviceprincipalname >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) ou usando o Construtor <xref:System.ServiceModel.EndpointAddress>. Para obter mais informações, consulte [identidade de serviço e autenticação](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
### <a name="mutualcertificate"></a>MutualCertificate  
 Com esse modo de autenticação, o cliente é autenticado usando um certificado X. 509 que aparece na camada SOAP como um token de suporte de endosso; ou seja, um token que assina a assinatura da mensagem. O serviço também é autenticado usando um certificado X. 509. O elemento de associação de segurança é um `SymmetricSecurityBindingElement` retornado pelo método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A>. Como alternativa, defina o atributo `authenticationMode` como `MutualCertificate`.  
  
### <a name="mutualcertificateduplex"></a>MutualCertificateDuplex  
 Com esse modo de autenticação, o cliente é autenticado usando um certificado X. 509 que aparece na camada SOAP como um token de suporte de endosso; ou seja, um token que assina a assinatura da mensagem. O serviço também é autenticado usando um certificado X. 509. A associação é uma `AsymmetricSecurityBindingElement` retornada pelo método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateDuplexBindingElement%2A>. Como alternativa, defina o atributo `authenticationMode` como `MutualCertificateDuplex`.  
  
### <a name="mutualsslnegotiated"></a>MutualSslNegotiated  
 Com esse modo de autenticação, o cliente e o serviço se autenticam usando certificados X. 509. O elemento de associação de segurança é um `SymmetricSecurityBindingElement` retornado pelo método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> quando um valor de `true` é passado para o primeiro parâmetro. Como alternativa, defina o atributo `authenticationMode` como `MutualSslNegotiated`.  
  
### <a name="secureconversation"></a>SecureConversation  
 O elemento de associação de segurança é um `SymmetricSecurityBindingElement` retornado pelo método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A>. Esse método usa um <xref:System.ServiceModel.Channels.SecurityBindingElement> como um parâmetro, que é usado durante a inicialização para estabelecer a sessão segura. Como alternativa, defina o atributo `authenticationMode` como `SecureConversation`.  
  
 Se nenhuma associação de inicialização for especificada, o modo de autenticação `SspiNegotiated` será usado para inicialização.  
  
### <a name="sspinegotiation"></a>SspiNegotiation  
 Com esse modo de autenticação, um protocolo de negociação é usado para executar a autenticação de cliente e servidor. O Kerberos é usado, se possível; caso contrário, o NT LanMan (NTLM) será usado. O elemento de associação de segurança é um `SymmetricSecurityBindingElement` retornado pelo método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%2A>. Como alternativa, defina o atributo `authenticationMode` como `SspiNegotiated`.  
  
### <a name="sspinegotiatedovertransport"></a>SspiNegotiatedOverTransport  
 Com esse modo de autenticação, um protocolo de negociação é usado para executar a autenticação de cliente e servidor. O protocolo Kerberos é usado, se possível; caso contrário, o NTLM será usado. O token resultante aparece na camada SOAP como um token de suporte de endosso; ou seja, um token que assina a assinatura da mensagem. O serviço também é autenticado na camada de transporte por um certificado X. 509. O elemento de associação de segurança é um `TransportSecurityBindingElement` retornado pelo método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationOverTransportBindingElement%2A>. Como alternativa, defina o atributo `authenticationMode` como `SspiNegotiatedOverTransport`.  
  
### <a name="usernameforcertificate"></a>UserNameForCertificate  
 Com esse modo de autenticação, o cliente é autenticado no serviço usando um token de nome de usuário que aparece na camada SOAP como um token de suporte assinado; ou seja, um token assinado pela assinatura da mensagem. O serviço é autenticado no cliente usando um certificado X. 509. O elemento de associação de segurança é um `SymmetricSecurityBindingElement` retornado pelo método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A>. Como alternativa, defina o atributo `authenticationMode` como `UserNameForCertificate`.  
  
 Para o modo de autenticação `UserNameForCertificate`, o cliente e o serviço devem usar o WS-Security 1,1.  
  
### <a name="usernameforsslnegotiated"></a>UserNameForSslNegotiated  
 Com esse modo de autenticação, o cliente é autenticado usando um token de nome de usuário que aparece na camada SOAP como um token de suporte assinado; ou seja, um token assinado pela assinatura da mensagem. O serviço é autenticado usando um certificado X. 509. O elemento de associação de segurança é um `SymmetricSecurityBindingElement` retornado pelo método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForSslBindingElement%2A>. Como alternativa, defina o atributo `authenticationMode` como `UserNameForSslNegotiated`.  
  
### <a name="usernameovertransport"></a>UserNameOverTransport  
 Com esse modo de autenticação, o cliente é autenticado usando um token de nome de usuário que aparece na camada SOAP como um token de suporte assinado; ou seja, um token assinado pela assinatura da mensagem. O serviço é autenticado usando um certificado X. 509 na camada de transporte. O elemento de associação de segurança é um `TransportSecurityBindingElement` retornado pelo método <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameOverTransportBindingElement%2A>. Como alternativa, defina o atributo `authenticationMode` como `UserNameOverTransport`.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- [Como criar um SecurityBindingElement para um modo de autenticação especificado](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
