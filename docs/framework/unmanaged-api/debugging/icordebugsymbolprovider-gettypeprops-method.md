---
title: Método ICorDebugSymbolProvider::GetTypeProps
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e21273506e91c5ab69b1b0b4a52d6c0f72692dab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54712766"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a>Método ICorDebugSymbolProvider::GetTypeProps
Retorna informações sobre propriedades de um tipo, como o número de assinatura de seus parâmetros genéricos, considerando um endereço virtual relativo (RVA) em uma vtable.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `tableRva`  
 [in] Um endereço virtual relativo (RVA) em uma vtable.  
  
 `cbSignature`  
 [in] O tamanho do `signature` matriz. Consulte a seção Comentários.  
  
 `pcbSignature`  
 [out] [out] Um ponteiro para o tamanho de retornado `signature` matriz.  
  
 `signature`  
 [out] Um buffer que contém as assinaturas de typespec de todos os parâmetros genéricos.  
  
## <a name="remarks"></a>Comentários  
 Para obter o tamanho necessário do tipo de `signature` matriz, defina a `cbSignature` argumento como 0 e `signature` à **nulo**. Quando o método retorna, `pcbSignature` conterá o número de bytes necessários para o `signature` matriz.  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Método GetMethodProps](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-getmethodprops-method.md)
- [Interface ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
