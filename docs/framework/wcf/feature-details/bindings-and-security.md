---
title: Associações e segurança
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], security
- WCF security
- Windows Communication Foundation, security
- bindings [WCF]
ms.assetid: 4de03dd3-968a-4e65-af43-516e903d7f95
ms.openlocfilehash: 5e3a8bc58d0828f50feb7752eb438d41695460fa
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857786"
---
# <a name="bindings-and-security"></a>Associações e segurança
As associações fornecidas pelo sistema incluídas com o Windows Communication Foundation (WCF) oferecem uma maneira rápida de aplicativos do WCF de programa. Com uma exceção, todas as associações têm um esquema de segurança padrão habilitado. Este tópico ajuda você a selecionar a associação certa para suas necessidades de segurança.  
  
 Para obter uma visão geral da segurança do WCF, consulte [visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md). Para obter mais informações sobre programação do WCF usando associações, consulte [Programming WCF Security](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md).  
  
 Se você já tiver selecionado uma associação, você pode encontrar mais informações sobre os comportamentos de tempo de execução que estão associados com segurança no [comportamentos de segurança](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md).  
  
 Algumas funções de segurança não são programáveis usando as associações fornecidas pelo sistema. Para obter mais controle utilizando uma associação personalizada, consulte [recursos de segurança com associações personalizadas](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).  
  
## <a name="security-functions-of-bindings"></a>Funções de segurança de associações  
 O WCF inclui um número de associações fornecidas pelo sistema que atendem a maioria das necessidades. Se não ser suficiente uma ligação específica, você também pode criar uma associação personalizada. Para obter uma lista das associações fornecidas pelo sistema, consulte [System-Provided associações](../../../../docs/framework/wcf/system-provided-bindings.md). Para obter mais informações sobre ligações personalizadas, consulte [ligações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
 Todas as associações do WCF tem duas formas: como uma API e como um elemento XML usado em um arquivo de configuração. Por exemplo, o `WSHttpBinding` (API) tem um equivalente em de [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 A seção a seguir lista as duas formas para cada associação e resume os recursos de segurança.  
  
### <a name="basichttp"></a>BasicHttp  
 No código, use o <xref:System.ServiceModel.BasicHttpBinding> classe; na configuração, use o [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).  
  
 Essa associação é projetada para uso com uma variedade de tecnologias existentes, incluindo o seguinte:  
  
- Serviços Web do ASP.NET (ASMX), versão 1.  
  
- Aplicativos do Web Service Enhancements (WSE).  
  
- Basic perfil conforme definido na interoperabilidade de serviços da Web (WS-I) especificação (<https://go.microsoft.com/fwlink/?LinkId=38955>).  
  
- Perfil de segurança básica, conforme definido em WS-I.  
  
 Por padrão, essa associação não é segura. Ele é projetado para interoperar com serviços ASMX. Quando a segurança é habilitada, a associação foi projetada para interoperação perfeita com mecanismos de segurança do Internet Information Services (IIS), como autenticação básica, digest e segurança integrada do Windows. Para obter mais informações, consulte [visão geral da segurança de transporte](../../../../docs/framework/wcf/feature-details/transport-security-overview.md). Essa associação dá suporte a:  
  
- Segurança de transporte HTTPS.  
  
- Autenticação HTTP básica.  
  
- WS-Security.  
  
 Para obter mais informações, consulte <xref:System.ServiceModel.BasicHttpSecurity>, <xref:System.ServiceModel.BasicHttpMessageSecurity>, <xref:System.ServiceModel.BasicHttpMessageCredentialType> e <xref:System.ServiceModel.BasicHttpSecurityMode>.  
  
### <a name="wshttpbinding"></a>WSHttpBinding  
 No código, use o <xref:System.ServiceModel.WSHttpBinding> classe; na configuração, use o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 Por padrão, essa associação implementa a especificação WS-Security e permite a interoperabilidade com serviços que implementam o WS-* especificações. Ele oferece suporte a seguir:  
  
- Segurança de transporte HTTPS.  
  
- WS-Security.  
  
- Proteção de transporte com segurança de credencial de mensagem SOAP para autenticar o chamador de HTTPS.  
  
 Para obter mais informações, consulte <xref:System.ServiceModel.WSHttpSecurity>, <xref:System.ServiceModel.MessageSecurityOverHttp>, <xref:System.ServiceModel.MessageCredentialType>, <xref:System.ServiceModel.SecurityMode>, <xref:System.ServiceModel.HttpTransportSecurity>, <xref:System.ServiceModel.HttpClientCredentialType>, e <xref:System.ServiceModel.HttpProxyCredentialType>.  
  
### <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 No código, use o <xref:System.ServiceModel.WSDualHttpBinding> classe; na configuração, use o [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).  
  
 Essa associação é projetada para permitir que os aplicativos de serviço duplex. Essa associação implementa a especificação WS-Security para segurança de transferência baseada em mensagem. Segurança de transporte não está disponível. Por padrão, ele fornece os seguintes recursos:  
  
- Implementa o WS-Reliable Messaging para confiabilidade.  
  
- Implementa o WS-Security para autenticação e segurança de transferência.  
  
- Usa HTTP para entrega de mensagens.  
  
- Usa a codificação de mensagem de texto/XML.  
  
 Usando o WS-Security (segurança de camada de mensagem), a associação permite que você configure os seguintes parâmetros:  
  
- O pacote de algoritmos de segurança para determinar o algoritmo de criptografia.  
  
- Opções de associação para o seguinte:  
  
    - Fornecendo serviço credenciais disponíveis fora de banda no cliente.  
  
    - Fornecer credenciais de serviço negociado do serviço como parte da configuração de canal.  
  
 Para obter mais informações, consulte <xref:System.ServiceModel.WSDualHttpSecurity> e <xref:System.ServiceModel.WSDualHttpSecurityMode>.  
  
### <a name="nettcpbinding"></a>NetTcpBinding  
 No código, use o <xref:System.ServiceModel.NetTcpBinding> classe; na configuração, use o [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 Essa associação é otimizada para comunicação entre computadores. Por padrão, ele tem as seguintes características:  
  
- Segurança de camada de transporte implementa.  
  
- Aproveita a segurança do Windows para autenticação e segurança de transferência.  
  
- Usa o TCP para o transporte.  
  
- Codificação de mensagem binária implementa.  
  
- Implementa WS-Reliable Messaging.  
  
 As opções incluem o seguinte:  
  
- Segurança de camada de mensagem (usando o WS-Security).  
  
- Segurança com credencial de mensagem de transporte — confidencialidade e integridade fornecida pela segurança de camada de transporte (TLS) sobre TCP e as credenciais de autorização fornecidos pelo WS-Security.  
  
 Para obter mais informações, consulte <xref:System.ServiceModel.NetTcpSecurity>, <xref:System.ServiceModel.TcpTransportSecurity>, <xref:System.ServiceModel.TcpClientCredentialType>, <xref:System.ServiceModel.MessageSecurityOverTcp> e <xref:System.ServiceModel.MessageCredentialType>.  
  
### <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 No código, use o <xref:System.ServiceModel.NetNamedPipeBinding> classe; na configuração, use o [ \<netNamedPipeBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).  
  
 Essa associação é otimizada para comunicação entre processos (normalmente no mesmo computador). Por padrão, essa associação tem as seguintes características:  
  
- Usa segurança de transporte para autenticação e transferência de mensagens.  
  
- Usa pipes nomeadas para entrega de mensagens.  
  
- Codificação de mensagem binária implementa.  
  
- A criptografia e assinatura de mensagens.  
  
 As opções incluem o seguinte:  
  
- Autenticação usando a segurança do Windows.  
  
 Para obter mais informações, consulte <xref:System.ServiceModel.NetNamedPipeSecurity>, <xref:System.ServiceModel.NetNamedPipeSecurityMode> e <xref:System.ServiceModel.NamedPipeTransportSecurity>.  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 No código, use o <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> classe; na configuração, use o [ \<msmqIntegrationBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).  
  
 Essa associação é otimizada para a criação de clientes do WCF e serviços que interoperam com pontos de extremidade de não - Microsoft mensagem enfileiramento de mensagens MSMQ do WCF.  
  
 Por padrão, essa ligação usa a segurança de transporte e fornece as seguintes características de segurança:  
  
- A segurança pode ser desativado (nenhum).  
  
- Segurança do transporte MSMQ (transporte).  
  
 Para obter mais informações, consulte <xref:System.ServiceModel.NetMsmqSecurity> e <xref:System.ServiceModel.NetMsmqSecurityMode>.  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 No código, use o <xref:System.ServiceModel.NetMsmqBinding> classe; na configuração, use o [ \<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md).  
  
 Essa associação destina para uso ao criar serviços WCF que exigem MSMQ na fila de suporte para mensagens.  
  
 Por padrão, essa ligação usa a segurança de transporte e fornece as seguintes características de segurança:  
  
- A segurança pode ser desativado (nenhum).  
  
- Segurança do transporte MSMQ (transporte).  
  
- Segurança de mensagem baseado em SOAP (mensagem).  
  
- Segurança de transporte e de mensagem simultânea (ambos).  
  
- Tipos de credencial de cliente com suporte: Nenhum, Windows, o nome de usuário, o certificado, o IssuedToken.  
  
 O <xref:System.ServiceModel.MessageCredentialType.Certificate> credencial é suportada apenas quando o modo de segurança é definido como <xref:System.ServiceModel.NetMsmqSecurityMode.Both> ou <xref:System.ServiceModel.NetMsmqSecurityMode.Message>.  
  
 Para obter mais informações, consulte <xref:System.ServiceModel.MessageSecurityOverMsmq> e <xref:System.ServiceModel.MsmqTransportSecurity>.  
  
### <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 No código, use o <xref:System.ServiceModel.WSFederationHttpBinding> classe; na configuração, use o [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 Por padrão, essa ligação usa WS-Security (segurança de camada de mensagem).  
  
 Para obter mais informações, consulte [federação](../../../../docs/framework/wcf/feature-details/federation.md), <xref:System.ServiceModel.WSFederationHttpSecurity>, e <xref:System.ServiceModel.WSFederationHttpSecurityMode>.  
  
## <a name="custom-bindings"></a>Associações personalizadas  
 Se nenhuma das associações fornecidas pelo sistema atende aos requisitos, você pode criar uma ligação personalizada com um elemento de associação de segurança personalizada. Para obter mais informações, consulte [recursos de segurança com associações personalizadas](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).  
  
## <a name="binding-choices"></a>Opções de associação  
 A tabela a seguir resume os recursos oferecidos na configuração do modo de segurança, ou seja, ele lista os recursos disponíveis quando o modo de segurança é definido como `Transport`, `Message`, ou `TransportWithMessageCredential`. Use essa tabela para ajudá-lo a localizar os recursos de segurança que seu aplicativo requer.  
  
|Configuração|Recursos|  
|-------------|--------------|  
|Transporte|Autenticação do servidor<br /><br /> Autenticação de cliente<br /><br /> Segurança ponto a ponto<br /><br /> Interoperabilidade<br /><br /> Aceleração de hardware<br /><br /> Alta taxa de transferência<br /><br /> Firewall seguro<br /><br /> Aplicativos de alta latência<br /><br /> Nova criptografia em vários saltos|  
|Mensagem|Autenticação do servidor<br /><br /> Autenticação de cliente<br /><br /> Segurança de ponta a ponta<br /><br /> Interoperabilidade<br /><br /> Rica de declarações<br /><br /> Federação<br /><br /> Autenticação multifator<br /><br /> Tokens personalizados<br /><br /> Serviço de carimbo de hora/cartório<br /><br /> Aplicativos de alta latência<br /><br /> Persistência de assinaturas de mensagem|  
|TransportWithMessageCredential|Autenticação do servidor<br /><br /> Autenticação de cliente<br /><br /> Segurança ponto a ponto<br /><br /> Interoperabilidade<br /><br /> Aceleração de hardware<br /><br /> Alta taxa de transferência<br /><br /> Declarações de cliente avançado<br /><br /> Federação<br /><br /> Autenticação multifator<br /><br /> Tokens personalizados<br /><br /> Firewall seguro<br /><br /> Aplicativos de alta latência<br /><br /> Nova criptografia em vários saltos|  
  
 A tabela a seguir lista as associações compatíveis com as várias configurações do modo. Selecione uma associação na tabela a ser usada para criar seu ponto de extremidade de serviço.  
  
|Associação|Suporte ao modo de transporte|Suporte ao modo de mensagem|Suporte de TransportWithMessageCredential|  
|-------------|----------------------------|--------------------------|--------------------------------------------|  
|`BasicHttpBinding`|Sim|Sim|Sim|  
|`WSHttpBinding`|Sim|Sim|Sim|  
|`WSDualHttpBinding`|Não|Sim|Não|  
|`NetTcpBinding`|Sim|Sim|Sim|  
|`NetNamedPipeBinding`|Sim|Não|Não|  
|`NetMsmqBinding`|Sim|Sim|Não|  
|`MsmqIntegrationBinding`|Sim|Não|Não|  
|`wsFederationHttpBinding`|Não|Sim|Sim|  
  
## <a name="transport-credentials-in-bindings"></a>Credenciais de transporte em associações  
 A tabela a seguir lista os tipos de credencial de cliente disponíveis ao usar qualquer `BasicHttpBinding` ou `WSHttpBinding` no modo de segurança de transporte.  
  
|Tipo|Descrição|  
|----------|-----------------|  
|Nenhum|Especifica que o cliente não precisa apresentar nenhuma credencial. Isso se traduz em um cliente anônimo.|  
|Basic|Autenticação básica. Para obter mais informações, consulte RFC 2617 – autenticação HTTP: Básica e Digest, disponível em <https://go.microsoft.com/fwlink/?LinkId=84023>.|  
|Digest|Autenticação Digest. Para obter mais informações, consulte RFC 2617 – autenticação HTTP: Básica e Digest, disponível em <https://go.microsoft.com/fwlink/?LinkId=84023>.|  
|NTLM|Autenticação NT LAN Manager (NTLM).|  
|Windows|Autenticação do Windows.|  
|Certificado|Autenticação executada usando um certificado.|  
|IssuedToken|Permite que o serviço exigir que o cliente seja autenticado usando um token emitido por um serviço de token de segurança ou por [!INCLUDE[infocard](../../../../includes/infocard-md.md)]. Para obter mais informações, consulte [federação e Tokens emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
### <a name="message-client-credentials-in-bindings"></a>Credenciais de cliente de mensagem em associações  
 A tabela a seguir lista os tipos de credencial de cliente disponíveis ao usar uma associação no modo de segurança de mensagem.  
  
|Tipo|Descrição|  
|----------|-----------------|  
|Nenhum|Permite que o serviço interaja com clientes anônimos.|  
|Windows|Permite que as trocas de mensagens SOAP a ser feita sob o contexto autenticado de uma credencial do Windows.|  
|UserName|Permite que o serviço exigir que o cliente seja autenticado usando uma credencial de nome de usuário. Observe que, quando o modo de segurança é definido como `TransportWithMessageCredential`, o WCF não oferece suporte para enviar uma senha digest ou derivação de chaves usando a senha e essas chaves para segurança de modo de mensagem. Como tal, o WCF impõe que o transporte é protegido ao usar as credenciais de nome de usuário.|  
|Certificado|Permite que o serviço exigir que o cliente seja autenticado usando um certificado.|  
|IssuedToken|Permite que o serviço usar um serviço de token de segurança para fornecer um token personalizado.|  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)
- [Protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [Selecionando um tipo de credencial](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [Recursos de segurança com associações personalizadas](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)
- [Comportamentos de segurança](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)
- [Modelo de segurança do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
