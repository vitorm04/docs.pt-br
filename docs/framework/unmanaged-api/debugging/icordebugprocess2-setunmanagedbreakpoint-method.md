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
ms.openlocfilehash: ffab2762fd86e95c3272ca456039028e0897bc41
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137175"
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a>Método ICorDebugProcess2::SetUnmanagedBreakpoint
Define um ponto de interrupção não gerenciado no deslocamento da imagem nativa especificada.  
  
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
  
## <a name="parameters"></a>Parâmetros  
 `address`  
 no Um objeto `CORDB_ADDRESS` que especifica o deslocamento da imagem nativa.  
  
 `bufsize`  
 no O tamanho, em bytes, da matriz de `buffer`.  
  
 `buffer`  
 fora Uma matriz que contém o opcode que é substituído pelo ponto de interrupção.  
  
 `bufLen`  
 fora Um ponteiro para o número de bytes retornados na matriz de `buffer`.  
  
## <a name="remarks"></a>Comentários  
 Se o deslocamento da imagem nativa estiver dentro do Common Language Runtime (CLR), o ponto de interrupção será ignorado. Isso permite que o CLR Evite distribuir um ponto de interrupção fora de banda, quando o ponto de interrupção é definido pelo depurador.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
