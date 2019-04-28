---
title: 1124 - InvokeMethodIsStatic
ms.date: 03/30/2017
ms.assetid: b9643641-fb52-4fa8-b354-4dd6617d68f6
ms.openlocfilehash: 49a9dec73392681fd4150c611f78399a1e15dd48
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61924053"
---
# <a name="1124---invokemethodisstatic"></a>1124 - InvokeMethodIsStatic
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|1124|  
|Palavras-chave|WFRuntime|  
|Nível|Informações|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração|  
  
## <a name="description"></a>Descrição  
 Durante a etapa de CacheMetadata, a atividade de InvokeMethod indica que o método a ser chamado é estático.  
  
## <a name="message"></a>Mensagem  
 InvokeMethod “%1" - o método é estático.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|InvokeMethod|xs:string|O nome para exibição de atividade de InvokeMethod.|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
