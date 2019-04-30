---
title: 401- StopSignPostEvent
ms.date: 03/30/2017
ms.assetid: e033d03a-510d-4300-aa65-ef02cb4807f2
ms.openlocfilehash: 1776252c362feb3c3ebc04651603944040ceee7b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61999746"
---
# <a name="401--stopsignpostevent"></a>401- StopSignPostEvent
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|401|  
|Palavras-chave|Solução de problemas|  
|Nível|Informações|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/analítico|  
  
## <a name="description"></a>Descrição  
 Esse evento marca o final de uma atividade de ponta a ponta. Contém o nome da atividade.  
  
## <a name="message"></a>Mensagem  
 Limite de atividade.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|Dados estendidos|`xs:string`|O nome da atividade.|  
|AppDomain|`xs:string`|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
