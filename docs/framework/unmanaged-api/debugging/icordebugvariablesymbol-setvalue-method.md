---
title: Método ICorDebugVariableSymbol::SetValue
ms.date: 03/30/2017
ms.assetid: 4609418d-71fa-44bc-9618-4d529d25cabb
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1ccdb78e522cb037821135c52bf762707f7de76c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugvariablesymbolsetvalue-method"></a>Método ICorDebugVariableSymbol::SetValue
Atribui o valor de uma matriz de bytes a uma variável.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetValue(  
   [in] ULONG32 offset,  
   [in] DWORD threadID,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [in, size_is(cbValue)] BYTE pValue[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `offset`  
 [in] O deslocamento inicial da variável no qual definir o valor. Esse parâmetro é usado durante a gravação em campos de membro em um objeto.  
  
 `threadID`  
 [in] O identificador de thread do thread cujo contexto deve ser atualizado para refletir o novo valor.  
  
 `cbContext`  
 [in] O tamanho em bytes do contexto do thread.  
  
 `context`  
 [in] O contexto do thread usado para gravar o valor.  
  
 `cbValue`  
 [in] O tamanho em bytes do `pValue` buffer.  
  
 `pValue`  
 [in] O buffer que contém o valor a ser definido.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
