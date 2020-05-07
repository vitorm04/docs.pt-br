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
ms.openlocfilehash: 59a497d203d241bbc6e0f884007d4a401c112073
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/07/2020
ms.locfileid: "82893647"
---
# <a name="icordebugcodegetcode-method"></a>Método ICorDebugCode::GetCode
Obtém todo o código para a função especificada, formatado para desmontagem. Esse método foi preterido no .NET Framework versão 2,0. Use [ICorDebugCode2:: GetCodeChunks](icordebugcode2-getcodechunks-method.md) em vez disso.  
  
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
  
## <a name="parameters"></a>Parâmetros  
 `startOffset`  
 no O deslocamento do início da função.  
  
 `endOffset`  
 no O deslocamento do fim da função.  
  
 `cBufferAlloc`  
 no O tamanho da `buffer` matriz na qual o código será retornado.  
  
 `buffer`  
 fora A matriz na qual o código será retornado.  
  
 `pcBufferSize`  
 fora O número de bytes retornados.  
  
## <a name="remarks"></a>Comentários  
 Se o código da função tiver sido dividido em várias partes, eles serão concatenados na ordem de aumento do deslocamento nativo. Os limites de instrução não são verificados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** 1,1, 1,0  
  
## <a name="see-also"></a>Consulte também

- [Método GetCodeChunks](icordebugcode2-getcodechunks-method.md)
