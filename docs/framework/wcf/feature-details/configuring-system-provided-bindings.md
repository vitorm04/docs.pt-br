---
title: Configurando associações fornecidas pelo sistema
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], system-provided bindings
- WCF [WCF], system-provided bindings
- bindings [WCF], system-provided
ms.assetid: 443f8d65-f1f2-4311-83b3-4d8fdf7ccf16
ms.openlocfilehash: c2c1f468fba404768fe01e84260125843964fea0
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69949622"
---
# <a name="configuring-system-provided-bindings"></a>Configurando associações fornecidas pelo sistema
As associações especificam o mecanismo de comunicação a ser usado ao se comunicar com um ponto de extremidade e indicam como se conectar a um ponto de extremidade. Associações consistem em elementos que definem como os canais de Windows Communication Foundation (WCF) são dispostos em camadas para fornecer os recursos de comunicação necessários. Uma associação contém três tipos de elementos:  
  
- Elementos de associação de canal de protocolo, que determinam a segurança, a confiabilidade, as configurações de fluxo de contexto ou os protocolos definidos pelo usuário a serem usados com as mensagens enviadas ao ponto de extremidade.  
  
- Elementos de associação de canal de transporte, que determinam o protocolo de transporte subjacente a ser usado ao enviar mensagens para o ponto de extremidade, por exemplo, TCP ou HTTP.  
  
- Elementos de associação de codificação de mensagens, que determinam a codificação de fio a ser usada para mensagens enviadas ao ponto de extremidade, por exemplo, texto/XML, binário ou MTOM (mecanismo de otimização de transmissão de mensagens).  
  
 Este tópico apresenta todas as associações do WCF (Windows Communication Foundation fornecido pelo sistema). Se nenhum deles atender aos requisitos exatos para seu aplicativo, você poderá criar uma associação usando a <xref:System.ServiceModel.Channels.CustomBinding> classe. Para obter mais informações sobre como criar associações personalizadas, confira [Associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
> [!IMPORTANT]
> Selecione uma associação com segurança habilitada. Por padrão, todas as associações, exceto a <xref:System.ServiceModel.BasicHttpBinding> associação, têm a segurança habilitada. Se você não selecionar uma associação segura, ou se desabilitar a segurança, verifique se as trocas de rede estão protegidas de alguma outra maneira, como estando em um data center protegido ou em uma rede isolada.  
  
> [!IMPORTANT]
> Não use contratos duplex com associações que não dão suporte à segurança ou que têm segurança desabilitada, a menos que a troca de rede seja protegida por outros meios.  
  
## <a name="system-provided-bindings"></a>Associações fornecidas pelo sistema  
 As associações a seguir são enviadas com o WCF.  
  
|Associação|Elemento de configuração|Descrição|  
|-------------|---------------------------|-----------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Uma associação que é adequada para comunicação com serviços Web compatíveis com o perfil WS-Basic, por exemplo, serviços baseados no ASP.NET Web Services (ASMX). Essa associação usa HTTP como o transporte e texto/XML como a codificação de mensagem padrão.|  
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Uma associação segura e interoperável que é adequada para contratos de serviço não duplex.|  
|<xref:System.ServiceModel.WS2007HttpBinding>|[\<ws2007HttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|Uma associação segura e interoperável que fornece suporte para as versões corretas <xref:System.ServiceModel.WSHttpBinding.Security%2A>dos <xref:System.ServiceModel.ReliableSession>elementos de <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> associação, e.|  
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Uma associação segura e interoperável que é adequada para contratos de serviços duplex ou para comunicação por intermediários SOAP.|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Uma associação segura e interoperável que dá suporte ao protocolo WS-Federation, permitindo que as organizações que estão em uma federação autentiquem e autorizem os usuários com eficiência.|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|[\<ws2007FederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)|Uma associação segura e interoperável que deriva de <xref:System.ServiceModel.WS2007HttpBinding> e dá suporte à segurança federada.|  
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Uma associação segura e otimizada, adequada para comunicação de computadores entre aplicativos do WCF.|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)|Uma associação segura, confiável e otimizada, que é adequada para comunicação no computador entre aplicativos do WCF.|  
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Uma associação na fila que é adequada para comunicação de computadores entre aplicativos do WCF.|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)|Uma associação que permite comunicação segura e de vários computadores.|  
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|Uma associação usada para configurar pontos de extremidade para serviços Web WCF expostos por meio de solicitações HTTP, em vez de mensagens SOAP.|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<msmqIntegrationBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)|Uma associação adequada para comunicação entre computadores entre um aplicativo WCF e aplicativos de enfileiramento de mensagens (também conhecidos como MSMQ) existentes.|  
  
## <a name="binding-features"></a>Recursos de associação  
 A tabela a seguir mostra alguns dos principais recursos de cada uma das associações fornecidas pelo sistema fornecidas. As associações são listadas na primeira coluna e as informações sobre os recursos são descritas na tabela. A tabela a seguir fornece um código para as abreviações de associação usadas. Para escolher uma associação, determine qual coluna atende a todas as funcionalidades de linha necessárias.  
  
|Associação|Interoperabilidade|Modo de segurança (padrão)|Session<br /><br /> (Padrão)|Transações|Duplex|  
|-------------|----------------------|----------------------------------|-----------------------------|------------------|------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|Basic Profile 1.1|(Nenhum), Transporte, Mensagem, Misto|Nenhum, (nenhum)|(Nenhum)|N/D|  
|<xref:System.ServiceModel.WSHttpBinding>|WS|Nenhum, transporte, (mensagem), misto|(Nenhum), transporte, sessão confiável|(Nenhum), Sim|N/D|  
|<xref:System.ServiceModel.WS2007HttpBinding>|WS-Security, WS-Trust, WS-SecureConversation, WS-SecurityPolicy|Nenhum, transporte, (mensagem), misto|(Nenhum), transporte, sessão confiável|(Nenhum), Sim|N/D|  
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|Nenhum, (mensagem)|(Sessão confiável)|(Nenhum), Sim|Sim|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federation|Nenhum, (mensagem), misto|(Nenhum), sessão confiável|(Nenhum), Sim|Não|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|WS-Federation|Nenhum, (mensagem), misto|(Nenhum), sessão confiável|(Nenhum), Sim|Não|  
|<xref:System.ServiceModel.NetTcpBinding>|.NET|Nenhum, (transporte), mensagem,<br /><br /> Mixed|Sessão confiável, (transporte)|(Nenhum), Sim|Sim|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|None<br /><br /> (Transporte)|Nenhum, (Transporte)|(Nenhum), Sim|Sim|  
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|Nenhum, mensagem, (transporte), ambos|(Nenhum)|(Nenhum), Sim|Não|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|Par|Nenhum, mensagem, (transporte), misto|(Nenhum)|(Nenhum)|Sim|  
|<xref:System.ServiceModel.WebHttpBinding>|.Net|Nenhum, transporte, TransportCredentialOnly|(Nenhum)|(Nenhum)|N/D|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|MSMQ|Nenhum, (Transporte)|(Nenhum)|(Nenhum), Sim|N/D|  
  
 A tabela a seguir explica os recursos encontrados na tabela anterior.  
  
|Recurso|Descrição|  
|-------------|-----------------|  
|Tipo de interoperabilidade|Nomeia a tecnologia ou o protocolo com o qual a associação garante a interoperação.|  
|Segurança|Especifica como o canal é protegido:<br /><br /> None A mensagem SOAP não está protegida e o cliente não está autenticado.<br />Porta Os requisitos de segurança são atendidos na camada de transporte.<br />Exibida Os requisitos de segurança são atendidos na camada de mensagens.<br />Norte Esse modo de segurança é conhecido `TransportWithMessageCredentials`como. Ele manipula as credenciais no nível da mensagem, e os requisitos de integridade e confidencialidade são satisfeitos pela camada de transporte.<br />Mesmo O nível de mensagem e a segurança de nível de transporte são usados. Essa capacidade é exclusiva do <xref:System.ServiceModel.NetMsmqBinding>.|  
|Session|Especifica se essa associação dá suporte a contratos de sessão.|  
|Transações|Especifica se as transações estão habilitadas.|  
|Duplex|Especifica se há suporte para os contratos duplex. Observe que esse recurso requer suporte para sessões na associação.|  
|Streaming|Especifica se o streaming de mensagens tem suporte.|  
  
## <a name="see-also"></a>Consulte também

- [Visão geral de criação de ponto de extremidade](../../../../docs/framework/wcf/endpoint-creation-overview.md)
- [Usando associações para configurar serviços e clientes](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [Programação básica do WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)
