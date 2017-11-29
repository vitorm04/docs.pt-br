---
title: 1031 - CompleteFaultWorkItem
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 95f4ccb0-6be4-41f3-9330-fae43165828f
caps.latest.revision: "3"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 260647b56d945600afea5609f06d36385fa66014
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
