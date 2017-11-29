---
title: 3552 - MaxPendingMessagesPerChannelExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc8309d9-eb3a-4636-a6f0-dd0018c1361d
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 5ba5e4aa8e1338321838e40db7d976107315ef64
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
