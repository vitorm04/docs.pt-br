---
title: 'Método ICorDebugVariableSymbol:: GetValue'
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
ms.openlocfilehash: 2dc074384d209d0740a1fb0a9a16d96ff355f02b
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790881"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a>Método ICorDebugVariableSymbol:: GetValue
Obtém o valor de uma variável como uma matriz de bytes.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `offset`  
 no O deslocamento inicial na variável a partir da qual o valor deve ser lido. Esse parâmetro é usado ao ler campos de membro em um objeto.  
  
 `cbContext`  
 no O tamanho em bytes do argumento `context`.  
  
 `context`  
 no O contexto de thread usado para ler o valor.  
  
 `cbValue`  
 no O tamanho em bytes do buffer de `pValue`.  
  
 `pcbValue`  
 fora O número de bytes realmente gravados no buffer de `pValue`.  
  
 `pValue`  
 fora Uma matriz de bytes que contém o valor da variável.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
