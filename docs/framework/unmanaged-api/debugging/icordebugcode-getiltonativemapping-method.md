---
title: Método ICorDebugCode::GetILToNativeMapping
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetILToNativeMapping
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetILToNativeMapping
helpviewer_keywords:
- GetILToNativeMapping method, ICorDebugCode interface [.NET Framework debugging]
- ICorDebugCode::GetILToNativeMapping method [.NET Framework debugging]
ms.assetid: a8ecd8c8-9627-4356-9c6f-bd05e24637c0
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 13ec60999db88b9d7191a3866fcebe8098b4edee
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411380"
---
# <a name="icordebugcodegetiltonativemapping-method"></a>Método ICorDebugCode::GetILToNativeMapping
Obtém uma matriz de instâncias de "COR_DEBUG_IL_TO_NATIVE_MAP" que representam os mapeamentos da Microsoft intermediate language (MSIL) desloca para deslocamentos nativo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetILToNativeMapping (  
    [in]  ULONG32    cMap,  
    [out] ULONG32    *pcMap,  
    [out, size_is(cMap), length_is(*pcMap)]  
        COR_DEBUG_IL_TO_NATIVE_MAP map[]  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `cMap`  
 [in] O tamanho do `map` matriz.  
  
 `pcMap`  
 [out] Um ponteiro para o número real de elementos retornados no `map` matriz.  
  
 `map`  
 [out] Uma matriz de `COR_DEBUG_IL_TO_NATIVE_MAP` estruturas, cada um deles representa um mapeamento de um deslocamento MSIL para um deslocamento nativo.  
  
 Não há nenhuma ordem para a matriz de elementos retornados.  
  
## <a name="remarks"></a>Comentários  
 O `GetILToNativeMapping` método retorna resultados significativos somente se essa instância de "ICorDebugCode" representa o código nativo que foi just-in-time (JIT) compilado a partir de código MSIL.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface1 ICorDebugCode](../../../../docs/framework/unmanaged-api/debugging/icordebugcode-interface1.md)
