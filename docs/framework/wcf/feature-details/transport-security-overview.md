---
title: "Visão geral de segurança de transporte"
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
ms.assetid: 00959326-aa9d-44d0-af61-54933d4adc7f
caps.latest.revision: "23"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 71325089f2c72f6f01b2179bd150d21a98b3a8e2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="transport-security-overview"></a>Visão geral de segurança de transporte
Transporte de mecanismos de segurança em [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] dependem de associação e transporte que está sendo usado. Por exemplo, ao usar o <xref:System.ServiceModel.WSHttpBinding> classe, o transporte é HTTP e o mecanismo principal para proteger o transporte é o protocolo (SSL) sobre HTTP, comumente chamado de HTTPS. Este tópico discute os mecanismos de segurança de transporte principal usados no [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] associações fornecidas pelo sistema.  
  
> [!NOTE]
>  Quando a segurança SSL é usada com o .NET Framework 3.5 e versões posteriores um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] cliente usa tanto os certificados intermediários em seu repositório de certificado e os certificados intermediários recebidos durante a negociação SSL para executar a validação da cadeia de certificado na certificado do serviço. .NET framework 3.0 usa apenas os certificados intermediários instalados no repositório de certificados local.  
  
> [!WARNING]
>  Quando a segurança de transporte é usada, o <!--zz <xref:System.Treading.Thread.CurrentPrincipal%2A> --> `CurrentPrincipal` propriedade pode ser substituída. Para impedir que isso aconteça conjunto o <!--zz <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermission%2A> --> `PrincipalPermission` como None. <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>é um comportamento de serviço que pode ser definido na descrição do serviço.  
  
## <a name="basichttpbinding"></a>BasicHttpBinding  
 Por padrão, o <xref:System.ServiceModel.BasicHttpBinding> classe não oferece segurança. Essa associação destina-se para interoperabilidade com provedores de serviço Web que não implementam a segurança. No entanto, você pode alternar segurança definindo o <xref:System.ServiceModel.BasicHttpSecurity.Mode%2A> propriedade para qualquer valor exceto <xref:System.ServiceModel.BasicHttpSecurityMode.None>. Para habilitar a segurança de transporte, defina a propriedade como <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>.  
  
### <a name="interoperation-with-iis"></a>Interoperação com o IIS  
 O <xref:System.ServiceModel.BasicHttpBinding> classe é usada principalmente para interoperar com serviços da Web existentes e muitos desses serviços hospedados pelo Internet Information Services (IIS). Consequentemente, a segurança de transporte para esta associação se destina a interoperação perfeita com sites do IIS. Isso é feito definindo o modo de segurança <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> e, em seguida, definindo o cliente do tipo de credencial. Os valores de tipo de credencial correspondem aos mecanismos de segurança de diretório do IIS. O código a seguir mostra o definição do modo e o tipo de credencial definida como Windows. Você pode usar essa configuração quando o cliente e o servidor estão no mesmo domínio do Windows.  
  
 [!code-csharp[c_ProgrammingSecurity#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#10)] 
 [!code-vb[c_ProgrammingSecurity#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#10)]  
  
 Ou, na configuração:  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <binding name="SecurityByTransport">  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" />  
       </security>  
     </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 As seções a seguir discutem os outros tipos de credencial de cliente.  
  
#### <a name="basic"></a>Basic  
 Isso corresponde ao método de autenticação básica no IIS. Ao usar esse modo, o servidor IIS deve ser configurado com contas de usuário do Windows e permissões do sistema de arquivos NTFS apropriadas. [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iis601](../../../../includes/iis601-md.md)], consulte [habilitar autenticação básica e configurar o nome de Realm](http://go.microsoft.com/fwlink/?LinkId=88592). [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iisver](../../../../includes/iisver-md.md)], consulte [IIS 7.0 Beta: configurar autenticação básica](http://go.microsoft.com/fwlink/?LinkId=88593).  
  
#### <a name="certificate"></a>certificado  
 O IIS tem uma opção para exigir que os clientes façam logon com um certificado. O recurso também permite que o IIS mapear um certificado de cliente para uma conta do Windows. [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iis601](../../../../includes/iis601-md.md)], consulte [habilitando certificados de cliente no IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=88594). [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iisver](../../../../includes/iisver-md.md)], consulte [IIS 7.0 Beta: Configurando certificados de servidor no IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=88595).  
  
#### <a name="digest"></a>Digest  
 A autenticação Digest é semelhante à autenticação básica, mas oferece a vantagem de enviar as credenciais como um hash, em vez de em texto não criptografado. [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iis601](../../../../includes/iis601-md.md)], consulte [a autenticação Digest no IIS 6.0](http://go.microsoft.com/fwlink/?LinkID=88443). [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iisver](../../../../includes/iisver-md.md)], consulte [IIS 7.0 Beta: configurar a autenticação Digest](http://go.microsoft.com/fwlink/?LinkId=88596).  
  
#### <a name="windows"></a>Windows  
 Isso corresponde a autenticação integrada do Windows no IIS. Quando definido como esse valor, o servidor também deve existir em um domínio do Windows que usa o protocolo Kerberos como o controlador de domínio. Se o servidor não está em um domínio Kerberos com backup, ou se o sistema Kerberos falhar, você pode usar o valor de NT LAN Manager (NTLM) descrito na próxima seção. [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iis601](../../../../includes/iis601-md.md)], consulte [autenticação integrada do Windows no IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=88597). [!INCLUDE[crabout](../../../../includes/crabout-md.md)][!INCLUDE[iisver](../../../../includes/iisver-md.md)], consulte [IIS 7.0 Beta: Configurando certificados de servidor no IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=88595).  
  
#### <a name="ntlm"></a>NTLM  
 Isso permite que o servidor usam NTLM para autenticação, se o protocolo Kerberos falhar. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Configurando o IIS em [!INCLUDE[iis601](../../../../includes/iis601-md.md)], consulte [forçar a autenticação NTLM](http://go.microsoft.com/fwlink/?LinkId=88598). Para [!INCLUDE[iisver](../../../../includes/iisver-md.md)], a autenticação do Windows inclui a autenticação NTLM. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][IIS 7.0 Beta: Configurando certificados de servidor no IIS 7.0](http://go.microsoft.com/fwlink/?LinkID=88595).  
  
## <a name="wshttpbinding"></a>WsHttpBinding  
 O <xref:System.ServiceModel.WSHttpBinding> classe destina-se a interoperação com os serviços que implementam o WS-* especificações. A segurança de transporte para essa associação é o protocolo (SSL) via HTTP ou HTTPS. Para criar um [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo que usa o SSL, use o IIS para hospedar o aplicativo. Como alternativa, se você estiver criando um aplicativo hospedado automaticamente, use a ferramenta HttpCfg.exe para associar um certificado x. 509 a uma porta específica em um computador. O número da porta é especificado como parte do [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativo como um endereço de ponto de extremidade. Ao usar o modo de transporte, o endereço de ponto de extremidade deve incluir o protocolo HTTPS ou uma exceção será lançada em tempo de execução. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][Segurança de transporte HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Para autenticação de cliente, defina o <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> propriedade o <xref:System.ServiceModel.HttpTransportSecurity> classe para um do <xref:System.ServiceModel.HttpClientCredentialType> valores de enumeração. Os valores de enumeração são idênticos para os tipos de credencial de cliente para <xref:System.ServiceModel.BasicHttpBinding> e são projetados para ser hospedado com os serviços do IIS.  
  
 O exemplo a seguir mostra a associação está sendo usada com um tipo de credencial de cliente do Windows.  
  
 [!code-csharp[c_ProgrammingSecurity#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#11)]
 [!code-vb[c_ProgrammingSecurity#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#11)]  
  
## <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 Essa associação fornece segurança em nível de mensagem somente, segurança de nível de transporte não.  
  
## <a name="nettcpbinding"></a>NetTcpBinding  
 O <xref:System.ServiceModel.NetTcpBinding> classe usa o TCP para o transporte de mensagens. Segurança para o modo de transporte é fornecida com a implementação de segurança de camada de transporte (TLS) sobre TCP. A implementação de TLS é fornecida pelo sistema operacional.  
  
 Você também pode especificar o tipo de credencial do cliente, definindo a <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> propriedade o <xref:System.ServiceModel.TcpTransportSecurity> classe para um do <xref:System.ServiceModel.TcpClientCredentialType> valores, conforme mostrado no código a seguir.  
  
 [!code-csharp[c_ProgrammingSecurity#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#12)]
 [!code-vb[c_ProgrammingSecurity#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#12)]  
  
#### <a name="client"></a>Cliente  
 No cliente, você deve especificar um certificado usando o <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> método o <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> classe.  
  
> [!NOTE]
>  Se você estiver usando a segurança do Windows, um certificado não é necessário.  
  
 O código a seguir usa a impressão digital do certificado, que identifica com exclusividade. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]certificados, consulte [trabalhar com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md).  
  
 [!code-csharp[c_ProgrammingSecurity#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#13)]
 [!code-vb[c_ProgrammingSecurity#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#13)]  
  
 Como alternativa, especifique o certificado na configuração do cliente usando um [ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) elemento na seção de comportamentos.  
  
```xml  
<behaviors>  
  <behavior>  
   <clientCredentials>  
     <clientCertificate findValue= "101010101010101010101010101010000000000"   
      storeLocation="LocalMachine" storeName="My"   
      X509FindType="FindByThumbPrint"/>  
     </clientCertificate>  
   </clientCredentials>  
 </behavior>  
</behaviors>    
```  
  
## <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 O <xref:System.ServiceModel.NetNamedPipeBinding> foi criado para uma comunicação eficiente entre computadores; ou seja, para processos em execução no mesmo computador, embora denominado canais do pipe pode ser criado entre dois computadores na mesma rede. Essa associação fornece somente segurança em nível de transporte. Ao criar aplicativos que usam essa associação, os endereços de ponto de extremidade devem incluir o "pipe" como o protocolo do endereço do ponto de extremidade.  
  
## <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 Ao usar a segurança de transporte, esta associação usa SSL sobre HTTP, conhecido como HTTPS com um token emitido (<xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential>). [!INCLUDE[crabout](../../../../includes/crabout-md.md)]aplicativos de federação, consulte [federação e Tokens emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="netpeertcpbinding"></a>NetPeerTcpBinding  
 O <xref:System.ServiceModel.NetPeerTcpBinding> classe é um transporte seguro que foi criado para uma comunicação eficiente usando o recurso de rede ponto a ponto. Conforme indicado pelo nome da classe de associação, o TCP é o protocolo. Quando o modo de segurança é definido como transporte, a associação implementa o TLS sobre TCP. [!INCLUDE[crabout](../../../../includes/crabout-md.md)]o recurso de ponto a ponto, consulte [rede ponto a ponto](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="msmqintegrationbinding-and-netmsmqbinding"></a>MsmqIntegrationBinding e NetMsmqBinding  
 Para uma discussão completa de transporte de segurança com o enfileiramento de mensagens (anteriormente chamado de MSMQ), consulte [proteger mensagens usando a segurança de transporte](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
## <a name="see-also"></a>Consulte também  
 [Programação de segurança do WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
