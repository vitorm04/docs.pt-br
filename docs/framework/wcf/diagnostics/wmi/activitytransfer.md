---
title: ActivityTransfer
ms.date: 03/30/2017
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
ms.openlocfilehash: 936e870c1ec991e2e33acf8a08ccc93975989679
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/25/2018
ms.locfileid: "50034411"
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
|Namespace|Definido no root\ServiceModel.|
