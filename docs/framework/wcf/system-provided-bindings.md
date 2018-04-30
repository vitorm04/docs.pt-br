---
title: Associações fornecidas pelo sistema
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
- bindings [WCF], system-provided
ms.assetid: 2c243746-45ce-4588-995e-c17126a579a6
caps.latest.revision: 60
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4ccdab56a90f4114836dd9f0a56cc495657ee9c8
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="system-provided-bindings"></a>Associações fornecidas pelo sistema
Associações de especificar o mecanismo de comunicação para usar ao conversar com um ponto de extremidade e indicar como se conectar a um ponto de extremidade. Uma associação contém os seguintes elementos:  
  
-   A pilha do protocolo determina a segurança, confiabilidade e as configurações de fluxo de contexto a ser usado para mensagens que são enviadas para o ponto de extremidade.  
  
-   O transporte determina o protocolo de transporte subjacente para usar ao enviar mensagens para o ponto de extremidade, por exemplo, HTTP ou TCP.  
  
-   A codificação determina a codificação a ser usada para mensagens que são enviadas ao ponto de extremidade, por exemplo, text/XML, binário ou mecanismo de otimização de transmissão mensagem (MTOM) durante a transmissão.  
  
 Este tópico apresenta todos os fornecidos pelo sistema [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] associações. Se nenhuma delas atende aos critérios exatos para seu aplicativo, você pode criar uma associação personalizada. Para obter mais informações sobre como criar associações personalizadas, consulte [associações personalizadas](../../../docs/framework/wcf/extending/custom-bindings.md).  
  
 Uma associação segura e interoperável que oferece suporte ao protocolo WS-Federation permite que as organizações que estão em uma federação para autenticar e autorizar usuários com eficiência.  
  
> [!IMPORTANT]
>  Sempre selecione uma associação que inclui a segurança. Por padrão, todas as associações, exceto o [ \<basicHttpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) elemento ter segurança habilitada. Se você não selecionar uma associação de segurança ou desativar a segurança, certifique-se de proteger seus dados em alguma outra forma, como o armazenamento em um data center protegido ou em uma rede isolada.  
  
> [!IMPORTANT]
>  Nunca use contratos duplex com associações que não dão suporte à segurança ou que possuem segurança desabilitada a menos que você protege os dados por outros meios.  
  
## <a name="system-provided-bindings"></a>Associações fornecidas pelo sistema  
 As seguintes associações fornecidas com o [!INCLUDE[indigo2](../../../includes/indigo2-md.md)].  
  
|Associação|Elemento de configuração|Descrição|  
|-------------|---------------------------|-----------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|Uma associação que é adequada para se comunicar com o perfil básico WS compatível com serviços da Web, por exemplo, serviços Web do ASP.NET (ASMX)-serviços baseados em. Esta associação usa HTTP como o transporte e texto/XML como a codificação de mensagem padrão.|  
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|Uma associação segura e interoperável que é adequada para contratos de serviço não-duplex.|  
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|Uma associação segura e interoperável que é adequada para contratos de serviço duplex ou comunicação através de intermediários SOAP.|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|Uma associação segura e interoperável que suporta o protocolo de WS-Federation que permite que as organizações que estão em uma federação para autenticar e autorizar usuários com eficiência.|  
|<xref:System.ServiceModel.NetHttpBinding>|\<netHttpBinding>|Uma associação projetada para consumir serviços HTTP ou WebSocket que usa a codificação binária por padrão.|  
|<xref:System.ServiceModel.NetHttpsBinding>|\<netHttpsBinding >|Uma associação de segurança criada para consumir serviços HTTP ou WebSocket que usa a codificação binária por padrão.|  
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|Uma associação segura e otimizada adequada para comunicação entre computadores entre [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativos.|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding >](../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)|Uma associação segura, confiável e otimizada adequada para comunicação na máquina entre [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativos.|  
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding >](../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|Uma associação enfileirada adequada para comunicação entre computadores entre [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativos.|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding >](../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)|Uma associação que permite proteger, comunicação de vários computadores.|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<msmqIntegrationBinding>](../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)|Uma associação que é adequada para comunicação entre computadores entre um [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativos e aplicativos de enfileiramento de mensagens existentes.|  
|<xref:System.ServiceModel.BasicHttpContextBinding>|[\<basicHttpContextBinding >](../../../docs/framework/configure-apps/file-schema/wcf/basichttpcontextbinding.md)|Uma associação que é adequada para se comunicar com o perfil básico WS compatível serviços Web que permite que os cookies HTTP a ser usado para a troca de contexto.|  
|<xref:System.ServiceModel.NetTcpContextBinding>|[\<netTcpContextBinding >](../../../docs/framework/configure-apps/file-schema/wcf/nettcpcontextbinding.md)|Uma associação segura e otimizada adequada para comunicação entre computadores entre [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplicativos que permite que os cabeçalhos SOAP a ser usado para a troca de contexto.|  
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|Uma associação usada para configurar pontos de extremidade para serviços Web [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] expostos por meio de solicitações HTTP em vez de mensagens SOAP.|  
|<xref:System.ServiceModel.WSHttpContextBinding>|[\<wsHttpContextBinding >](../../../docs/framework/configure-apps/file-schema/wcf/wshttpcontextbinding.md)|Seguro e |<xref:System.ServiceModel.UdpBinding>|\<udpBinding>|Uma associação para usar ao enviar uma intermitência de mensagens simples para um grande número de clientes ao mesmo tempo.|  
  
 A tabela a seguir mostra os recursos de cada uma das associações fornecidas pelo sistema. As associações são encontradas nas colunas da tabela; os recursos estão listados nas linhas e descritos em uma segunda tabela. A tabela a seguir fornece uma chave para as abreviações de associação usado. Para selecionar uma associação, determine qual coluna atenda a todos os recursos de linha que é necessário.  
  
|Associação|Interoperabilidade|Segurança (padrão)|Session<br /><br /> (Padrão)|Transações|Duplex|Codificação (padrão)|Streaming<br /><br /> (Padrão)|  
|-------------|----------------------|--------------------------|-----------------------------|------------------|------------|--------------------------|-------------------------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|Basic Profile 1.1|(Nenhum), transporte, mensagem, misto|(Nenhum)|(Nenhum)|N/D|Texto, (MTOM)|Sim<br /><br /> (em buffer)|  
|<xref:System.ServiceModel.WSHttpBinding>|WS|Misto de transporte, (mensagem)|(Nenhum), a sessão confiável, sessão de segurança|(Nenhum), Sim|N/D|(Texto), MTOM|Não|  
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|(Mensagem), nenhum|(Sessão confiável), a sessão de segurança|(Nenhum), Sim|Sim|(Texto), MTOM|Não|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federation|(Mensagem), misto, None|(Nenhum), a sessão confiável, sessão de segurança|(Nenhum), Sim|Não|(Texto), MTOM|Não|  
|<xref:System.ServiceModel.NetHttpBinding>|.NET|(Nenhum), transporte, mensagem, TransportWithMessageCredential, TransportCredentialOnly|Consulte a observação abaixo|Nenhum|Consulte a observação abaixo|(Binário), texto, MTOM|Sim (em buffer)|  
|<xref:System.ServiceModel.NetHttpsBinding>|.NET|(Transporte), TransportWithMessageCredential|Consulte a observação abaixo|Nenhum|Consulte a observação abaixo|(Binário), texto, MTOM|Sim (em buffer)|  
|<xref:System.ServiceModel.NetTcpBinding>|.NET|(Transporte), mensagem, None, misto|(Transporte), a sessão confiável, sessão de segurança|(Nenhum), Sim|Sim|Binário|Sim<br /><br /> (em buffer)|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|(Transporte), nenhum|Nenhum (transporte)|(Nenhum), Sim|Sim|Binário|Sim<br /><br /> (em buffer)|  
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|Mensagem (transporte), nenhum|(Nenhum), de transporte|Nenhum (Sim)|Não|Binário|Não|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|ponto a ponto|(Transporte)|(Nenhum)|(Nenhum)|Sim||Não|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|MSMQ|(Transporte)|(Nenhum)|Nenhum (Sim)|N/D|N/D|Não|  
|<xref:System.ServiceModel.BasicHttpContextBinding>|Basic Profile 1.1|(Nenhum), transporte, mensagem, misto|(Nenhum)|(Nenhum)|N/D|Texto, (MTOM)|Sim<br /><br /> (em buffer)|  
|<xref:System.ServiceModel.NetTcpContextBinding>|.NET|(Transporte), mensagem, None, misto|(Transporte), a sessão confiável, sessão de segurança|(Nenhum), Sim|Sim|Binário|Sim<br /><br /> (em buffer)|  
|<xref:System.ServiceModel.WSHttpContextBinding>|WS|Misto de transporte, (mensagem)|(Nenhum), a sessão confiável, sessão de segurança|(Nenhum), Sim|N/D|Texto, (MTOM)|Não|  
|<xref:System.ServiceModel.UdpBinding>|.NET **Observação:** interoperabilidade pode ser obtida ao implementar a especificação de SOAP-over-UDP padrão que implementa essa associação.|(Nenhum)|(Nenhum)|(Nenhum)|N/D|(Texto)|Não|  
  
> [!IMPORTANT]
>  O <xref:System.ServiceModel.NetHttpBinding> é uma associação criada para consumir HTTP ou serviços WebSocket e usa a codificação binária por padrão. <xref:System.ServiceModel.NetHttpBinding> detecta se ele é usado com um contrato de solicitação-resposta ou um contrato duplex e alterar seu comportamento para corresponder - ele usará o HTTP para a solicitação-resposta e WebSockets para duplex. Esse comportamento pode ser substituído usando o <!--zz <xref:System.ServiceModel.NetHttpBinding.WebSocketTransportUsage%2A>--> `System.ServiceModel.NetHttpBinding.WebSocketTransportUsage` configuração de associação: permitida - este é o valor padrão e se comporta conforme descrito acima. Não permitido - Isso impede que o WebSocket que está sendo usado. Tentativa de usar um contrato duplex com essa configuração resultará em uma exceção. Necessária – isso força o WebSocket a ser usado até mesmo para contratos de solicitação-resposta. NetHttpBinding dá suporte a sessões confiáveis em modo de HTTP e o modo de WebSocket. No modo WebSocket as sessões são fornecidas pelo transporte.  
  
 A tabela a seguir explica os recursos listados na tabela anterior.  
  
|Recurso|Descrição|  
|-------------|-----------------|  
|Tipo de interoperabilidade|Nomeia o protocolo ou a tecnologia com a qual a associação garante interoperação.|  
|Segurança|Especifica como o canal é protegido:<br /><br /> -Nenhum: A mensagem SOAP não é protegida e o cliente não está autenticado.<br />-Transporte: Requisitos de segurança são satisfeitos na camada de transporte.<br />-Mensagem: Requisitos de segurança são satisfeitos na camada de mensagem.<br />-Misto: Declarações são executadas na mensagem; requisitos de integridade e confidencialidade são atendidos pela camada de transporte.|  
|Session|Especifica se essa associação oferece suporte a contratos de sessão.|  
|Transações|Especifica se as transações estão habilitadas.|  
|Duplex|Especifica se os contratos duplex têm suporte. Observe que esse recurso exige suporte para sessões na associação.|  
|Codificando|Especifica o formato de transmissão da mensagem. Valores permitidos são:<br /><br /> -Texto: por exemplo, UTF-8.<br />-Binário<br />-Mecanismo de otimização de transmissão mensagem (MTOM): Um método de codificação com eficiência os elementos XML binários de dentro do contexto de um envelope SOAP.|  
|Streaming|Especifica se o fluxo tem suporte para mensagens de entrada e saídas. Use o `TransferMode` propriedade na associação para definir o valor. Os valores possíveis incluem:<br /><br /> -   <xref:System.ServiceModel.TransferMode.Buffered>: As mensagens de solicitação e resposta são buffer.<br />-   <xref:System.ServiceModel.TransferMode.Streamed>: As mensagens de solicitação e resposta são transmitidas.<br />-   <xref:System.ServiceModel.TransferMode.StreamedRequest>: A mensagem de solicitação é transmitida e a mensagem de resposta é armazenada em buffer.<br />-   <xref:System.ServiceModel.TransferMode.StreamedResponse>: A mensagem de solicitação é armazenado em buffer e a mensagem de resposta é transmitida.|  
  
## <a name="see-also"></a>Consulte também  
 [Visão geral de criação de ponto de extremidade](../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [Usando associações para configurar serviços e clientes](../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [Programação básica do WCF](../../../docs/framework/wcf/basic-wcf-programming.md)
