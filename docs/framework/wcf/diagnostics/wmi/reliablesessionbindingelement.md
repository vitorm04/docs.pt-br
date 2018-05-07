---
title: ReliableSessionBindingElement
ms.date: 03/30/2017
ms.assetid: effda125-b8d3-4de6-8c0e-f59f5ea8f6eb
ms.openlocfilehash: 2f04e6794342d7bd0acd51481efcbeceb04fd459
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="reliablesessionbindingelement"></a>ReliableSessionBindingElement
ReliableSessionBindingElement  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class ReliableSessionBindingElement : BindingElement  
{  
  datetime AcknowledgementInterval;  
  boolean FlowControlEnabled;  
  datetime InactivityTimeout;  
  sint32 MaxPendingChannels;  
  sint32 MaxRetryCount;  
  sint32 MaxTransferWindowSize;  
  boolean Ordered;  
  integer ReliableMessagingVersion;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe ReliableSessionBindingElement não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe ReliableSessionBindingElement tem as seguintes propriedades:  
  
### <a name="acknowledgementinterval"></a>AcknowledgementInterval  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 O intervalo de tempo que um destino aguarda antes de enviar uma confirmação para a origem da mensagem em canais confiáveis que são criados pela fábrica.  
  
### <a name="flowcontrolenabled"></a>FlowControlEnabled  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor booleano que especifica se o controle de fluxo está habilitado.  
  
### <a name="inactivitytimeout"></a>InactivityTimeout  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 Especifica a duração máxima que o canal vai permitir que a outra parte da comunicação para não enviar nenhuma mensagem antes de haver falha no canal.  
  
### <a name="maxpendingchannels"></a>MaxPendingChannels  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O número máximo de canais que podem aguardar para serem aceitos no ouvinte.  
  
### <a name="maxretrycount"></a>MaxRetryCount  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O número máximo de vezes que um canal confiável tenta retransmitir uma mensagem não recebeu confirmação, chamando `Send` em seu canal subjacente.  
  
### <a name="maxtransferwindowsize"></a>MaxTransferWindowSize  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O tamanho da janela de transferência máxima para a sessão confiável.  
  
### <a name="ordered"></a>Ordenada  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor booleano que especifica se as mensagens são garantidas de chegar na ordem em que foram enviadas.  
  
### <a name="reliablemessagingversion"></a>ReliableMessagingVersion  
 Tipo de dados: número inteiro  
  
 Tipo de acesso: somente leitura  
  
 Um inteiro que especifica a versão do protocolo WS-ReliableMessaging usada na sessão confiável.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
