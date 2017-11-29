---
title: 2577 - TryCatchExceptionDuringCancelation
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 35ee9f55-227f-4566-bcb4-4c7c75dea85b
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2a4bc0d9ab45fe8e2f025c651fce137d6a4255bc
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="2577---trycatchexceptionduringcancelation"></a>2577 - TryCatchExceptionDuringCancelation
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|2577|  
|Palavras-chave|WFActivities|  
|Nível|Aviso|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração|  
  
## <a name="description"></a>Descrição  
 Indica que uma atividade filho de atividade de TryCatch apresentou uma exceção durante o cancelar.  
  
## <a name="message"></a>Mensagem  
 Uma atividade filho da atividade “%1 " de TryCatch apresentou uma exceção durante o cancelar.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|DisplayName|xs:string|O nome para exibição de atividade.|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
