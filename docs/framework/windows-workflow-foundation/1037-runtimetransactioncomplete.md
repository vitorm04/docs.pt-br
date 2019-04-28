---
title: 1037 - RuntimeTransactionComplete
ms.date: 03/30/2017
ms.assetid: 2c8c31e0-42a9-4f46-865b-2da9ab16a0ba
ms.openlocfilehash: 7a94c917157904c5cb84105c41842657a534c973
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924287"
---
# <a name="1037---runtimetransactioncomplete"></a>1037 - RuntimeTransactionComplete
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|1037|  
|Palavras-chave|WFRuntime|  
|Nível|Detalhado|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração|  
  
## <a name="description"></a>Descrição  
 Indica que a transação de tempo de execução terminado.  
  
## <a name="message"></a>Mensagem  
 A transação de tempo de execução terminou com o estado “%1 ".  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|Estado|xs:string|O estado de transação.|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
