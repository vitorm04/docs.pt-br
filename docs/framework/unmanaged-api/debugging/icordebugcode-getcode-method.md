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
ms.openlocfilehash: fde76c3b34fcc9f2321f3426d2801b310f681067
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178994"
---
# <a name="icordebugcodegetcode-method"></a>Método ICorDebugCode::GetCode
Obtém todo o código para a função especificada, formatado para desmontagem. Este método foi preterido na versão 2.0 do .NET Framework. Use [ICorDebugCode2::GetCodeChunks](icordebugcode2-getcodechunks-method.md) em vez disso.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCode (  
    [in] ULONG32     startOffset,
    [in] ULONG32     endOffset,  
    [in] ULONG32     cBufferAlloc,  
    [out, size_is(cBufferAlloc),  
        length_is(*pcBufferSize)] BYTE buffer[],  
    [out] ULONG32    *pcBufferSize  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `startOffset`  
 [em] O deslocamento do início da função.  
  
 `endOffset`  
 [em] O deslocamento do fim da função.  
  
 `cBufferAlloc`  
 [em] O tamanho `buffer` da matriz para a qual o código será devolvido.  
  
 `buffer`  
 [fora] A matriz na qual o código será devolvido.  
  
 `pcBufferSize`  
 [fora] O número de bytes retornou.  
  
## <a name="remarks"></a>Comentários  
 Se o código da função foi dividido em vários pedaços, eles são concatenados para aumentar o deslocamento nativo. Os limites da instrução não são verificados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versões:** 1.1, 1.0  
  
## <a name="see-also"></a>Confira também

- [Método GetCodeChunks](icordebugcode2-getcodechunks-method.md)
