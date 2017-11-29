---
title: 3508 - TrackingProfileNotFound
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4cee3c4a-0490-4c94-aa19-ef7ce7287c02
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: fb5636057193fcfb59e5062f6f3833a62b4f3027
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="3508---trackingprofilenotfound"></a>3508 - TrackingProfileNotFound
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|3508|  
|Palavras-chave|WFServices|  
|Nível|Detalhado|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Indica que um ou TrackingProfile não está localizado no arquivo de configuração ou o ActivityDefinitionId não corresponde ao perfil.  
  
## <a name="message"></a>Mensagem  
 TrackingProfile “%1 " para o ActivityDefinitionId “%2 " não encontrado. O TrackingProfile não é encontrado no arquivo de configuração ou a ActivityDefinitionId não é correspondente.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|TrackingProfile|xs:string|O nome de perfil de rastreamento.|  
|ActivityDefinitionId|xs:string|A identificação da definição de atividades|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
