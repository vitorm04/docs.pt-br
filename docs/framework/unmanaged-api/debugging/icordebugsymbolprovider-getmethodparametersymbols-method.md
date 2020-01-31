---
title: 'Método ICorDebugSymbolProvider:: GetMethodParameterSymbols'
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
ms.openlocfilehash: a940077e50ff251111ca6eedaee49401775644d3
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791592"
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a>Método ICorDebugSymbolProvider:: GetMethodParameterSymbols
Obtém os símbolos de parâmetro de um método de acordo com o endereço virtual relativo (RVA) desse método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMethodParameterSymbols(  
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
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Método GetMethodLocalSymbols](icordebugsymbolprovider-getmethodlocalsymbols-method.md)
- [Interface ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
