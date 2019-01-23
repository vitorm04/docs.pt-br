---
title: Método ICorDebugVariableSymbol::GetValue
ms.date: 03/30/2017
ms.assetid: 90abece1-392e-4ade-94a1-30c75b0f7074
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 14412c11010b94fdc462c5aa29e9bc769b2633cc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54496748"
---
# <a name="icordebugvariablesymbolgetvalue-method"></a>Método ICorDebugVariableSymbol::GetValue
Obtém o valor de uma variável como uma matriz de bytes.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetValue(  
   [in] ULONG32 offset,  
   [in] ULONG32 cbContext,  
   [in, size_is(cbContext)] BYTE context[],  
   [in] ULONG32 cbValue,  
   [out] ULONG32 *pcbValue,  
   [out, size_is(cbValue), length_is(*pcbValue)] BYTE pValue[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `offset`  
 [in] O deslocamento inicial da variável da qual ler o valor. Esse parâmetro é usado durante a leitura de campos de membro em um objeto.  
  
 `cbContext`  
 [in] O tamanho em bytes do `context` argumento.  
  
 `context`  
 [in] O contexto do thread usado para ler o valor.  
  
 `cbValue`  
 [in] O tamanho em bytes do `pValue` buffer.  
  
 `pcbValue`  
 [out] O número de bytes realmente gravados a `pValue` buffer.  
  
 `pValue`  
 [out] Uma matriz de bytes que contém o valor da variável.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
