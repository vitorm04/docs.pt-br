---
title: ChannelPoolSettings
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d3f475bd-f780-4bbe-b291-339387322964
caps.latest.revision: "7"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 0a56616e97526b2d410d18d97dc1391c6fc32cc3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="channelpoolsettings"></a>ChannelPoolSettings
ChannelPoolSettings  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class ChannelPoolSettings  
{  
  datetime IdleTimeout;  
  datetime LeaseTimeout;  
  sint32 MaxOutboundChannelsPerEndpoint;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe ChannelPoolSettings não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe ChannelPoolSettings tem as seguintes propriedades:  
  
### <a name="idletimeout"></a>IdleTimeout  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 O tempo máximo que a conexão pode ficar ociosa antes de ser desconectada.  
  
### <a name="leasetimeout"></a>LeaseTimeout  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 O tempo máximo para uma operação de concessão seja concluída antes de atingir o tempo limite.  
  
### <a name="maxoutboundchannelsperendpoint"></a>MaxOutboundChannelsPerEndpoint  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O número máximo de canais de saída para cada ponto de extremidade.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>
