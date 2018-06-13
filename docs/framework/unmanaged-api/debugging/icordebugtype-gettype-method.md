---
title: Método ICorDebugType::GetType
ms.date: 03/30/2017
api_name:
- ICorDebugType.GetType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetType
helpviewer_keywords:
- ICorDebugType::GetType method [.NET Framework debugging]
- GetType method, ICorDebugType interface [.NET Framework debugging]
ms.assetid: d6e64534-4d47-4ad0-a340-7590e07e2b4a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d881a1fe3965b6e1d89e6172c887061434cd52ff
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33418712"
---
# <a name="icordebugtypegettype-method"></a>Método ICorDebugType::GetType
Obtém um valor de CorElementType que descreve o tipo nativo do common language runtime (CLR) <xref:System.Type> representado por esse ICorDebugType.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetType (  
    [out] CorElementType   *ty  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `ty`  
 [out] Um ponteiro para um valor de `CorElementType` enumeração que indica o CLR <xref:System.Type> que este `ICorDebugType` representa.  
  
## <a name="remarks"></a>Comentários  
 Se o valor de `ty` é ELEMENT_TYPE_CLASS ou ELEMENT_TYPE_VALUETYPE, o [: Getclass](../../../../docs/framework/unmanaged-api/debugging/icordebugtype-getclass-method.md) método pode ser chamado para obter o tipo instanciado para um tipo genérico; caso contrário, não chame `ICorDebugType::GetClass`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
