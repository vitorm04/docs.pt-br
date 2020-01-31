---
title: 'Método ICorDebugSymbolProvider:: GetMethodProps'
ms.date: 03/30/2017
ms.assetid: 8f836b80-b7a5-460b-bf76-5f0e45652aea
ms.openlocfilehash: 58642d0a9b1cfe1fd969f39fa7e5ab22a8dbfa05
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76791579"
---
# <a name="icordebugsymbolprovidergetmethodprops-method"></a>Método ICorDebugSymbolProvider:: GetMethodProps
Retorna informações sobre as propriedades do método, como o token de metadados do método e informações sobre seus parâmetros genéricos, considerando um endereço virtual relativo (RVA) nesse método.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetMethodProps(  
   [in]  ULONG32 codeRva,  
   [out] mdToken *pMethodToken,  
   [out] ULONG32 *pcGenericParams,  
   [in]  ULONG32 cbSignature,  
   [out] ULONG32 *pcbSignature,  
   [out, size_is(cbSignature), length_is(*pcbSignature)] BYTE signature[]  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `codeRVA`  
 no Um endereço virtual relativo no método sobre quais informações serão recuperadas.  
  
 `pMethodToken`  
 fora Um ponteiro para o token de metadados do método.  
  
 `pcGenericParams`  
 fora Um ponteiro para o número de parâmetros genéricos associados a este método.  
  
 `cbSignature`  
 no O tamanho da matriz de `signature`. Consulte a seção Comentários.  
  
 `pcbSignature`  
 fora Um ponteiro para o tamanho da matriz de `signature` retornada.  
  
 `signature`  
 fora Um buffer que contém as assinaturas TypeSpec de todos os parâmetros genéricos.  
  
## <a name="remarks"></a>Comentários  
 Para obter o tamanho necessário da matriz de `signature` do método, defina o argumento `cbSignature` como 0 e `signature` como **nulo**. Quando o método retornar, `pcbSignature` conterá o número de bytes necessários para a matriz `signature`.  
  
> [!NOTE]
> Esse método está disponível somente com .NET Native.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Método GetTypeProps](icordebugsymbolprovider-gettypeprops-method.md)
- [Interface ICorDebugSymbolProvider](icordebugsymbolprovider-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
