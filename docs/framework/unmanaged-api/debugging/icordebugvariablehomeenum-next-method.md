---
title: 'Método ICorDebugVariableHomeEnum:: Next'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type:
- apiref
ms.openlocfilehash: 9c2c16789fb61099c9b7c58154810739d225af1f
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121929"
---
# <a name="icordebugvariablehomeenumnext-method"></a>Método ICorDebugVariableHomeEnum:: Next
Obtém o número especificado de instâncias [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) que contêm informações sobre as variáveis e os argumentos locais em uma função.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `celt`  
 no O número de objetos a serem recuperados.  
  
 `homes`  
 Uma matriz de ponteiros, cada um dos quais aponta para um objeto [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) que fornece informações sobre uma variável local ou um argumento de uma função.  
  
 `pceltFetched`  
 fora O número de instâncias realmente retornadas em objetos.  
  
## <a name="return-value"></a>Valor retornado  
 O método retorna os valores a seguir.  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|O método foi concluído com êxito.|  
|`S_FALSE`|O número real de instâncias recuperadas, conforme refletido em `pceltFetched`, é menor que o número de instâncias solicitadas.|  
  
## <a name="remarks"></a>Comentários  
 O método [ICorDebugVariableHomeEnum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) recupera um máximo de `celt` objetos começando na posição atual do enumerador. Quando o método retorna, `pceltFetched` contém o número real de objetos recuperados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugVariableHomeEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)
- [Interface ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
