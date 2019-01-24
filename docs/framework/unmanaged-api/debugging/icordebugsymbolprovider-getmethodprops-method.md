---
title: Método ICorDebugSymbolProvider::GetMethodProps
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 487b376b2c8e4738ac4bc4d3c21b07eed62036a7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54635982"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a>Método ICorDebugSymbolProvider::GetMethodProps
Retorna informações sobre as propriedades do método, como o método token de metadados e informações sobre seus parâmetros genéricos, considerando um endereço virtual relativo (RVA) nesse método.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `codeRVA`  
 [in] Um endereço virtual relativo no método sobre quais informações deverá ser recuperado.  
  
 `pMethodToken`  
 [out] Um ponteiro para o token de metadados do método.  
  
 `pcGenericParams`  
 [out] Um ponteiro para o número de parâmetros genéricos associados com esse método.  
  
 `cbSignature`  
 [in] O tamanho do `signature` matriz. Consulte a seção Comentários.  
  
 `pcbSignature`  
 [out] Um ponteiro para o tamanho de retornado `signature` matriz.  
  
 `signature`  
 [out] Um buffer que contém as assinaturas de typespec de todos os parâmetros genéricos.  
  
## <a name="remarks"></a>Comentários  
 Para obter o tamanho necessário do que o método `signature` matriz, defina a `cbSignature` argumento como 0 e `signature` para **nulo**. Quando o método retorna, `pcbSignature` conterá o número de bytes necessários para o `signature` matriz.  
  
> [!NOTE]
>  Esse método só está disponível com o .NET Native.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Método GetTypeProps](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-gettypeprops-method.md)
- [Interface ICorDebugSymbolProvider](../../../../docs/framework/unmanaged-api/debugging/icordebugsymbolprovider-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
