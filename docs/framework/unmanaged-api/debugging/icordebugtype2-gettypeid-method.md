---
title: 'Método ICorDebugType2:: GetTypeId'
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
ms.openlocfilehash: 944313893d88b8eff97291d2517e4863a5ae958a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73092756"
---
# <a name="icordebugtype2gettypeid-method"></a>Método ICorDebugType2:: GetTypeId
Obtém um [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) para este tipo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetTypeID(  
    ([out] COR_TYPEID *id  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `id`  
 fora Um ponteiro para o [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) para este ICorDebugType.  
  
## <a name="return-value"></a>Valor retornado  
 O valor retornado é `S_OK` em caso de êxito, ou um código de falha `HRESULT` em caso de falha. Os códigos de `HRESULT` incluem o seguinte:  
  
|Código de retorno|Descrição|  
|-----------------|-----------------|  
|`S_OK`|O método foi bem-sucedido. O método recuperou um [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md)válido.|  
|`CORDBG_E_CLASS_NOT_LOADED`|O tipo não foi carregado.|  
|`CORDBG_E_UNSUPPORTED`|Não há suporte para o tipo.|  
  
## <a name="remarks"></a>Comentários  
 Esse método fornece um mapeamento do ICorDebugType, que representa um tipo que pode ou não ter sido carregado no tempo de execução, para um [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md), que serve como um identificador opaco que identifica um tipo carregado no tempo de execução.  
  
 Quando o tipo que o ICorDebugType representa ainda não foi carregado, esse método retorna `CORDBG_E_CLASS_NOT_LOADED`.  Se não houver suporte para o tipo, ele retornará `CORDBG_E_UNSUPPORTED`.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugType2](../../../../docs/framework/unmanaged-api/debugging/icordebugtype2-interface.md)
