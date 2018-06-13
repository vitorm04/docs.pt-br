---
title: Estrutura StackOverflowInfo
ms.date: 03/30/2017
api_name:
- StackOverflowInfo
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- StackOverflowInfo
helpviewer_keywords:
- StackOverflowInfo structure [.NET Framework hosting]
ms.assetid: 519389f2-0217-436c-99d4-93a76ebce5b5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b1e652588d27521a04015228e86eb9af9c53346e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33440808"
---
# <a name="stackoverflowinfo-structure"></a>Estrutura StackOverflowInfo
Armazena o tipo de estouro ocorreu e informações sobre a exceção que foi gerada devido ao estouro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
typedef struct _StackOverflowInfo {  
    StackOverflowType   soType;  
    EXCEPTION_POINTERS  *pExceptionInfo;  
} StackOverflowInfo;  
```  
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`soType`|Um valor de [StackOverflowType](../../../../docs/framework/unmanaged-api/hosting/stackoverflowtype-enumeration.md) enumeração que especifica o tipo de estouro.|  
|`pExceptionInfo`|Um ponteiro para um Win32 `EXCEPTION_POINTERS` objeto, que contém um registro de exceção com uma descrição independente de máquina de uma exceção e um registro de contexto com uma descrição de máquina dependente de contexto do processador no momento da exceção.|  
  
## <a name="remarks"></a>Comentários  
 Um `StackOverflowInfo` objeto é passado para o [Iactiononclrevent](../../../../docs/framework/unmanaged-api/hosting/iactiononclrevent-onevent-method.md) método `Event_StackOverflow` eventos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MSCorEE.idl  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Estruturas de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-structures.md)
