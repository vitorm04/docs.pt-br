---
title: ConnectionOrientedTransportBindingElement
ms.date: 03/30/2017
ms.assetid: c1308313-f0e2-49e6-977d-6b4ce9ad35d1
ms.openlocfilehash: 3b1055e6e2329fd213ae973ad32cdf8014d30a04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33487442"
---
# <a name="connectionorientedtransportbindingelement"></a>ConnectionOrientedTransportBindingElement
ConnectionOrientedTransportBindingElement  
  
## <a name="syntax"></a>Sintaxe  
  
```  
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
 A classe ConnectionOrientedTransportBindingElement não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe ConnectionOrientedTransportBindingElement tem as seguintes propriedades:  
  
### <a name="channelinitializationtimeout"></a>ChannelInitializationTimeout  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 O timespan que especifica quanto tempo a inicialização do canal tem para concluir antes do tempo limite.  
  
### <a name="connectionbuffersize"></a>connectionBufferSize  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O tamanho do buffer usado para transmitir um bloco da mensagem serializada na conexão do cliente ou serviço.  
  
### <a name="hostnamecomparisonmode"></a>hostNameComparisonMode  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Um valor que indica se o nome do host é usado para acessar o serviço ao fazer correspondência no URI.  
  
### <a name="maxbuffersize"></a>maxBufferSize  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O tamanho máximo do buffer a ser usado.  
  
### <a name="maxoutputdelay"></a>maxOutputDelay  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 O intervalo máximo de tempo que uma parte de uma mensagem ou uma mensagem completa pode permanecer armazenada em buffer na memória antes de ser enviada.  
  
### <a name="maxpendingaccepts"></a>MaxPendingAccepts  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O número máximo de pendente assíncrono aceita threads que estão disponíveis para processar conexões de entrada no serviço.  
  
### <a name="maxpendingconnections"></a>MaxPendingConnections  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O número máximo de conexões pendentes.  
  
### <a name="transfermode"></a>transferMode  
 Tipo de dados: cadeia de caracteres  
  
 Tipo de acesso: somente leitura  
  
 Um valor que especifica se as mensagens são armazenadas em buffer ou transmitidas em fluxo com o transporte orientado à conexão.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>
