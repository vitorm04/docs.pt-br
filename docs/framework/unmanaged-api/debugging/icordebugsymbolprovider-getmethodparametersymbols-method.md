---
title: ICorDebugSymbolProvider::GetMethodParameterSymbols Method
ms.date: 03/30/2017
ms.assetid: 58b7c0b9-f6ad-4b49-b92d-0e421cfd0ec6
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 98efd1446c88c3a6c004b5a3254c9db835a43804
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61953368"
---
# <a name="icordebugsymbolprovidergetmethodparametersymbols-method"></a>ICorDebugSymbolProvider::GetMethodParameterSymbols Method
Obtém os símbolos de parâmetro do método dado o endereço virtual relativo (RVA) desse método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetMethodParameterSymbols(  
   [in] ULONG32 nativeRVA,  
   [in] ULONG32 cRequestedSymbols,  
   [out] ULONG32 *pcFetchedSymbols,  
   [out, size_is(cRequestedSymbols), length_is(*pcFetchedSymbols)] ICorDebugVariableSymbol *pSymbols[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `nativeRVA`  
 [in] O endereço de virtual relativo nativo do método.  
  
 `cRequestedSymbols`  
 [in] O número de símbolos locais solicitado.  
  
 `pcFetchedSymbols`  
 [out] Um ponteiro para o número de símbolos recuperados pelo método.  
  
 `pcFetchedSymbols`  
 [out] Um ponteiro para um [ICorDebugVariableSymbol](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablesymbol-interface.md) matriz que contém símbolos de locais do método.  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Método GetMethodLocalSymbols](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodlocalsymbols-method.md)
- [Interface ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
