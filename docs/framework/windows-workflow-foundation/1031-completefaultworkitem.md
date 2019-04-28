---
title: 1031 - CompleteFaultWorkItem
ms.date: 03/30/2017
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
ms.openlocfilehash: cdcbe516fc8ba7440b3d109a5e5cadc105ecee9f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62008792"
---
# <a name="1031---completefaultworkitem"></a>1031 - CompleteFaultWorkItem
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|1031|  
|Palavras-chave|WFRuntime|  
|Nível|Detalhado|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração|  
  
## <a name="description"></a>Descrição  
 Indica que um FaultWorkItem terminado.  
  
## <a name="message"></a>Mensagem  
 Um FaultWorkItem concluiu para atividades “%1 ", DisplayName: “%2", InstanceId: “%3". A exceção é propagada de atividade “%4 ", DisplayName: “%5", InstanceId: “%6".  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|FaultActivity|xs:string|O nome do tipo de atividade de falha.|  
|FaultActivityDisplayName|xs:string|O nome para exibição de atividade de falha.|  
|FaultActivityInstanceId|xs:string|A identificação de instância de atividade de falha.|  
|ExceptionActivity|xs:string|O nome do tipo de atividade que apresentou a exceção.|  
|ExceptionActivityDisplayName|xs:string|O nome para exibição de atividade que apresentou a exceção.|  
|ExceptionActivityInstanceId|xs:string|A identificação de instância de atividade que apresentou a exceção.|  
|Exceção|xs:string|Os detalhes de exceção para a exceção|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
