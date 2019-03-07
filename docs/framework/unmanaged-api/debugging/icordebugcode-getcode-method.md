---
title: Método ICorDebugCode::GetCode
ms.date: 03/30/2017
api_name:
- ICorDebugCode.GetCode
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugCode::GetCode
helpviewer_keywords:
- ICorDebugCode::GetCode method [.NET Framework debugging]
- GetCode method, ICorDebugCode interface [.NET Framework debugging]
ms.assetid: 7137e3d1-1dad-48d8-8c37-16ac816534d3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b69970d50652da203ecf1ae6fe8d604ccee06cf
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57483569"
---
# <a name="icordebugcodegetcode-method"></a>Método ICorDebugCode::GetCode
Obtém todo o código para a função especificada, formatada para desmontagem. Esse método foi preterido no .NET Framework versão 2.0. Use [ICorDebugCode2::GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md) em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetCode (  
    [in] ULONG32     startOffset,   
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `startOffset`  
 [in] O deslocamento do início da função.  
  
 `endOffset`  
 [in] O deslocamento do final da função.  
  
 `cBufferAlloc`  
 [in] O tamanho do `buffer` de matriz no qual o código será retornado.  
  
 `buffer`  
 [out] A matriz na qual o código será retornado.  
  
 `pcBufferSize`  
 [out] O número de bytes retornados.  
  
## <a name="remarks"></a>Comentários  
 Se o código da função foi dividido em várias partes, elas são concatenadas em ordem crescente de deslocamento nativo. Limites de instrução não são verificados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** 1.1, 1.0  
  
## <a name="see-also"></a>Consulte também
- [Método GetCodeChunks](../../../../docs/framework/unmanaged-api/debugging/icordebugcode2-getcodechunks-method.md)

