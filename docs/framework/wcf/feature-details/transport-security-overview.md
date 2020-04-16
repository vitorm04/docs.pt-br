---
title: Visão geral de segurança de transporte
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00959326-aa9d-44d0-af61-54933d4adc7f
ms.openlocfilehash: 6796ca0b16e65a07735aec075d63b0cdfe38d080
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/16/2020
ms.locfileid: "81464011"
---
# <a name="transport-security-overview"></a>Visão geral de segurança de transporte
Os mecanismos de segurança de transporte na Windows Communication Foundation (WCF) dependem da vinculação e do transporte que estão sendo utilizados. Por exemplo, ao <xref:System.ServiceModel.WSHttpBinding> usar a classe, o transporte é HTTP, e o mecanismo principal para garantir o transporte é o Secure Sockets Layer (SSL) através do HTTP, comumente chamado HTTPS. Este tópico discute os principais mecanismos de segurança de transporte utilizados nas vinculações fornecidas pelo sistema WCF.  
  
> [!NOTE]
> Quando a segurança SSL é usada com o .NET Framework 3.5 e, posteriormente, um cliente WCF usa tanto os certificados intermediários em sua loja de certificados quanto os certificados intermediários recebidos durante a negociação SSL para realizar a validação da cadeia de certificados no certificado do serviço. O .NET Framework 3.0 usa apenas os certificados intermediários instalados na loja de certificados local.  
  
> [!WARNING]
> Quando a segurança do <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> transporte é usada, a propriedade pode ser substituída. Para evitar que isso <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A?displayProperty=nameWithType> <xref:System.ServiceModel.Description.PrincipalPermissionMode.None?displayProperty=nameWithType>aconteça, defina o para . <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior>é um comportamento de serviço que pode ser definido na descrição do serviço.  
  
## <a name="basichttpbinding"></a>BasicHttpBinding  
 Por padrão, <xref:System.ServiceModel.BasicHttpBinding> a classe não fornece segurança. Esta vinculação foi projetada para interoperabilidade com provedores de serviços web que não implementam segurança. No entanto, você pode <xref:System.ServiceModel.BasicHttpSecurity.Mode%2A> ligar a segurança <xref:System.ServiceModel.BasicHttpSecurityMode.None>definindo a propriedade para qualquer valor, exceto . Para habilitar a segurança <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>do transporte, defina a propriedade como .  
  
### <a name="interoperation-with-iis"></a>Interoperação com IIS  
 A <xref:System.ServiceModel.BasicHttpBinding> classe é usada principalmente para interoperar com serviços web existentes, e muitos desses serviços são hospedados pelos Serviços de Informação da Internet (IIS). Consequentemente, a segurança de transporte para esta vinculação é projetada para uma interoperação perfeita com os sites do IIS. Isso é feito definindo <xref:System.ServiceModel.BasicHttpSecurityMode.Transport> o modo de segurança e, em seguida, definindo o tipo de credencial do cliente. Os valores do tipo de credencial correspondem aos mecanismos de segurança do diretório IIS. O código a seguir mostra o modo que está sendo definido e o tipo de credencial definido como Windows. Você pode usar essa configuração quando o cliente e o servidor estiverem no mesmo domínio do Windows.  
  
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
  
 As seções a seguir discutem outros tipos de credenciais de clientes.  
  
#### <a name="basic"></a>Basic  
 Isso corresponde ao método de autenticação básica no IIS. Ao usar este modo, o servidor IIS deve ser configurado com contas de usuário do Windows e permissões apropriadas do sistema de arquivos NTFS. Para obter mais informações sobre o IIS 6.0, consulte [Habilitar autenticação básica e configurar o nome do reino](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc785293(v=ws.10)). Para obter mais informações sobre o IIS 7.0, consulte [Configurar autenticação básica (IIS 7)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc772009(v=ws.10)).  
  
#### <a name="certificate"></a>Certificado  
 O IIS tem a opção de exigir que os clientes façam logon com um certificado. O recurso também permite que o IIS mapeie um certificado de cliente para uma conta do Windows. Para obter mais informações sobre o IIS 6.0, consulte [Habilitar certificados de cliente no IIS 6.0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc727994(v=ws.10)). Para obter mais informações sobre o IIS 7.0, consulte [Configurando certificados de servidor no IIS 7](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).  
  
#### <a name="digest"></a>Digest  
 A autenticação digesta é semelhante à autenticação Básica, mas oferece a vantagem de enviar as credenciais como um hash, em vez de em texto claro. Para obter mais informações sobre o IIS 6.0, consulte [Digest Authentication no IIS 6.0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc782661(v=ws.10)). Para obter mais informações sobre o IIS 7.0, consulte [Configure Digest Authentication (IIS 7)](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc754104(v=ws.10)).  
  
#### <a name="windows"></a>Windows  
 Isso corresponde à autenticação integrada do Windows no IIS. Quando definido para esse valor, espera-se que o servidor também exista em um domínio do Windows que usa o protocolo Kerberos como seu controlador de domínio. Se o servidor não estiver em um domínio apoiado pelo Kerberos ou se o sistema Kerberos falhar, você poderá usar o valor NT LAN Manager (NTLM) descrito na próxima seção. Para obter mais informações sobre o IIS 6.0, consulte [Autenticação integrada do Windows no IIS 6.0](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc738016(v=ws.10)). Para obter mais informações sobre o IIS 7.0, consulte [Configurando certificados de servidor no IIS 7](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).
  
#### <a name="ntlm"></a>NTLM  
 Isso permite que o servidor use NTLM para autenticação se o protocolo Kerberos falhar. Para obter mais informações sobre a configuração do IIS no IIS 6.0, consulte [Forçando a Autenticação NTLM](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2003/cc786486(v=ws.10)). Para o IIS 7.0, a autenticação do Windows inclui autenticação NTLM. Para obter mais informações, consulte [Configurando certificados de servidor no IIS 7](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc732230(v=ws.10)).
  
## <a name="wshttpbinding"></a>WshttpBinding  
 A <xref:System.ServiceModel.WSHttpBinding> classe foi projetada para interoperação com serviços que implementam especificações WS-*. A segurança de transporte para essa vinculação é Secure Sockets Layer (SSL) em HTTP ou HTTPS. Para criar um aplicativo WCF que usa SSL, use o IIS para hospedar o aplicativo. Alternativamente, se você estiver criando um aplicativo auto-hospedado, use a ferramenta HttpCfg.exe para vincular um certificado X.509 a uma porta específica em um computador. O número da porta é especificado como parte do aplicativo WCF como um endereço de ponto final. Ao usar o modo de transporte, o endereço de ponto final deve incluir o protocolo HTTPS ou uma exceção será lançada no tempo de execução. Para obter mais informações, consulte [HTTP Transport Security](../../../../docs/framework/wcf/feature-details/http-transport-security.md).  
  
 Para autenticação do <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> cliente, <xref:System.ServiceModel.HttpTransportSecurity> defina a <xref:System.ServiceModel.HttpClientCredentialType> propriedade da classe como um dos valores de enumeração. Os valores de enumeração são idênticos <xref:System.ServiceModel.BasicHttpBinding> aos tipos de credenciais do cliente e foram projetados para serem hospedados com serviços iIS.  
  
 O exemplo a seguir mostra a vinculação sendo usada com um tipo de credencial do cliente do Windows.  
  
 [!code-csharp[c_ProgrammingSecurity#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#11)]
 [!code-vb[c_ProgrammingSecurity#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#11)]  
  
## <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 Essa vinculação fornece apenas segurança em nível de mensagem, não segurança em nível de transporte.  
  
## <a name="nettcpbinding"></a>NetTcpBinding  
 A <xref:System.ServiceModel.NetTcpBinding> classe usa TCP para transporte de mensagens. A segurança para o modo de transporte é fornecida implementando TLS (Transport Layer Security, segurança de camada de transporte) sobre TCP. A implementação do TLS é fornecida pelo sistema operacional.  
  
 Você também pode especificar o tipo de <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> credencial <xref:System.ServiceModel.TcpTransportSecurity> do cliente definindo a propriedade da classe como um dos <xref:System.ServiceModel.TcpClientCredentialType> valores, conforme mostrado no código a seguir.  
  
 [!code-csharp[c_ProgrammingSecurity#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#12)]
 [!code-vb[c_ProgrammingSecurity#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#12)]  
  
#### <a name="client"></a>Cliente  
 No cliente, você deve especificar <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> um <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> certificado usando o método da classe.  
  
> [!NOTE]
> Se você estiver usando a segurança do Windows, um certificado não é necessário.  
  
 O código a seguir usa a impressão digital do certificado, que o identifica exclusivamente. Para obter mais informações sobre certificados, consulte [Working with Certificates](../../../../docs/framework/wcf/feature-details/working-with-certificates.md) (Trabalhando com certificados).  
  
 [!code-csharp[c_ProgrammingSecurity#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#13)]
 [!code-vb[c_ProgrammingSecurity#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#13)]  
  
 Alternativamente, especifique o certificado na [ \<](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) configuração do cliente usando um elemento de>de credenciais do cliente na seção comportamentos.  
  
```xml  
<behaviors>  
  <behavior>  
   <clientCredentials>  
     <clientCertificate findValue= "101010101010101010101010101010000000000"
      storeLocation="LocalMachine" storeName="My"
      X509FindType="FindByThumbPrint">  
     </clientCertificate>  
   </clientCredentials>  
 </behavior>  
</behaviors>
```  
  
## <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 A <xref:System.ServiceModel.NetNamedPipeBinding> classe foi projetada para uma comunicação intra-máquina eficiente; ou seja, para processos em execução no mesmo computador, embora canais de tubulação nomeados possam ser criados entre dois computadores na mesma rede. Esta vinculação fornece apenas segurança em nível de transporte. Ao criar aplicativos usando essa vinculação, os endereços de ponto final devem incluir "net.pipe" como o protocolo do endereço de ponto final.  
  
## <a name="wsfederationhttpbinding"></a>WSFederationhttpbinding  
 Ao usar a segurança de transporte, essa vinculação usa SSL<xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential>através de HTTP, conhecido como HTTPS com um token emitido ( ). Para obter mais informações sobre os aplicativos da federação, consulte [Federação e Tokens Emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).  
  
## <a name="netpeertcpbinding"></a>NetPeerTcpBinding  
 A <xref:System.ServiceModel.NetPeerTcpBinding> classe é um transporte seguro que foi projetado para uma comunicação eficiente usando o recurso de rede ponto a ponto. Como indicado pelo nome da classe e vinculação, TCP é o protocolo. Quando o modo de segurança é definido como Transporte, a vinculação implementa TLS sobre TCP. Para obter mais informações sobre o recurso peer-to-peer, consulte [Rede peer-to-peer](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
## <a name="msmqintegrationbinding-and-netmsmqbinding"></a>MsmqIntegrationBinding and NetMsmqBinding  
 Para uma discussão completa sobre segurança de transporte com fila de mensagens (anteriormente chamada de MSMQ), consulte [Protegendo mensagens usando segurança de transporte](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md).  
  
## <a name="see-also"></a>Confira também

- [Programação de segurança do WCF](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
