---
title: Configurando associações fornecidas pelo sistema
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], system-provided bindings
- WCF [WCF], system-provided bindings
- bindings [WCF], system-provided
ms.assetid: 443f8d65-f1f2-4311-83b3-4d8fdf7ccf16
ms.openlocfilehash: 184f4da26df2c688b2b6f30f063bab058af37a4a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33496832"
---
# <a name="configuring-system-provided-bindings"></a>Configurando associações fornecidas pelo sistema
Associações de especificar o mecanismo de comunicação para usar ao conversar com um ponto de extremidade e indicar como se conectar a um ponto de extremidade. Associações consistem em elementos que definem como os canais do Windows Communication Foundation (WCF) são colocados para fornecer os recursos de comunicação solicitado. Uma associação contém três tipos de elementos:  
  
-   Elementos de associação de canal do protocolo, que determinam a segurança, confiabilidade, as configurações de fluxo do contexto ou protocolos definidos pelo usuário a ser usado com mensagens que são enviadas para o ponto de extremidade.  
  
-   Transporte de elementos de associação de canal, que determinam o protocolo de transporte subjacente para usar ao enviar mensagens para o ponto de extremidade, por exemplo, HTTP ou TCP.  
  
-   Codificação de elementos de associação que determinam a codificação para uso para mensagens que são enviadas para o ponto de extremidade, por exemplo, text/XML, binário, durante a transmissão de mensagens ou mecanismo de otimização de transmissão mensagem (MTOM).  
  
 Este tópico apresenta todas as associações fornecidas pelo sistema do Windows Communication Foundation (WCF). Se nenhuma delas atende os requisitos exatos para seu aplicativo, você pode criar uma associação usando o <xref:System.ServiceModel.Channels.CustomBinding> classe. Para obter mais informações sobre como criar associações personalizadas, consulte [associações personalizadas](../../../../docs/framework/wcf/extending/custom-bindings.md).  
  
> [!IMPORTANT]
>  Selecione uma associação com segurança habilitada. Por padrão, todas as associações, exceto o <xref:System.ServiceModel.BasicHttpBinding> associação, ter segurança habilitada. Se você não selecionar uma associação de segurança, ou se você desativar a segurança, certifique-se de que as trocas de sua rede estão protegidas em alguma outra forma, como estando em um data center protegido ou em uma rede isolada.  
  
> [!IMPORTANT]
>  Não use contratos duplex com associações que não dão suporte à segurança, ou que possuem segurança desativada, a menos que a troca de rede é protegida por outros meios.  
  
## <a name="system-provided-bindings"></a>Associações fornecidas pelo sistema  
 As seguintes associações são fornecidas com o WCF.  
  
|Associação|Elemento de configuração|Descrição|  
|-------------|---------------------------|-----------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Uma associação que é adequada para se comunicar com o perfil básico WS compatível com serviços da Web, por exemplo, serviços Web do ASP.NET (ASMX)-serviços baseados em. Esta associação usa HTTP como o transporte e texto/XML como a codificação de mensagem padrão.|  
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Uma associação segura e interoperável que é adequada para contratos de serviço não-duplex.|  
|<xref:System.ServiceModel.WS2007HttpBinding>|[\<ws2007HttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|Uma associação segura e interoperável que fornece suporte para as versões corretas do <xref:System.ServiceModel.WSHttpBinding.Security%2A>, <xref:System.ServiceModel.ReliableSession>, e <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> elementos de associação.|  
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Uma associação segura e interoperável que é adequada para contratos de serviço duplex ou comunicação através de intermediários SOAP.|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Uma associação segura e interoperável que suporta o protocolo WS-Federation, permitindo que as organizações que estão em uma federação para autenticar e autorizar usuários com eficiência.|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|[\<WS2007FederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)|Uma associação segura e interoperável que deriva de <xref:System.ServiceModel.WS2007HttpBinding> e dá suporte à segurança federada.|  
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Uma associação segura e otimizada adequada para comunicação entre computadores entre os aplicativos do WCF.|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)|Uma associação segura, confiável e otimizada adequada para a comunicação entre aplicativos WCF na máquina.|  
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Uma associação enfileirada adequada para comunicação entre computadores entre os aplicativos do WCF.|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)|Uma associação que permite a comunicação segura, com vários computador.|  
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|Uma associação usada para configurar pontos de extremidade para serviços Web WCF que são expostos por meio de solicitações HTTP em vez de mensagens SOAP.|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<msmqIntegrationBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)|Uma associação que é adequada para comunicação entre computadores entre um aplicativo WCF e enfileiramento de mensagens existente (também conhecido como MSMQ) aplicativos.|  
  
## <a name="binding-features"></a>Recursos de associação  
 A tabela a seguir mostra alguns dos principais recursos cada uma das associações fornecidas pelo sistema fornecidas. As associações são listadas na primeira coluna e informações sobre os recursos são descritas na tabela. A tabela a seguir fornece uma chave para as abreviações de associação usado. Para selecionar uma associação, determine qual coluna atenda a todos os recursos de linha que é necessário.  
  
|Associação|Interoperabilidade|Modo de segurança (padrão)|Session<br /><br /> (Padrão)|Transações|Duplex|  
|-------------|----------------------|----------------------------------|-----------------------------|------------------|------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|Basic Profile 1.1|(Nenhum), transporte, mensagem, misto|Nenhum, (nenhum)|(Nenhum)|N/D|  
|<xref:System.ServiceModel.WSHttpBinding>|WS|Nenhum, transporte, (mensagem), misto|(Nenhum), transporte, confiável sessão|(Nenhum), Sim|N/D|  
|<xref:System.ServiceModel.WS2007HttpBinding>|WS-Security, WS-Trust, WS-SecureConversation, WS-SecurityPolicy.|Nenhum, transporte, (mensagem), misto|(Nenhum), transporte, confiável sessão|(Nenhum), Sim|N/D|  
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|Nenhum (mensagem)|(Sessão confiável)|(Nenhum), Sim|Sim|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federation|Nenhum (mensagem), misto|(Nenhum), a sessão confiável|(Nenhum), Sim|Não|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|WS-Federation|Nenhum (mensagem), misto|(Nenhum), a sessão confiável|(Nenhum), Sim|Não|  
|<xref:System.ServiceModel.NetTcpBinding>|.NET|Nenhum, (transporte), a mensagem,<br /><br /> Mixed|Sessão confiável, (transporte)|(Nenhum), Sim|Sim|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|Nenhum,<br /><br /> (Transporte)|Nenhum (transporte)|(Nenhum), Sim|Sim|  
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|Nenhum, mensagem, (transporte), ambos|(Nenhum)|(Nenhum), Sim|Não|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|ponto a ponto|Nenhum, mensagem, (transporte) misto|(Nenhum)|(Nenhum)|Sim|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|MSMQ|Nenhum (transporte)|(Nenhum)|(Nenhum), Sim|N/D|  
  
 A tabela a seguir explica os recursos encontrados na tabela anterior.  
  
|Recurso|Descrição|  
|-------------|-----------------|  
|Tipo de interoperabilidade|Nomeia o protocolo ou a tecnologia com a qual a associação garante interoperação.|  
|Segurança|Especifica como o canal é protegido:<br /><br /> -Nenhum: A mensagem SOAP não é protegida e o cliente não está autenticado.<br />-Transporte: Requisitos de segurança são satisfeitos na camada de transporte.<br />-Mensagem: Requisitos de segurança são satisfeitos na camada de mensagem.<br />-Misto: Esse modo de segurança é conhecido como `TransportWithMessageCredentials`. Gerencia as credenciais no nível da mensagem e requisitos de integridade e confidencialidade são atendidos pela camada de transporte.<br />-Ambos: Ambos mensagem transporte e o nível de segurança em nível são usados. Essa capacidade é exclusiva para o <xref:System.ServiceModel.NetMsmqBinding>.|  
|Session|Especifica se essa associação oferece suporte a contratos de sessão.|  
|Transações|Especifica se as transações estão habilitadas.|  
|Duplex|Especifica se os contratos duplex têm suporte. Observe que esse recurso exige suporte para sessões na associação.|  
|Streaming|Especifica se o fluxo de mensagem tem suporte.|  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de criação de ponto de extremidade](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Usando associações para configurar serviços e clientes](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Programação básica do WCF](../../../../docs/framework/wcf/basic-wcf-programming.md)
