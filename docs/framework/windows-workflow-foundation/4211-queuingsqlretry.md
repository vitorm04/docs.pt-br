---
title: 4211 - QueuingSqlRetry
ms.date: 03/30/2017
ms.assetid: df569f88-c86b-4503-840d-1399b67f4df7
ms.openlocfilehash: ede74eb642c5c2c79b90cf1458db424d9f83b087
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61774238"
---
# <a name="4211---queuingsqlretry"></a>4211 - QueuingSqlRetry
## <a name="properties"></a>Propriedades  
  
|||  
|-|-|  
|ID|4211|  
|Palavras-chave|WFInstanceStore|  
|Nível|Aviso|  
|Canal|Os aplicativos de servidor de Microsoft-Windows- aplicativo/depuração|  
  
## <a name="description"></a>Descrição  
 Indica a nova tentativa de enfileiramento SQL.  
  
## <a name="message"></a>Mensagem  
 Nova tentativa SQL fila com atraso %1 milissegundos.  
  
## <a name="details"></a>Detalhes  
  
|Nome do item de dados|Tipo de item de dados|Descrição|  
|--------------------|--------------------|-----------------|  
|Atraso|xs:string|O atraso entre o tenta.|  
|AppDomain|xs:string|A cadeia de caracteres retornada por AppDomain.CurrentDomain.FriendlyName.|
