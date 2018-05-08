---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 480670f19407321eb0928d07752936b2ece1f7e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="activitytransfer"></a>ActivityTransfer
Evento de transferência da atividade  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class ActivityTransfer : WSAT_TraceEvent  
{  
  object ActivityID;  
  object RelatedActivityID;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe ActivityTransfer não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe ActivityTransfer tem as seguintes propriedades:  
  
### <a name="activityid"></a>ActivityID  
  
-   Tipo de dados: objeto  
    Tipo de acesso: somente leitura  
  
-   ID da Atividade  
  
### <a name="relatedactivityid"></a>RelatedActivityID  
  
-   Tipo de dados: objeto  
    Tipo de acesso: somente leitura  
  
-   ID da atividade relacionada  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel.|
