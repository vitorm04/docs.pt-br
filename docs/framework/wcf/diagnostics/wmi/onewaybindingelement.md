---
title: OneWayBindingElement
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: abaacfb6541d41019a8d0cd6df53913c6b7911f2
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
---
# <a name="onewaybindingelement"></a>OneWayBindingElement
OneWayBindingElement  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe OneWayBindingElement não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe OneWayBindingElement tem as seguintes propriedades:  
  
### <a name="channelpoolsettings"></a>ChannelPoolSettings  
 Tipo de dados: ChannelPoolSettings  
  
 Tipo de acesso: somente leitura  
  
 As configurações de pool do canal.  
  
### <a name="maxacceptedchannels"></a>MaxAcceptedChannels  
 Tipo de dados: sint32  
  
 Tipo de acesso: somente leitura  
  
 O número máximo de canais aceitos.  
  
### <a name="packetroutable"></a>PacketRoutable  
 Tipo de dados: boolean  
  
 Tipo de acesso: somente leitura  
  
 Um valor que indica se o pacote é roteável.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
