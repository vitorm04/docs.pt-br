---
title: Método ICorDebugSymbolProvider::GetMethodLocalSymbols
ms.date: 03/30/2017
ms.assetid: 8b989e38-e779-49d1-9e90-f1f920484b08
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6c590944c321050c9ecca330a2961a2a7b7f31e6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33420008"
---
# <a name="icordebugsymbolprovidergetmethodlocalsymbols-method"></a>Método ICorDebugSymbolProvider::GetMethodLocalSymbols
Obtém os símbolos do local do método recebe o endereço virtual relativo (RVA) do método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetMethodLocalSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `nativeRVA`  
 [in] O endereço de virtual relativo nativo do método.  
  
 `cRequestedSymbols`  
 [in] O número de símbolos locais solicitado.  
  
 `pcFetchedSymbols`  
 [out] Um ponteiro para o número de símbolos recuperada pelo método.  
  
 `pcFetchedSymbols`  
 [out] Um ponteiro para um [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) matriz que contém os símbolos de local do método.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Método GetMethodParameterSymbols](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodparametersymbols-method.md)  
 [Interface ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
