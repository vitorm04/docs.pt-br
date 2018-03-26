---
title: Associações e segurança
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- bindings [WCF], security
- WCF security
- Windows Communication Foundation, security
- bindings [WCF]
ms.assetid: 4de03dd3-968a-4e65-af43-516e903d7f95
caps.latest.revision: ''
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload:
- dotnet
ms.openlocfilehash: 9e44db963a696f22f91569eb3d7c2956289a9c76
ms.sourcegitcommit: c883637b41ee028786edceece4fa872939d2e64c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/26/2018
---
# <a name="bindings-and-security"></a>Associações e segurança
As associações fornecidas pelo sistema acompanha [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] oferecem uma maneira rápida de programa [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplicativos. Com uma exceção, todas as associações de tem um esquema de segurança padrão habilitado. Este tópico ajuda você a selecionar a associação certa para suas necessidades de segurança.  
  
 Para obter uma visão geral de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] segurança, consulte [visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] programação [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usando associações, consulte [de programação WCF segurança](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md).  
  
 Se você já tiver selecionado uma associação, você pode encontrar mais informações sobre os comportamentos de tempo de execução que estão associados com a segurança em [comportamentos de segurança](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md).  
  
 Algumas funções de segurança não são programáveis usando as associações fornecidas pelo sistema. Para obter mais controle utilizando uma associação personalizada, consulte [recursos de segurança com associações personalizadas](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).  
  
## <a name="security-functions-of-bindings"></a>Funções de segurança de associações  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] inclui um número de associações fornecidas pelo sistema que atendem a maioria das necessidades. Se uma associação específica não é suficiente, você também pode criar uma associação personalizada. Para obter uma lista de associações fornecidas pelo sistema, consulte [System-Provided associações](../../../../docs/framework/wcf/system-provided-bindings.md). [!INCLUDE[crabout](../../../../includes/crabout-md.md)] associações personalizadas, consulte [associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
 Todas as associações de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] tem duas formas: como uma API e um elemento XML usados em um arquivo de configuração. Por exemplo, o `WSHttpBinding` (API) tem um equivalente [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 A seção a seguir lista as duas formas para cada associação e resume os recursos de segurança.  
  
### <a name="basichttp"></a>BasicHttp  
 No código, use o <xref:System.ServiceModel.BasicHttpBinding> classe; na configuração, use o [ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).  
  
 Essa associação é projetada para uso com uma variedade de tecnologias existentes, incluindo o seguinte:  
  
-   Serviços Web do ASP.NET (ASMX) versão 1.  
  
-   Aplicativos do Web Service Enhancements (WSE).  
  
-   Basic perfil conforme definido na interoperabilidade de serviços da Web (WS-I) specification ([http://go.microsoft.com/fwlink/?LinkId=38955](http://go.microsoft.com/fwlink/?LinkId=38955)).  
  
-   Perfil de segurança básicas, conforme definido no WS-I.  
  
 Por padrão, essa associação não é segura. Ele é projetado para interoperar com serviços ASMX. Quando a segurança está habilitada, a associação foi projetada para interoperação perfeita com mecanismos de segurança do Internet Information Services (IIS), como autenticação básica, digest e segurança integrada do Windows. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Visão geral de segurança de transporte](../../../../docs/framework/wcf/feature-details/transport-security-overview.md). Essa associação suporta o seguinte:  
  
-   Segurança de transporte HTTPS.  
  
-   Autenticação básica HTTP.  
  
-   O WS-Security.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.BasicHttpSecurity>, <xref:System.ServiceModel.BasicHttpMessageSecurity>, <xref:System.ServiceModel.BasicHttpMessageCredentialType>, e <xref:System.ServiceModel.BasicHttpSecurityMode>.  
  
### <a name="wshttpbinding"></a>WSHttpBinding  
 No código, use o <xref:System.ServiceModel.WSHttpBinding> classe; na configuração, use o [ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md).  
  
 Por padrão, essa associação implementa a especificação WS-Security e permite a interoperabilidade com serviços que implementam o WS-* especificações. Ele oferece suporte a:  
  
-   Segurança de transporte HTTPS.  
  
-   O WS-Security.  
  
-   Proteção de transporte com segurança de credencial de mensagem SOAP para autenticar o chamador de HTTPS.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.WSHttpSecurity>, <xref:System.ServiceModel.MessageSecurityOverHttp>, <xref:System.ServiceModel.MessageCredentialType>, <xref:System.ServiceModel.SecurityMode>, <xref:System.ServiceModel.HttpTransportSecurity>, <xref:System.ServiceModel.HttpClientCredentialType>, e <xref:System.ServiceModel.HttpProxyCredentialType>.  
  
### <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 No código, use o <xref:System.ServiceModel.WSDualHttpBinding> classe; na configuração, use o [ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md).  
  
 Essa associação foi projetada para permitir que os aplicativos de serviço duplex. Essa associação implementa a especificação WS-Security para segurança baseada em mensagens de transferência. Segurança de transporte não está disponível. Por padrão, ele fornece os seguintes recursos:  
  
-   Implementa o WS-Reliable mensagens para a confiabilidade.  
  
-   Implementa o WS-Security para autenticação e segurança de transferência.  
  
-   Usa HTTP para entrega de mensagens.  
  
-   Usa a codificação de mensagem de texto/XML.  
  
 Usando o WS-Security (segurança de camada de mensagem), a associação permite que você configure os seguintes parâmetros:  
  
-   O conjunto de algoritmos de segurança para determinar o algoritmo de criptografia.  
  
-   Opções de associação para o seguinte:  
  
    -   Fornecendo serviço credenciais disponíveis fora de banda no cliente.  
  
    -   Fornecer credenciais de serviço negociado do serviço como parte da instalação do canal.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.WSDualHttpSecurity> e <xref:System.ServiceModel.WSDualHttpSecurityMode>.  
  
### <a name="nettcpbinding"></a>NetTcpBinding  
 No código, use o <xref:System.ServiceModel.NetTcpBinding> classe; na configuração, use o [ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md).  
  
 Essa associação é otimizada para comunicação entre computadores. Por padrão, ele tem as seguintes características:  
  
-   Segurança de camada de transporte implementa.  
  
-   Aproveita a segurança do Windows para autenticação e segurança de transferência.  
  
-   Usa o TCP para o transporte.  
  
-   Codificação de mensagem binária implementa.  
  
-   Mensagens WS-Reliable implementa.  
  
 As opções incluem o seguinte:  
  
-   Segurança de camada de mensagem (usando o WS-Security).  
  
-   Segurança com credencial de mensagem de transporte — fornecida por segurança de camada de transporte (TLS) sobre TCP e as credenciais de autorização fornecida pelo WS-Security de integridade e confidencialidade.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.NetTcpSecurity>, <xref:System.ServiceModel.TcpTransportSecurity>, <xref:System.ServiceModel.TcpClientCredentialType>, <xref:System.ServiceModel.MessageSecurityOverTcp>, e <xref:System.ServiceModel.MessageCredentialType>.  
  
### <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 No código, use o <xref:System.ServiceModel.NetNamedPipeBinding> classe; na configuração, use o [ \<netNamedPipeBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md).  
  
 Essa associação é otimizada para comunicação entre processos (normalmente no mesmo computador). Por padrão, essa associação tem as seguintes características:  
  
-   Usa a segurança para autenticação e transferência de mensagens de transporte.  
  
-   Usa pipes nomeados para entrega de mensagens.  
  
-   Codificação de mensagem binária implementa.  
  
-   Criptografia e assinatura de mensagens.  
  
 As opções incluem o seguinte:  
  
-   Autenticação usando a segurança do Windows.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.NetNamedPipeSecurity>, <xref:System.ServiceModel.NetNamedPipeSecurityMode>, e <xref:System.ServiceModel.NamedPipeTransportSecurity>.  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 No código, use o <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding> classe; na configuração, use o [ \<msmqIntegrationBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md).  
  
 Essa associação é otimizada para a criação de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] clientes e serviços que interoperam com não[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] pontos de extremidade do serviço de enfileiramento de mensagens da Microsoft (MSMQ).  
  
 Por padrão, esta associação usa segurança de transporte e fornece as seguintes características de segurança:  
  
-   Segurança pode ser desativado (nenhum).  
  
-   Segurança de transporte MSMQ (transporte).  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.NetMsmqSecurity> e <xref:System.ServiceModel.NetMsmqSecurityMode>.  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 No código, use o <xref:System.ServiceModel.NetMsmqBinding> classe; na configuração, use o [ \<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md).  
  
 Essa associação é destinada para uso ao criar [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] suporte a mensagens na fila de serviços que exigem MSMQ.  
  
 Por padrão, esta associação usa segurança de transporte e fornece as seguintes características de segurança:  
  
-   Segurança pode ser desativado (nenhum).  
  
-   Segurança de transporte MSMQ (transporte).  
  
-   Segurança de mensagens de baseado em SOAP (mensagem).  
  
-   Segurança de transporte e de mensagem simultânea (Both).  
  
-   Tipos de credencial de cliente com suporte: nenhum, Windows, o nome de usuário, o certificado, o IssuedToken.  
  
 O <xref:System.ServiceModel.MessageCredentialType.Certificate> credencial é suportada apenas quando o modo de segurança é definido como <xref:System.ServiceModel.NetMsmqSecurityMode.Both> ou <xref:System.ServiceModel.NetMsmqSecurityMode.Message>.  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] <xref:System.ServiceModel.MessageSecurityOverMsmq> e <xref:System.ServiceModel.MsmqTransportSecurity>.  
  
### <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 No código, use o <xref:System.ServiceModel.WSFederationHttpBinding> classe; na configuração, use o [ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md).  
  
 Por padrão, esta associação usa WS-Security (segurança de camada de mensagem).  
  
 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Federação](../../../../docs/framework/wcf/feature-details/federation.md), <xref:System.ServiceModel.WSFederationHttpSecurity>, e <xref:System.ServiceModel.WSFederationHttpSecurityMode>.  
  
## <a name="custom-bindings"></a>Associações personalizadas  
 Se nenhuma das associações fornecidas pelo sistema atende aos requisitos, você pode criar uma associação personalizada com um elemento de associação de segurança personalizada. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Recursos de segurança com associações personalizadas](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md).  
  
## <a name="binding-choices"></a>Opções de ligação  
 A tabela a seguir resume os recursos oferecidos na configuração de modo de segurança, ou seja, ela lista os recursos disponíveis quando o modo de segurança é definido como `Transport`, `Message`, ou `TransportWithMessageCredential`. Use esta tabela para ajudá-lo a localizar os recursos de segurança que requer que seu aplicativo.  
  
|Configuração|Recursos|  
|-------------|--------------|  
|Transporte|Autenticação do servidor<br /><br /> Autenticação de cliente<br /><br /> Segurança ponto a ponto<br /><br /> Interoperabilidade<br /><br /> Aceleração de hardware<br /><br /> Alta taxa de transferência<br /><br /> Firewall seguro<br /><br /> Aplicativos de alta latência<br /><br /> Nova criptografia entre vários saltos|  
|Mensagem|Autenticação do servidor<br /><br /> Autenticação de cliente<br /><br /> Segurança de ponta a ponta<br /><br /> Interoperabilidade<br /><br /> Declarações avançada<br /><br /> Federação<br /><br /> Autenticação multifator<br /><br /> Tokens personalizados<br /><br /> Serviço de carimbo de hora/cartório<br /><br /> Aplicativos de alta latência<br /><br /> Persistência de assinaturas de mensagem|  
|TransportWithMessageCredential|Autenticação do servidor<br /><br /> Autenticação de cliente<br /><br /> Segurança ponto a ponto<br /><br /> Interoperabilidade<br /><br /> Aceleração de hardware<br /><br /> Alta taxa de transferência<br /><br /> Declarações de cliente avançado<br /><br /> Federação<br /><br /> Autenticação multifator<br /><br /> Tokens personalizados<br /><br /> Firewall seguro<br /><br /> Aplicativos de alta latência<br /><br /> Nova criptografia entre vários saltos|  
  
 A tabela a seguir lista as associações que oferecem suporte as várias configurações de modo. Selecione uma associação da tabela a ser usado para criar seu ponto de extremidade de serviço.  
  
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
 A tabela a seguir lista os tipos de credencial de cliente disponíveis ao usar uma `BasicHttpBinding` ou `WSHttpBinding` no modo de segurança de transporte.  
  
|Tipo|Descrição|  
|----------|-----------------|  
|Nenhum|Especifica que o cliente não precisa apresentar credenciais. Isso se traduz em um cliente anônimo.|  
|Basic|Autenticação básica. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] RFC 2617 – autenticação HTTP: Basic e a autenticação Digest, disponível em [ http://go.microsoft.com/fwlink/?LinkId=84023 ](http://go.microsoft.com/fwlink/?LinkId=84023).|  
|Digest|Autenticação Digest. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] RFC 2617 – autenticação HTTP: Basic e a autenticação Digest, disponível em [ http://go.microsoft.com/fwlink/?LinkId=84023 ](http://go.microsoft.com/fwlink/?LinkId=84023).|  
|NTLM|Autenticação NT LAN Manager (NTLM).|  
|Windows|Autenticação do Windows.|  
|certificado|Autenticação executada usando um certificado.|  
|IssuedToken|Permite que o serviço exigir que o cliente seja autenticado usando um token emitido por um serviço de token de segurança ou por [!INCLUDE[infocard](../../../../includes/infocard-md.md)]. [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Federação e Tokens emitidos](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md).|  
  
### <a name="message-client-credentials-in-bindings"></a>Credenciais do cliente de mensagem em associações  
 A tabela a seguir lista os tipos de credencial de cliente disponíveis ao usar uma associação no modo de segurança de mensagem.  
  
|Tipo|Descrição|  
|----------|-----------------|  
|Nenhum|Permite que o serviço interaja com clientes anônimos.|  
|Windows|Permite que as trocas de mensagens SOAP a serem feitas sob o contexto autenticado de uma credencial do Windows.|  
|UserName|Permite que o serviço exigir que o cliente seja autenticado usando uma credencial de nome de usuário. Observe que, quando o modo de segurança é definido como `TransportWithMessageCredential`, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] não oferece suporte para enviar uma senha digest ou derivação de chaves usando a senha e essas chaves para segurança de modo de mensagem. Como tal, [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] impõe que o transporte é protegido ao usar as credenciais de nome de usuário.|  
|certificado|Permite que o serviço exigir que o cliente seja autenticado usando um certificado.|  
|IssuedToken|Permite que o serviço usar um serviço de token de segurança para fornecer um token personalizado.|  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de segurança](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [Protegendo serviços e clientes](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [Selecionando um tipo de credencial](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [Recursos de segurança com associações personalizadas](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [Comportamentos de segurança](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Modelo de segurança para o Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
