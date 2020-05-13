---
title: 'Método ICorDebugSymbolProvider:: GetTypeProps'
ms.date: 03/30/2017
ms.assetid: 35ac4140-91ea-4c77-b1c4-1daf41986ca5
ms.openlocfilehash: e116716284bb2081edb669e7fc9083cde10f6457
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379356"
---
# <a name="icordebugsymbolprovidergettypeprops-method"></a>Método ICorDebugSymbolProvider:: GetTypeProps
Retorna informações sobre as propriedades de um tipo, como o número de assinatura de seus parâmetros genéricos, considerando um endereço virtual relativo (RVA) em uma vtable.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetTypeProps(  
   [in]  ULONG32 vtableRva,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `tableRva`  
 no Um RVA (endereço virtual relativo) em uma vtable.  
  
 `cbSignature`  
 no O tamanho da `signature` matriz. Consulte a seção Comentários.  
  
 `pcbSignature`  
 fora fora Um ponteiro para o tamanho da matriz retornada `signature` .  
  
 `signature`  
 fora Um buffer que contém as assinaturas TypeSpec de todos os parâmetros genéricos.  
  
## <a name="remarks"></a>Comentários  
 Para obter o tamanho necessário da matriz do tipo `signature` , defina o `cbSignature` argumento como 0 e `signature` como **nulo**. Quando o método retornar, `pcbSignature` conterá o número de bytes necessários para a `signature` matriz.  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Método GetMethodProps](icordebugsymbolprovider-getmethodprops-method.md)
- [Interface ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
