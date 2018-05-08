---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: ee7cfed20234175ba54dd25dbbbab4615c1ed7af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
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
