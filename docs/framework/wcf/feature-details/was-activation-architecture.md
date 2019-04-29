---
title: Arquitetura de ativação do WAS
ms.date: 03/30/2017
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
ms.openlocfilehash: 9c1af21782b377a9fb01cbd05e4fe61f6a69f3ac
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61932697"
---
# <a name="was-activation-architecture"></a>Arquitetura de ativação do WAS
Este tópico relaciona e descreve os componentes do Windows Process Activation Service (também conhecido como WAS).  
  
## <a name="activation-components"></a>Componentes de ativação  
 FOI consiste em vários componentes de arquitetura:  
  
- Adaptadores de escuta. Serviços do Windows que recebem mensagens em protocolos de rede específico e se comunicar com o WAS para rotear mensagens de entrada para o processo de trabalho correto.  
  
- ERA. O serviço do Windows que gerencia a criação e o tempo de vida de processos de trabalho.  
  
- O executável de processo de trabalho genérica (w3wp.exe).  
  
- Gerenciador de aplicativos. Gerencia a criação e o tempo de vida de domínios de aplicativos que processam hospedar aplicativos dentro do trabalhador.  
  
- Manipuladores de protocolo. Componentes específicos de protocolo que são executados no processo de trabalho e gerenciam a comunicação entre o processo de trabalho e os adaptadores de escuta individuais. Existem dois tipos de manipuladores de protocolo: processar manipuladores de protocolo e manipuladores de protocolo AppDomain.  
  
 Ao WAS ativa uma instância do processo de trabalho, ele carrega os manipuladores de protocolo de processo necessários no processo de trabalho e usa o Gerenciador de aplicativos para criar um domínio de aplicativo para hospedar o aplicativo. O domínio do aplicativo carrega o código do aplicativo, bem como os manipuladores de protocolo AppDomain que os protocolos de rede usados pelo exigem aplicativo.  
  
 ![Captura de tela que mostra a arquitetura do WAS.](./media/was-activation-architecture/windows-process-application-service-architecture.gif)  
  
### <a name="listener-adapters"></a>Adaptadores de escuta  
 Os adaptadores de escuta são serviços individuais do Windows que implementam a lógica de comunicação de rede usada para receber mensagens usando o protocolo de rede no qual eles escutam. A tabela a seguir lista os adaptadores de escuta para protocolos do Windows Communication Foundation (WCF).  
  
|Nome do serviço de adaptador de ouvinte|Protocolo|Observações|  
|-----------------------------------|--------------|-----------|  
|W3SVC|HTTP|Componente comum que fornece a ativação de HTTP para IIS 7.0 e o WCF.|  
|NetTcpActivator|net.tcp|Depende do serviço NetTcpPortSharing.|  
|NetPipeActivator|net.pipe||  
|NetMsmqActivator|net.msmq|Para uso com aplicativos de enfileiramento de mensagens baseada no WCF.|  
|NetMsmqActivator|msmq.formatname|É compatível com aplicativos de enfileiramento de mensagens existentes.|  
  
 Os adaptadores de escuta para protocolos específicos são registrados durante a instalação no arquivo applicationHost. config, conforme mostrado no exemplo XML a seguir.  
  
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
 Processo e manipuladores de protocolo AppDomain para protocolos específicos são registrados no arquivo de Web. config de nível de máquina.  
  
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
  
## <a name="see-also"></a>Consulte também

- [Configurando o WAS para utilização com o WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [Recursos de hospedagem do Windows Server App Fabric](https://go.microsoft.com/fwlink/?LinkId=201276)
