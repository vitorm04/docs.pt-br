---
title: 1036 - RuntimeTransactionCompletionRequested
ms.date: 03/30/2017
ms.assetid: d36b9f44-7c0f-4083-9d3a-9034dd2b98de
ms.openlocfilehash: 649ba542a9ed2f330ac71e447602d637530dc601
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924833"
---
# <a name="1036---runtimetransactioncompletionrequested"></a>1036 - RuntimeTransactionCompletionRequested
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|1036|  
|Palavras-chave|WFRuntime|  
|Nível|Detalhado|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração|  
  
## <a name="description"></a>Descrição  
 Indica que uma atividade agendou a conclusão de transação de tempo de execução.  
  
## <a name="message"></a>Mensagem  
 Atividade “%1", DisplayName: “%2", InstanceId: “%3 " agendaram a conclusão de transação de tempo de execução.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|Atividade|xs:string|O nome do tipo de atividade.|  
|DisplayName|xs:string|O nome para exibição de atividade.|  
|InstanceId|xs:string|A identificação de instância de atividade.|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
