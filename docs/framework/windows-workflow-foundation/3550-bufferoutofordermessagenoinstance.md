---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: ce8b2cd52523d8a2efc94214479ca3c41d2dec4b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="3550---bufferoutofordermessagenoinstance"></a>3550 - BufferOutOfOrderMessageNoInstance
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|3550|  
|Palavras-chave|WFServices|  
|Nível|Informações|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Indica que um armazenados em buffer recebe falhou. A operação será tentada novamente quando a instância do serviço está pronta para processar esta operação específico.  
  
## <a name="message"></a>Mensagem  
 A operação “%1 " não pode ser executada no momento. Outra tentativa será feita quando a instância de serviço estiver pronta para processar esse operação específica.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|OperationName|xs:string|O nome da operação.|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
