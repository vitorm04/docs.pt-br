---
title: ConnectionOrientedTransportBindingElement
ms.date: 03/30/2017
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
ms.openlocfilehash: 04e6abc5941ec99769ff2c15d47881b60e81d2e0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62048387"
---
# <a name="connectionorientedtransportbindingelement"></a>ConnectionOrientedTransportBindingElement
ConnectionOrientedTransportBindingElement  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class ConnectionOrientedTransportBindingElement : TransportBindingElement  
{  
  datetime ChannelInitializationTimeout;  
  sint32 ConnectionBufferSize;  
  string HostNameComparisonMode;  
  sint32 MaxBufferSize;  
  datetime MaxOutputDelay;  
  sint32 MaxPendingAccepts;  
  sint32 MaxPendingConnections;  
  string TransferMode;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe ConnectionOrientedTransportBindingElement não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe ConnectionOrientedTransportBindingElement tem as seguintes propriedades:  
  
### <a name="channelinitializationtimeout"></a>ChannelInitializationTimeout  
 Tipo de dados: datetime  
  
 Tipo de acesso: Somente leitura  
  
 O timespan que especifica quanto tempo a inicialização do canal tem para ser concluída antes do tempo limite.  
  
### <a name="connectionbuffersize"></a>ConnectionBufferSize  
 Tipo de dados: sint32  
  
 Tipo de acesso: Somente leitura  
  
 O tamanho do buffer usado para transmitir uma parte da mensagem serializada na conexão do cliente ou do serviço.  
  
### <a name="hostnamecomparisonmode"></a>HostNameComparisonMode  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 Um valor que indica se o nome do host é usado para alcançar o serviço ao fazer a correspondência no URI.  
  
### <a name="maxbuffersize"></a>maxBufferSize  
 Tipo de dados: sint32  
  
 Tipo de acesso: Somente leitura  
  
 O tamanho máximo do buffer a usar.  
  
### <a name="maxoutputdelay"></a>MaxOutputDelay  
 Tipo de dados: datetime  
  
 Tipo de acesso: Somente leitura  
  
 O intervalo máximo de tempo que uma parte de uma mensagem ou uma mensagem completa pode permanecer armazenada em buffer na memória antes de serem enviados.  
  
### <a name="maxpendingaccepts"></a>MaxPendingAccepts  
 Tipo de dados: sint32  
  
 Tipo de acesso: Somente leitura  
  
 O número máximo de pendente assíncrono aceita threads que estão disponíveis para processar conexões de entrada no serviço.  
  
### <a name="maxpendingconnections"></a>MaxPendingConnections  
 Tipo de dados: sint32  
  
 Tipo de acesso: Somente leitura  
  
 O número máximo de conexões pendentes.  
  
### <a name="transfermode"></a>TransferMode  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: Somente leitura  
  
 Um valor que especifica se as mensagens são armazenadas em buffer ou transmitidas com o transporte orientado a conexão.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também

- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
