---
title: "Arquitetura de ativação do WAS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 58aeffb0-8f3f-4b40-80c8-15f3f1652fd3
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7563510fdd44336cb5f8c50705edefd732082347
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="was-activation-architecture"></a>Arquitetura de ativação do WAS
Este tópico relaciona e descreve os componentes do Windows Process Activation Service (também conhecido como WAS).  
  
## <a name="activation-components"></a>Componentes de ativação  
 FOI consiste em vários componentes de arquitetura:  
  
-   Adaptadores de escuta. Serviços do Windows que recebem mensagens em protocolos de rede específicos e se comunicar com o WAS para rotear mensagens de entrada para o processo de trabalho correto.  
  
-   FOI. O serviço do Windows que gerencia a criação e o tempo de vida de processos de trabalho.  
  
-   O executável do processo worker genérico (w3wp.exe).  
  
-   Gerenciador de aplicativos. Gerencia a criação e o tempo de vida de domínios de aplicativos que processam hospedar aplicativos dentro do trabalhador.  
  
-   Manipuladores de protocolo. Componentes de protocolo específico que executar no processo de trabalho e gerenciam a comunicação entre o processo de trabalho e os adaptadores de escuta individuais. Existem dois tipos de manipuladores de protocolo: processar manipuladores de protocolo e manipuladores de protocolo do AppDomain.  
  
 Quando WAS ativa uma instância do processo de trabalho, ele carrega os manipuladores de protocolo de processo necessários no processo de trabalho e usa o Gerenciador de aplicativos para criar um domínio de aplicativo para hospedar o aplicativo. O domínio do aplicativo carrega o código do aplicativo, bem como os manipuladores de protocolo do AppDomain que os protocolos de rede usados pelo exigem aplicativo.  
  
 ![ARQUITETURA](../../../../docs/framework/wcf/feature-details/media/wasarchitecture.gif "WASArchitecture")  
  
### <a name="listener-adapters"></a>Adaptadores de escuta  
 Os adaptadores de escuta são serviços individuais do Windows que implementam a lógica de comunicação de rede usada para receber mensagens usando o protocolo de rede na escuta. A tabela a seguir lista os adaptadores de escuta para [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] protocolos.  
  
|Nome de serviço do adaptador de escuta|Protocolo|Observações|  
|-----------------------------------|--------------|-----------|  
|W3SVC|HTTP|Componente comum que fornece ativação de HTTP para ambos os IIS 7.0 e [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].|  
|NetTcpActivator|net.tcp|Depende do serviço de NetTcpPortSharing.|  
|NetPipeActivator|net.pipe||  
|NetMsmqActivator|NET. MSMQ|Para uso com [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]-com base em aplicativos de enfileiramento de mensagens.|  
|NetMsmqActivator|FormatName|Versões anteriores fornece compatibilidade com aplicativos de enfileiramento de mensagens existentes.|  
  
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
 Processo e AppDomain manipuladores de protocolo para protocolos específicos são registrados no arquivo Web. config no nível da máquina.  
  
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
 [Configurando o WAS para utilização com o WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [Recursos de hospedagem do Windows Server App Fabric](http://go.microsoft.com/fwlink/?LinkId=201276)
