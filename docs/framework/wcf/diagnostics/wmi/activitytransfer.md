---
title: ActivityTransfer
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: fc40ef17-2a92-4ce2-853c-6ba8e5d571f3
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: acbc346da940caf933868a03295744132bda4733
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
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
