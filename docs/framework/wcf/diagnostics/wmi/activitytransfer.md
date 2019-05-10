---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 6237d65d6964a4ebca34af895158c83239641593
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/28/2019
ms.locfileid: "64662817"
---
# <a name="activitytransfer"></a>ActivityTransfer
Evento de transferência de atividade  
  
## <a name="syntax"></a>Sintaxe  
  
```csharp
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe ActivityTransfer não define quaisquer métodos.  
  
## <a name="properties"></a>Propriedades  
 A classe ActivityTransfer tem as seguintes propriedades:  
  
### <a name="activityid"></a>ActivityID  
  
- Tipo de dados: objeto  
    Tipo de acesso: Somente leitura  
  
- ID da Atividade  
  
### <a name="relatedactivityid"></a>RelatedActivityID  
  
- Tipo de dados: objeto  
    Tipo de acesso: Somente leitura  
  
- ID da atividade relacionada  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido no root\ServiceModel.|
