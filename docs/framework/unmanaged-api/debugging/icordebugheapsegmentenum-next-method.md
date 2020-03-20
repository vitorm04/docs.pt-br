---
title: Método ICorDebugHeapSegmentEnum::Next
ms.date: 03/30/2017
api_name:
- Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapSegmentEnum::Next
helpviewer_keywords:
- ICorDebugHeapSegmentEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugHeapSegmentEnum interface [.NET Framework debugging]
ms.assetid: 51625fd0-7399-49c7-b22b-5dfb05451fe6
topic_type:
- apiref
ms.openlocfilehash: 8a267ec7123edb73ad51f0781a78344119ec6f21
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178892"
---
# <a name="icordebugheapsegmentenumnext-method"></a>Método ICorDebugHeapSegmentEnum::Next
Obtém o número especificado de [COR_HEAPOBJECT](cor-heapobject-structure.md) instâncias que contêm informações sobre regiões de memória do heap gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT Next(  
    [in] ULONG celt,    [out, size_is(celt), length_is(*pceltFetched)] COR_SEGMENT segments[],
    [out] ULONG *pceltFetched  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 Celt  
 [em] O número de segmentos a serem recuperados.  
  
 segmentos  
 [fora] Uma matriz de ponteiros, cada um dos quais aponta para um objeto [COR_HEAPOBJECT](cor-heapobject-structure.md) que fornece informações sobre uma região de memória no heap gerenciado.  
  
 pceltFetched  
 [fora] Um ponteiro para o número de `segments` [objetos COR_HEAPOBJECT](cor-heapobject-structure.md) realmente retornado em . Este valor `null` pode `celt` ser se for 1.  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Interface ICorDebugHeapSegmentEnum](icordebugheapsegmentenum-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
