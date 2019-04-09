---
title: SecurityBindingElement Authentication Modes
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 12300bf4-c730-4405-9f65-d286f68b5a43
ms.openlocfilehash: 9c8b2cb0417db6481ce0171d85b225ef3a784c1b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59119750"
---
# <a name="securitybindingelement-authentication-modes"></a>SecurityBindingElement Authentication Modes
Windows Communication Foundation (WCF) fornece vários modos pelos quais os clientes e serviços autenticam um ao outro. Você pode criar elementos de associação para esses modos de autenticação de segurança por meio de métodos estáticos no <xref:System.ServiceModel.Channels.SecurityBindingElement> classe ou por meio da configuração. Este tópico descreve resumidamente os modos de 18 autenticação.  
  
 Para obter um exemplo de como usar o elemento para um dos modos de autenticação, consulte [como: Criar um SecurityBindingElement para um modo de autenticação especificado](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md).  
  
## <a name="basic-configuration-programming"></a>Configuração básica de programação  
 O procedimento a seguir descreve como definir o modo de autenticação em um arquivo de configuração.  
  
#### <a name="to-set-the-authentication-mode-in-configuration"></a>Para definir o modo de autenticação na configuração  
  
1.  Para o [ \<associações >](../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md) elemento, adicionar um [ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).  
  
2.  Como um elemento filho, adicione uma [ \<associação >](../../../../docs/framework/misc/binding.md) elemento para o `<customBinding>` elemento.  
  
3.  Adicionar um `<security>` elemento para o `<binding>` elemento.  
  
4.  Defina o `authenticationMode` de atributo para um dos valores descritos a seguir. Por exemplo, o código a seguir define o modo como `AnonymousForCertificate`.  
  
    ```xml  
    <bindings>  
      <customBinding>  
        <binding name="SecureCustomBinding">  
         <security authenticationMode ="AnonymousForCertificate" />  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
#### <a name="to-set-the-mode-programmatically"></a>Para definir o modo de forma programática  
  
1.  Determinar o tipo de retorno, que pode ser um dos seguintes: <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement>, <xref:System.ServiceModel.Channels.TransportSecurityBindingElement>, <xref:System.ServiceModel.Channels.AsymmetricSecurityBindingElement>, ou <xref:System.ServiceModel.Channels.SecurityBindingElement>.  
  
2.  Chame o método estático apropriado do <xref:System.ServiceModel.Channels.SecurityBindingElement> classe. Por exemplo, o código a seguir chama o <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A> método.  
  
     [!code-csharp[c_CustomBindingsAuthMode#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_custombindingsauthmode/cs/source.cs#3)]
     [!code-vb[c_CustomBindingsAuthMode#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_custombindingsauthmode/vb/source.vb#3)]  
  
3.  Use o elemento de associação para criar a associação personalizada. Para obter mais informações, consulte [ligações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
## <a name="mode-descriptions"></a>Descrições de modo  
  
### <a name="anonymousforcertificate"></a>AnonymousForCertificate  
 Com esse modo de autenticação, o cliente é anônimo e o serviço é autenticado usando um certificado X.509. O elemento de associação de segurança é uma <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> retornado pelo <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateAnonymousForCertificateBindingElement%2A> método. Como alternativa, defina as `authenticationMode` atributo da <`security`> elemento a ser `AnonymousForCertificate`.  
  
### <a name="anonymousforsslnegotiated"></a>AnonymousForSslNegotiated  
 Com esse modo de autenticação, o cliente é anônimo e o serviço é autenticado usando um certificado X.509 que é negociado em tempo de execução. O elemento de associação de segurança é uma <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> retornado pela <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> método quando um valor de `false` é passado para o primeiro parâmetro. Como alternativa, defina as `authenticationMode` atributo `AnonymousForSslNegotiated`.  
  
### <a name="certificateovertransport"></a>CertificateOverTransport  
 Com esse modo de autenticação, o cliente é autenticado usando um certificado X.509 que é exibido na camada de SOAP como um token de suporte de endosso; ou seja, um token que entra a assinatura da mensagem. O serviço é autenticado usando um certificado X.509 na camada de transporte. O elemento de associação de segurança é uma <xref:System.ServiceModel.Channels.TransportSecurityBindingElement> retornado pelo <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateCertificateOverTransportBindingElement%2A> método. Como alternativa, defina as `authenticationMode` atributo `CertificateOverTransport`.  
  
### <a name="issuedtoken"></a>IssuedToken  
 Com esse modo de autenticação, o cliente não autentica para o serviço, como tal; em vez disso, o cliente se autentica em um serviço de token de segurança e recebe um token SAML, que ele então apresenta ao servidor para provar seu conhecimento de uma chave compartilhada. O serviço não está autenticado para o cliente, como tal, mas o serviço de token de segurança criptografa a chave compartilhada como parte do token emitido para que apenas o serviço possa descriptografar a chave. O elemento de associação de segurança é uma <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> retornado pelo <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenBindingElement%2A> método. Como alternativa, defina as `authenticationMode` atributo `IssuedToken`.  
  
### <a name="issuedtokenforcertificate"></a>IssuedTokenForCertificate  
 Com esse modo de autenticação, o cliente não autentica para o serviço, como tal; em vez disso, o cliente se autentica em um serviço de token de segurança e recebe um token SAML, que ele então apresenta ao servidor para provar seu conhecimento de uma chave compartilhada. O token emitido é exibido na camada de SOAP como um token de suporte de endosso ou token de portador; ou seja, um token que entra a assinatura da mensagem. O serviço autentica para o cliente usando um certificado X.509. O elemento de associação de segurança é uma <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> retornado pelo <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForCertificateBindingElement%2A> método. Como alternativa, defina as `authenticationMode` atributo `IssuedTokenForCertificate`.  
  
### <a name="issuedtokenforsslnegotiated"></a>IssuedTokenForSslNegotiated  
 Com esse modo de autenticação, o cliente não autentica para o serviço, como tal; em vez disso, o cliente se autentica em um serviço de token de segurança e recebe um token SAML, que ele então apresenta ao servidor para provar seu conhecimento de uma chave compartilhada. O token emitido é exibido na camada de SOAP como um token de suporte de endosso ou token de portador; ou seja, um token que entra a assinatura da mensagem. O serviço é autenticado usando um certificado X.509. O elemento de associação de segurança é uma <xref:System.ServiceModel.Channels.SymmetricSecurityBindingElement> retornado pelo <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenForSslBindingElement%2A> método. Como alternativa, defina as `authenticationMode` atributo `IssuedTokenForSslnegotiated`.  
  
### <a name="issuedtokenovertransport"></a>IssuedTokenOverTransport  
 Com esse modo de autenticação, o cliente não autentica para o serviço, como tal; em vez disso, o cliente se autentica em um serviço de token de segurança e recebe um token SAML, que ele então apresenta ao servidor para provar seu conhecimento de uma chave compartilhada. O token emitido é exibido na camada de SOAP como um token de suporte de endosso ou token de portador; ou seja, um token que entra a assinatura da mensagem. O serviço é autenticado usando um certificado X.509 na camada de transporte. O elemento de associação de segurança é uma `TransportSecurityBindingElement` retornado pelo <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateIssuedTokenOverTransportBindingElement%2A> método. Como alternativa, defina as `authenticationMode` atributo `IssuedTokenOverTransport`.  
  
### <a name="kerberos"></a>Kerberos  
 Com esse modo de autenticação, o cliente é autenticado para o serviço usando um tíquete Kerberos. Esse tíquete mesmo também fornece autenticação de servidor. O elemento de associação de segurança é uma `SymmetricSecurityBindingElement` retornado pelo <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosBindingElement%2A> método. Como alternativa, defina as `authenticationMode` atributo `Kerberos`.  
  
> [!NOTE]
>  Para usar esse modo de autenticação, a conta de serviço deve estar associada com um nome de entidade de serviço (SPN). Para fazer isso, execute o serviço sob a conta de serviço de rede ou a conta sistema LOCAL. Como alternativa, use a ferramenta SetSpn.exe para criar um SPN para a conta de serviço. Em ambos os casos, o cliente deve usar o SPN correto na [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) elemento, ou usando o <xref:System.ServiceModel.EndpointAddress> construtor. Para obter mais informações, consulte [identidade de serviço e autenticação](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
> [!NOTE]
>  Quando o `Kerberos` modo de autenticação é usado, o <xref:System.Security.Principal.TokenImpersonationLevel.Anonymous> e <xref:System.Security.Principal.TokenImpersonationLevel.Delegation> não há suporte para níveis de representação.  
  
### <a name="kerberosovertransport"></a>KerberosOverTransport  
 Com esse modo de autenticação, o cliente é autenticado para o serviço usando um tíquete Kerberos. O token Kerberos é exibido na camada de SOAP como um token de suporte de endosso; ou seja, um token que entra a assinatura da mensagem. O serviço é autenticado usando um certificado X.509 na camada de transporte. O elemento de associação de segurança é uma `TransportSecurityBindingElement` retornado pelo <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateKerberosOverTransportBindingElement%2A> método. Como alternativa, defina as `authenticationMode` atributo `KerberosOverTransport`.  
  
> [!NOTE]
>  Para usar esse modo de autenticação, a conta de serviço deve ser associada um SPN. Para fazer isso, execute o serviço sob a conta de serviço de rede ou a conta sistema LOCAL. Como alternativa, use a ferramenta SetSpn.exe para criar um SPN para a conta de serviço. Em ambos os casos, o cliente deve usar o SPN correto na [ \<servicePrincipalName >](../../../../docs/framework/configure-apps/file-schema/wcf/serviceprincipalname.md) elemento, ou usando o <xref:System.ServiceModel.EndpointAddress> construtor. Para obter mais informações, consulte [identidade de serviço e autenticação](../../../../docs/framework/wcf/feature-details/service-identity-and-authentication.md).  
  
### <a name="mutualcertificate"></a>MutualCertificate  
 Com esse modo de autenticação, o cliente é autenticado usando um certificado X.509 que é exibido na camada de SOAP como um token de suporte de endosso; ou seja, um token que entra a assinatura da mensagem. O serviço também é autenticado usando um certificado X.509. O elemento de associação de segurança é uma `SymmetricSecurityBindingElement` retornado pelo <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateBindingElement%2A> método. Como alternativa, defina as `authenticationMode` atributo `MutualCertificate`.  
  
### <a name="mutualcertificateduplex"></a>MutualCertificateDuplex  
 Com esse modo de autenticação, o cliente é autenticado usando um certificado X.509 que é exibido na camada de SOAP como um token de suporte de endosso; ou seja, um token que entra a assinatura da mensagem. O serviço também é autenticado usando um certificado X.509. A associação é uma `AsymmetricSecurityBindingElement` retornado pelo <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateMutualCertificateDuplexBindingElement%2A> método. Como alternativa, defina as `authenticationMode` atributo `MutualCertificateDuplex`.  
  
### <a name="mutualsslnegotiated"></a>MutualSslNegotiated  
 Com esse modo de autenticação, o cliente e o serviço se autenticar usando certificados x. 509. O elemento de associação de segurança é uma `SymmetricSecurityBindingElement` retornado pela <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSslNegotiationBindingElement%2A> método quando um valor de `true` é passado para o primeiro parâmetro. Como alternativa, defina as `authenticationMode` atributo `MutualSslNegotiated`.  
  
### <a name="secureconversation"></a>SecureConversation  
 O elemento de associação de segurança é uma `SymmetricSecurityBindingElement` retornado pelo <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSecureConversationBindingElement%2A> método. Esse método usa um <xref:System.ServiceModel.Channels.SecurityBindingElement> como um parâmetro, que é usado durante a inicialização para estabelecer a sessão segura. Como alternativa, defina as `authenticationMode` atributo `SecureConversation`.  
  
 Se nenhuma associação de inicialização for especificada, o `SspiNegotiated` modo de autenticação é usado para o bootstrap.  
  
### <a name="sspinegotiation"></a>SspiNegotiation  
 Com esse modo de autenticação, um protocolo de negociação é usado para realizar a autenticação de cliente e servidor. Kerberos é usado, se possível; Caso contrário, o NT LanMan (NTLM) é usado. O elemento de associação de segurança é uma `SymmetricSecurityBindingElement` retornado pelo <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationBindingElement%2A> método. Como alternativa, defina as `authenticationMode` atributo `SspiNegotiated`.  
  
### <a name="sspinegotiatedovertransport"></a>SspiNegotiatedOverTransport  
 Com esse modo de autenticação, um protocolo de negociação é usado para realizar a autenticação de cliente e servidor. Protocolo Kerberos é usado, se possível; Caso contrário, o NTLM é usado. O token resultante é exibido na camada de SOAP como um token de suporte de endosso; ou seja, um token que entra a assinatura da mensagem. Além disso, o serviço é autenticado na camada de transporte por um certificado X.509. O elemento de associação de segurança é uma `TransportSecurityBindingElement` retornado pelo <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateSspiNegotiationOverTransportBindingElement%2A> método. Como alternativa, defina as `authenticationMode` atributo `SspiNegotiatedOverTransport`.  
  
### <a name="usernameforcertificate"></a>UserNameForCertificate  
 Com esse modo de autenticação, o cliente é autenticado para o serviço usando um Token de nome de usuário que aparece na camada de SOAP como um token de suporte assinado; ou seja, um token que é assinado pela assinatura da mensagem. O serviço autentica para o cliente usando um certificado X.509. O elemento de associação de segurança é uma `SymmetricSecurityBindingElement` retornado pelo <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForCertificateBindingElement%2A> método. Como alternativa, defina as `authenticationMode` atributo `UserNameForCertificate`.  
  
 Para o `UserNameForCertificate` deve estar usando o modo de autenticação, o cliente e o serviço WS-Security 1.1.  
  
### <a name="usernameforsslnegotiated"></a>UserNameForSslNegotiated  
 Com esse modo de autenticação, é o cliente é autenticado usando um Token de nome de usuário que aparece na camada de SOAP como um token de suporte assinado; ou seja, um token que é assinado pela assinatura da mensagem. O serviço é autenticado usando um certificado X.509. O elemento de associação de segurança é uma `SymmetricSecurityBindingElement` retornado pelo <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameForSslBindingElement%2A> método. Como alternativa, defina as `authenticationMode` atributo `UserNameForSslNegotiated`.  
  
### <a name="usernameovertransport"></a>UserNameOverTransport  
 Com esse modo de autenticação, o cliente é autenticado usando um Token de nome de usuário que aparece na camada de SOAP como um token de suporte assinado; ou seja, um token que é assinado pela assinatura da mensagem. O serviço é autenticado usando um certificado X.509 na camada de transporte. O elemento de associação de segurança é uma `TransportSecurityBindingElement` retornado pelo <xref:System.ServiceModel.Channels.SecurityBindingElement.CreateUserNameOverTransportBindingElement%2A> método. Como alternativa, defina as `authenticationMode` atributo `UserNameOverTransport`.  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.SecurityBindingElement>
- [Como: criar um SecurityBindingElement para um modo de autenticação especificado](../../../../docs/framework/wcf/feature-details/how-to-create-a-securitybindingelement-for-a-specified-authentication-mode.md)
