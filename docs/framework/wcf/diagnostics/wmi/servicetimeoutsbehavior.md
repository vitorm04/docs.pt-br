---
title: ServiceTimeoutsBehavior
ms.date: 03/30/2017
ms.assetid: 4412525d-a3cc-4eae-b3e8-a50ce766d09d
ms.openlocfilehash: 7531cf27aec0ea9a71ee7b1906e8f7cee151695f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="servicetimeoutsbehavior"></a>ServiceTimeoutsBehavior
ServiceTimeoutsBehavior  
  
## <a name="syntax"></a>Sintaxe  
  
```  
class ServiceTimeoutsBehavior : Behavior  
{  
  datetime TransactionTimeout;  
};  
```  
  
## <a name="methods"></a>Métodos  
 A classe ServiceTimeoutsBehavior não define nenhum método.  
  
## <a name="properties"></a>Propriedades  
 A classe ServiceTimeoutsBehavior tem a seguinte propriedade:  
  
### <a name="transactiontimeout"></a>TransactionTimeout  
 Tipo de dados: datetime  
  
 Tipo de acesso: somente leitura  
  
 O período no qual uma transação deve ser concluída.  
  
## <a name="requirements"></a>Requisitos  
  
|MOF|Declarado em Servicemodel.mof.|  
|---------|-----------------------------------|  
|Namespace|Definido em root\ServiceModel|  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.Configuration.ServiceTimeoutsElement>
