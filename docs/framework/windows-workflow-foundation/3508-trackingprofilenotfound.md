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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 346cb98b1285883a9a85f2c7abb6147f42734395
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/02/2017
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
