---
title: Arquitetura de ativação do WAS
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 67ddcd97ac75ddeb0765c38bb9ce7b5e8f039272
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184249"
---
# <a name="was-activation-architecture"></a>Arquitetura de ativação do WAS
Este tópico itemeiza e discute os componentes do Serviço de Ativação de Processos do Windows (também conhecido como WAS).  
  
## <a name="activation-components"></a>Componentes de ativação  
 Was consiste em vários componentes arquitetônicos:  
  
- Adaptadores de ouvintes. Os serviços do Windows que recebem mensagens em protocolos específicos de rede e se comunicam com o WAS para encaminhar mensagens recebidas para o processo correto do trabalhador.  
  
- Foi. O serviço Windows que gerencia a criação e a vida útil dos processos dos trabalhadores.  
  
- O processo de trabalhador genérico executável (w3wp.exe).  
  
- Gerente de aplicativos. Gerencia a criação e a vida útil dos domínios de aplicativos que hospedam aplicativos dentro do processo do trabalhador.  
  
- Manipuladores de protocolo. Componentes específicos do protocolo que executam no processo do trabalhador e gerenciam a comunicação entre o processo do trabalhador e os adaptadores individuais do ouvinte. Existem dois tipos de manipuladores de protocolo: manipuladores de protocolo de processo e manipuladores de protocolo AppDomain.  
  
 Quando o WAS ativa uma instância de processo do trabalhador, ele carrega os manipuladores de protocolo de processo necessários no processo do trabalhador e usa o gerenciador de aplicativos para criar um domínio de aplicativo para hospedar o aplicativo. O domínio do aplicativo carrega o código do aplicativo, bem como os manipuladores de protocolo AppDomain que os protocolos de rede usados pelo aplicativo exigem.  
  
 ![Captura de tela que mostra a arquitetura WAS.](./media/was-activation-architecture/windows-process-application-service-architecture.gif)  
  
### <a name="listener-adapters"></a>Adaptadores de Ouvintes  
 Os adaptadores de ouvinte são serviços individuais do Windows que implementam a lógica de comunicação de rede usada para receber mensagens usando o protocolo de rede no qual eles ouvem. A tabela a seguir lista os adaptadores de ouvinte para protocolos Da Windows Communication Foundation (WCF).  
  
|Nome do serviço do adaptador do ouvinte|Protocolo|Observações|  
|-----------------------------------|--------------|-----------|  
|W3SVC|http|Componente comum que fornece ativação HTTP para IIS 7.0 e WCF.|  
|NetTcpActivator|net.tcp|Depende do serviço NetTcpPortSharing.|  
|NetPipeActivator|net.pipe||  
|NetMsmqActivator|net.msmq|Para uso com aplicativos de fila de mensagens baseados em WCF.|  
|NetMsmqActivator|msmq.formatname|Fornece retrocompatibilidade com aplicativos de fila de mensagens existentes.|  
  
 Os adaptadores de ouvinte para protocolos específicos são registrados durante a instalação no arquivo applicationHost.config, como mostrado no exemplo XML a seguir.  
  
```xml  
<system.applicationHost>  
    <listenerAdapters>  
        <add name="http" />  
        <add name="net.tcp"
          identity="S-1-5-80-3579033775-2824656752-1522793541-1960352512-462907086" />  
         <add name="net.pipe"
           identity="S-1-5-80-2943419899-937267781-4189664001-1229628381-3982115073" />  
          <add name="net.msmq"
            identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
           <add name="msmq.formatname"
             identity="S-1-5-80-89244771-1762554971-1007993102-348796144-2203111529" />  
    </listenerAdapters>  
</system.applicationHost>  
```  
  
### <a name="protocol-handlers"></a>Manipuladores de protocolo  
 Os manipuladores de protocolos Process e AppDomain para protocolos específicos estão registrados no arquivo Web.config no nível da máquina.  
  
```xml  
<system.web>  
   <protocols>  
      <add name="net.tcp"
        processHandlerType=  
         "System.ServiceModel.WasHosting.TcpProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.TcpAppDomainProtocolHandler"  
        validate="false" />  
      <add name="net.pipe"
        processHandlerType=  
         "System.ServiceModel.WasHosting.NamedPipeProcessProtocolHandler"  
          appDomainHandlerType=  
           "System.ServiceModel.WasHosting.NamedPipeAppDomainProtocolHandler"/>  
      <add name="net.msmq"  
        processHandlerType=  
         "System.ServiceModel.WasHosting.MsmqProcessProtocolHandler"  
        appDomainHandlerType=  
         "System.ServiceModel.WasHosting.MsmqAppDomainProtocolHandler"  
        validate="false" />  
   </protocols>  
</system.web>  
```  
  
## <a name="see-also"></a>Confira também

- [Configurar o WAS para uso com o WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [Recursos de hospedagem do Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
