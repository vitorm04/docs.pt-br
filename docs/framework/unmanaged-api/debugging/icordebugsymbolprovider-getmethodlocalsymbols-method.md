---
title: 'Método ICorDebugSymbolProvider:: GetMethodLocalSymbols'
ms.date: 03/30/2017
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
ms.openlocfilehash: 7e9aa01a3fa1c90b0ab4f85970c4eb294b9a4904
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379605"
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a>Método ICorDebugSymbolProvider:: GetMethodLocalSymbols
Obtém os símbolos locais de um método de acordo com o endereço virtual relativo (RVA) desse método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `nativeRVA`  
 no O endereço virtual relativo nativo do método.  
  
 `cRequestedSymbols`  
 no O número de símbolos locais solicitados.  
  
 `pcFetchedSymbols`  
 fora Um ponteiro para o número de símbolos recuperados pelo método.  
  
 `pcFetchedSymbols`  
 fora Um ponteiro para uma matriz [ICorDebugVariableSymbol](icordebugvariablesymbol-interface.md) que contém os símbolos locais do método.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Método GetMethodParameterSymbols](icordebugsymbolprovider-getmethodparametersymbols-method.md)
- [Interface ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
