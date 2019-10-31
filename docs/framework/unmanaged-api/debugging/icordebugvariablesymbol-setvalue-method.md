---
title: 'Método ICorDebugVariableSymbol:: SetValue'
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
ms.openlocfilehash: fbd3d617e3448730241ccfda7bd26b65d17b694d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121888"
---
# <a name="icordebugvariablesymbolsetvalue-method"></a>Método ICorDebugVariableSymbol:: SetValue
Atribui o valor de uma matriz de bytes a uma variável.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `offset`  
 no O deslocamento inicial na variável na qual definir o valor. Esse parâmetro é usado ao gravar em campos de membro em um objeto.  
  
 `threadID`  
 no O identificador de thread do thread cujo contexto deve ser atualizado para refletir o novo valor.  
  
 `cbContext`  
 no O tamanho em bytes do contexto do thread.  
  
 `context`  
 no O contexto de thread usado para gravar o valor.  
  
 `cbValue`  
 no O tamanho em bytes do buffer de `pValue`.  
  
 `pValue`  
 no O buffer que contém o valor a ser definido.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
