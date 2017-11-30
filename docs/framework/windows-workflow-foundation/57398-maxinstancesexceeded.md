---
title: 57398 - MaxInstancesExceeded
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: f943d209-dfeb-43e5-b572-c9a06217936e
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 7417d2e0e850017e65910be32e7449255f0761c3
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="57398---maxinstancesexceeded"></a>57398 - MaxInstancesExceeded
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|57398|  
|Palavras-chave|WFServices|  
|Nível|Aviso|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Indica que o sistema/o limite definido para o regulador de pressão “MaxConcurrentInstances”.  
  
## <a name="message"></a>Mensagem  
 O sistema atingiu o limite definido para o acelerador 'MaxConcurrentInstances'. O limite para este regulador de pressão foi definido como %1. O valor do acelerador pode ser alterado pela modificação do atributo 'maxConcurrentInstances' no elemento serviceThrottle ou modificando-se a propriedade 'MaxConcurrentInstances' no comportamento ServiceThrottlingBehavior.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|Nome|xs:string|O nome do item.|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
