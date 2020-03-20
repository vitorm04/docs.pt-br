---
title: Método ICorDebugProcess2::SetUnmanagedBreakpoint
ms.date: 03/30/2017
api_name:
- ICorDebugProcess2.SetUnmanagedBreakpoint
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint
helpviewer_keywords:
- ICorDebugProcess2::SetUnmanagedBreakpoint method [.NET Framework debugging]
- SetUnmanagedBreakpoint method [.NET Framework debugging]
ms.assetid: 93829d15-d942-4e2d-b7a4-dfc9d7fb96be
topic_type:
- apiref
ms.openlocfilehash: fb8b8f3e29c141e91587a4d0cdc81cdabccdbc9e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178642"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a>Método ICorDebugProcess2::SetUnmanagedBreakpoint
Define um ponto de ruptura não gerenciado no deslocamento de imagem nativo especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
## <a name="parameters"></a>parâmetros  
 `address`  
 [em] Um `CORDB_ADDRESS` objeto que especifica o deslocamento de imagem nativa.  
  
 `bufsize`  
 [em] O tamanho, em bytes, da `buffer` matriz.  
  
 `buffer`  
 [fora] Uma matriz que contém o opcode que é substituído pelo ponto de ruptura.  
  
 `bufLen`  
 [fora] Um ponteiro para o número de bytes retornado na `buffer` matriz.  
  
## <a name="remarks"></a>Comentários  
 Se o deslocamento de imagem nativo estiver dentro do tempo de execução do idioma comum (CLR), o ponto de ruptura será ignorado. Isso permite que o CLR evite despachar um ponto de ruptura fora de banda, quando o ponto de ruptura é definido pelo depurador.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework Versions:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
