---
title: OneWayBindingElement
ms.date: 03/30/2017
ms.assetid: 5c7e17c3-39b9-4214-ae08-9e6141734305
ms.openlocfilehash: 34220a3651819978f5f597fdc67d54630ec5e059
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195808"
---
# <a name="onewaybindingelement"></a>OneWayBindingElement
OneWayBindingElement  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class OneWayBindingElement : BindingElement  
{  
  ChannelPoolSettings ChannelPoolSettings;  
  sint32 MaxAcceptedChannels;  
  boolean PacketRoutable;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe OneWayBindingElement não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe OneWayBindingElement tem as seguintes propriedades:  
  
### <a name="channelpoolsettings"></a>ChannelPoolSettings  
 Tipo de dados: ChannelPoolSettings  
  
 Tipo de acesso: somente leitura  
  
 As configurações do pool de canal.  
  
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
|Namespace|Definido no root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Channels.OneWayBindingElement>
