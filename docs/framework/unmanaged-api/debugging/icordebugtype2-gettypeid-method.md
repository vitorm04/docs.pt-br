---
title: Método ICorDebugType2::GetTypeID
ms.date: 03/30/2017
api_name:
- ICorDebugType2.GetTypeID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugType::GetTypeID
helpviewer_keywords:
- GetTypeID method, ICorDebugType2 interface [.NET Framework debugging]
- ICorDebugType2.GetTypeID method [.NET Framework debugging]
ms.assetid: 0b933686-226e-4373-92b7-fac579ee7b1a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 54b3f8e931507e53809a2419ab7f06e63eb70c10
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57497633"
---
# <a name="icordebugtype2gettypeid-method"></a>Método ICorDebugType2::GetTypeID
Obtém uma [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) para esse tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `id`  
 [out] Um ponteiro para o [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) para este ICorDebugType.  
  
## <a name="return-value"></a>Valor de retorno  
 O valor retornado é `S_OK` em caso de êxito, ou um código de falha `HRESULT` em caso de falha. O `HRESULT` códigos incluem o seguinte:  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|`S_OK`|O método foi bem-sucedido. O método recuperou válida [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md).|  
|`CORDBG_E_CLASS_NOT_LOADED`|O tipo não foi carregado.|  
|`CORDBG_E_UNSUPPORTED`|Não há suporte para o tipo.|  
  
## <a name="remarks"></a>Comentários  
 Esse método fornece um mapeamento de ICorDebugType, que representa um tipo que pode, ou pode não ter sido carregado no tempo de execução, como uma [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), que serve como opaco identificador que identifica um tipo carregado no tempo de execução.  
  
 Quando o tipo que representa o ICorDebugType ainda não foi carregado, esse método retornará `CORDBG_E_CLASS_NOT_LOADED`.  Se não há suporte para o tipo, ele retorna `CORDBG_E_UNSUPPORTED`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorDebugType2](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)
