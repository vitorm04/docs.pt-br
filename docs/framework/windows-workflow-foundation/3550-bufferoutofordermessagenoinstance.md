---
title: 3550 - BufferOutOfOrderMessageNoInstance
ms.date: 03/30/2017
ms.assetid: 1299d294-99b8-430e-98b1-55f5f17002f3
ms.openlocfilehash: 1af943e23aa643c6614b946175c0b1854a7ceb62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61755578"
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
