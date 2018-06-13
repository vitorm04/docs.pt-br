---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.date: 03/30/2017
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
ms.openlocfilehash: a163ed216cbdfbf2b9d77d25979733d6bdb121d3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33511225"
---
# <a name="3552---maxpendingmessagesperchannelexceeded"></a>3552 - MaxPendingMessagesPerChannelExceeded
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|3552|  
|Palavras-chave|Cota, WFServices|  
|Nível|Aviso|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Indica que o limite de “MaxPendingMessagesPerChannel” de regulador de pressão foi atingido.  
  
## <a name="message"></a>Mensagem  
 Foi atingido o limite 'MaxPendingMessagesPerChannel' de '%1' do acelerador. Para aumentar esse limite, ajuste a propriedade MaxPendingMessagesPerChannel no BufferedReceiveServiceBehavior.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|Limite|xs:string|O limite de regulador de pressão de MaxPendingMessagesPerChannel.|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
