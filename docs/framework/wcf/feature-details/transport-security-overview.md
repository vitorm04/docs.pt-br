---
title: Visão geral de segurança de transporte
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00959326-aa9d-44d0-af61-54933d4adc7f
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 12b491971a9f3faa57edb1ccf9fb59351ed45f3b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="transport-security-overview"></a>Visão geral de segurança de transporte
Mecanismos de segurança de transporte no Windows Communication Foundation (WCF) dependem da associação e o transporte está sendo usado. Por exemplo, ao usar o <xref:System.ServiceModel.WSHttpBinding> classe, o transporte é HTTP e o mecanismo principal para proteger o transporte é o protocolo (SSL) sobre HTTP, comumente chamado de HTTPS. Este tópico discute os mecanismos de segurança de transporte principais usados nas associações de WCF fornecido pelo sistema.  
  
> [!NOTE]
>  Quando a segurança SSL é usada com o .NET Framework 3.5 e versões posteriores um cliente WCF usa ambos os certificados intermediários em seu repositório de certificado e os certificados intermediários recebido durante a negociação SSL para executar a validação da cadeia de certificado do serviço certificado. .NET framework 3.0 usa apenas os certificados intermediários instalados no repositório de certificados local.  
  
> [!WARNING]
>  Quando a segurança de transporte é usada, o <!--zz <xref:System.Treading.Thread.CurrentPrincipal%2A> --> `CurrentPrincipal` propriedade pode ser substituída. Para impedir que isso aconteça conjunto o <!--zz <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermission%2A> --> `PrincipalPermission` como None. <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> é um comportamento de serviço que pode ser definido na descrição do serviço.  
  
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
 Isso corresponde ao método de autenticação básica no IIS. Ao usar esse modo, o servidor IIS deve ser configurado com contas de usuário do Windows e permissões do sistema de arquivos NTFS apropriadas. Para obter mais informações sobre [!INCLUDE[iis601](../../../../includes/iis601-md.md)], consulte [habilitar autenticação básica e configurar o nome de Realm](http://go.microsoft.com/fwlink/?LinkId=88592). Para obter mais informações sobre [!INCLUDE[iisver](../../../../includes/iisver-md.md)], consulte [IIS 7.0 Beta: configurar autenticação básica](http://go.microsoft.com/fwlink/?LinkId=88593).  
  
#### <a name="certificate"></a>certificado  
 O IIS tem uma opção para exigir que os clientes façam logon com um certificado. O recurso também permite que o IIS mapear um certificado de cliente para uma conta do Windows. Para obter mais informações sobre [!INCLUDE[iis601](../../../../includes/iis601-md.md)], consulte [habilitando certificados de cliente no IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=88594). Para obter mais informações sobre [!INCLUDE[iisver](../../../../includes/iisver-md.md)], consulte [IIS 7.0 Beta: Configurando certificados de servidor no IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=88595).  
  
#### <a name="digest"></a>Digest  
 A autenticação Digest é semelhante à autenticação básica, mas oferece a vantagem de enviar as credenciais como um hash, em vez de em texto não criptografado. Para obter mais informações sobre [!INCLUDE[iis601](../../../../includes/iis601-md.md)], consulte [a autenticação Digest no IIS 6.0](http://go.microsoft.com/fwlink/?LinkID=88443). Para obter mais informações sobre [!INCLUDE[iisver](../../../../includes/iisver-md.md)], consulte [IIS 7.0 Beta: configurar a autenticação Digest](http://go.microsoft.com/fwlink/?LinkId=88596).  
  
#### <a name="windows"></a>Windows  
 Isso corresponde a autenticação integrada do Windows no IIS. Quando definido como esse valor, o servidor também deve existir em um domínio do Windows que usa o protocolo Kerberos como o controlador de domínio. Se o servidor não está em um domínio Kerberos com backup, ou se o sistema Kerberos falhar, você pode usar o valor de NT LAN Manager (NTLM) descrito na próxima seção. Para obter mais informações sobre [!INCLUDE[iis601](../../../../includes/iis601-md.md)], consulte [autenticação integrada do Windows no IIS 6.0](http://go.microsoft.com/fwlink/?LinkId=88597). Para obter mais informações sobre [!INCLUDE[iisver](../../../../includes/iisver-md.md)], consulte [IIS 7.0 Beta: Configurando certificados de servidor no IIS 7.0](http://go.microsoft.com/fwlink/?LinkId=88595).  
  
#### <a name="ntlm"></a>NTLM  
 Isso permite que o servidor usam NTLM para autenticação, se o protocolo Kerberos falhar. Para obter mais informações sobre como configurar o IIS no [!INCLUDE[iis601](../../../../includes/iis601-md.md)], consulte [forçar a autenticação NTLM](http://go.microsoft.com/fwlink/?LinkId=88598). Para [!INCLUDE[iisver](../../../../includes/iisver-md.md)], a autenticação do Windows inclui a autenticação NTLM. Para obter mais informações, consulte [IIS 7.0 Beta: Configurando certificados de servidor no IIS 7.0](http://go.microsoft.com/fwlink/?LinkID=88595).  
  
## <a name="wshttpbinding"></a>WsHttpBinding  
 O <xref:System.ServiceModel.WSHttpBinding> classe destina-se a interoperação com os serviços que implementam o WS-* especificações. A segurança de transporte para essa associação é o protocolo (SSL) via HTTP ou HTTPS. Para criar um aplicativo WCF que usa o SSL, use o IIS para hospedar o aplicativo. Como alternativa, se você estiver criando um aplicativo hospedado automaticamente, use a ferramenta HttpCfg.exe para associar um certificado x. 509 a uma porta específica em um computador. O número da porta é especificado como parte do aplicativo do WCF como um endereço de ponto de extremidade. Ao usar o modo de transporte, o endereço de ponto de extremidade deve incluir o protocolo HTTPS ou uma exceção será lançada em tempo de execução. Para obter mais informações, consulte [segurança de transporte HTTP](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
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
  
 O código a seguir usa a impressão digital do certificado, que identifica com exclusividade. Para obter mais informações sobre certificados, consulte [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) (Trabalhando com certificados).  
  
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
 Ao usar a segurança de transporte, esta associação usa SSL sobre HTTP, conhecido como HTTPS com um token emitido (<xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential>). Para obter mais informações sobre aplicativos de federação, consulte [federação e Tokens emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="netpeertcpbinding"></a>NetPeerTcpBinding  
 O <xref:System.ServiceModel.NetPeerTcpBinding> classe é um transporte seguro que foi criado para uma comunicação eficiente usando o recurso de rede ponto a ponto. Conforme indicado pelo nome da classe de associação, o TCP é o protocolo. Quando o modo de segurança é definido como transporte, a associação implementa o TLS sobre TCP. Para obter mais informações sobre o recurso de ponto a ponto, consulte [rede ponto a ponto](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="msmqintegrationbinding-and-netmsmqbinding"></a>MsmqIntegrationBinding e NetMsmqBinding  
 Para uma discussão completa de transporte de segurança com o enfileiramento de mensagens (anteriormente chamado de MSMQ), consulte [proteger mensagens usando a segurança de transporte](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
## <a name="see-also"></a>Consulte também  
 [Programação de segurança do WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
