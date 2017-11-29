---
title: '&lt;namedPipeTransport&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9fc3f42f-43e2-4ab1-8bc7-3c95a9220df1
caps.latest.revision: "15"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4d2d4be08012c1d33341ddd17713903782027c31
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="ltnamedpipetransportgt"></a>&lt;namedPipeTransport&gt;
Define um transporte que faz com que um canal transferir mensagens usando pipes nomeados quando ele é incluído em uma associação personalizada.  
  
\<System. ServiceModel >  
\<associações >  
\<customBinding >  
\<associação >  
\<namePipeTransport >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml
<namedPipeTransport channelInitializationTimeout="TimeSpan"   
                    connectionBufferSize="Integer"   
                    hostNameComparisonMode="StrongWildcard/Exact/WeakWildcard"  
                    manualAddressing="Boolean"   
                    maxBufferPoolSize="Integer"  
                    maxBufferSize="Integer"  
                    maxOutputDelay="TimeSpan"  
                    maxPendingAccepts="Integer"   
                    maxPendingConnections="Integer"  
                    maxReceivedMessageSize="Integer"   
                    transferMode="Buffered/Streamed/StreamedRequest/StreamedResponse">  
  <connectionPoolSettings groupName="String" 
                          idleTimeout"TimeSpan"  
                          maxOutboundConnectionsPerEndpopint="Integer" />  
</namedPipeTransport>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|ChannelInitializationTimeout|Obtém ou define um <xref:System.TimeSpan> que determina o tempo máximo que um canal pode estar com o status de inicialização antes de ser desconectada.|  
|connectionBufferSize|Obtém ou define o tamanho do buffer usado para transmitir um bloco da mensagem serializada na conexão do cliente ou serviço.|  
|hostNameComparisonMode|Obtém ou define um valor que indica se o nome do host é usado para acessar o serviço ao fazer correspondência no URI.|  
|manualAddressing|Obtém ou define um valor que indica se o endereçamento manual da mensagem é necessário.|  
|maxBufferPoolSize|Obtém ou define o tamanho máximo, em bytes, de qualquer pool de buffer usado pelo transporte.|  
|maxBufferSize|Obtém ou define o tamanho máximo do buffer a ser usado. Para mensagens em fluxo, esse valor deve ser pelo menos o tamanho máximo possível dos cabeçalhos de mensagem, que são lidas no modo de buffer.|  
|maxOutputDelay|Obtém ou define o intervalo máximo de tempo que uma parte de uma mensagem ou uma mensagem completa pode permanecer em buffer na memória antes de serem enviadas.|  
|maxPendingAccepts|Obtém ou define o número máximo de canais de que um serviço pode ter aguardando um ouvinte para processar conexões de entrada para o serviço.|  
|maxPendingConnections|Obtém ou define o número máximo de conexões aguardando a expedição no serviço.|  
|maxReceivedMessageSize|Obtém e define o tamanho de mensagem máximo permitido, em bytes, que pode ser recebido.|  
|transferMode|Obtém ou define um valor que indica se as mensagens são armazenadas em buffer ou transmitidas em fluxo com o transporte orientado à conexão.|  
|[\<connectionPoolSettings > de \<namedPipeTransport >](../../../../../docs/framework/configure-apps/file-schema/wcf/connectionpoolsettings.md)|Especifica as configurações do pool de conexão adicionais para uma associação de Pipe nomeado.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<associação >](../../../../../docs/framework/misc/binding.md)|Define todos os recursos de associação da associação personalizada.|  
  
## <a name="remarks"></a>Comentários  
Esse transporte usa URIs no formato "net.pipe://hostname/path". Outros componentes do URI são opcionais.  
  
O `namedPipeTransport` elemento é o ponto de partida para criar uma associação personalizada que implementa o protocolo de transporte de pipes nomeados. Esse transporte é usado para em computadores Windows Communication Foundation (WCF) - para - comunicação WCF.  
  
## <a name="see-also"></a>Consulte também  
<xref:System.ServiceModel.Configuration.NamedPipeTransportElement>   
<xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>   
<xref:System.ServiceModel.Channels.TransportBindingElement>   
<xref:System.ServiceModel.Channels.CustomBinding>   
[Transportes](../../../../../docs/framework/wcf/feature-details/transports.md)   
[Selecionando um transporte](../../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)   
[Associações](../../../../../docs/framework/wcf/bindings.md)   
[Estendendo associações](../../../../../docs/framework/wcf/extending/extending-bindings.md)   
[Associações personalizadas](../../../../../docs/framework/wcf/extending/custom-bindings.md)   
[\<customBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
