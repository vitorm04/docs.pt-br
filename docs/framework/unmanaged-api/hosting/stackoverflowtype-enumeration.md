---
title: Enumeração StackOverflowType
ms.date: 03/30/2017
api_name:
- StackOverflowType
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowType
helpviewer_keywords:
- StackOverflowType enumeration [.NET Framework hosting]
ms.assetid: dab648ad-972b-479c-b129-b4c1dcbd932e
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9e888b2359336c68ea6fdf52f798145fda12002e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440863"
---
# <a name="stackoverflowtype-enumeration"></a>Enumeração StackOverflowType
Contém valores que indicam a causa subjacente de um evento de estouro de pilha.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef enum {  
    SO_Managed,  
    SO_ClrEngine,  
    SO_Other  
} StackOverflowType;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`SO_ClrEngine`|O estouro da pilha foi causado pelo mecanismo de execução.|  
|`SO_Managed`|O estouro da pilha foi causado pelo código gerenciado.|  
|`SO_Other`|O estouro da pilha foi causado pelo código não gerenciado.|  
  
## <a name="remarks"></a>Comentários  
 Essas informações são passadas para o host por meio de uma chamada para o [Iactiononclrevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.h  
  
 **Biblioteca:** MSCorEE.dll  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
