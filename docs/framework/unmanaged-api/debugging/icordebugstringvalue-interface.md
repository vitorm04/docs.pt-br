---
title: ICorDebugStringValue Interface1
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue
helpviewer_keywords:
- ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: bf84d0af-53e1-4c04-bc5b-7e5f81ba2cc2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b9160b9013481de294e6c8dd032cfa2d0ebb405d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54596833"
---
# <a name="icordebugstringvalue-interface1"></a>ICorDebugStringValue Interface1
Uma subclasse de ICorDebugHeapValue que se aplica a valores de cadeia de caracteres.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetLength](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|Obtém o número de caracteres na cadeia de caracteres referenciada por este `ICorDebugStringValue`.|  
|[Método GetString](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|Obtém a cadeia de caracteres referenciada por este `ICorDebugStringValue`.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
