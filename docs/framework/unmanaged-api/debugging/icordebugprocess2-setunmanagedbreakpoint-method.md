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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d4326c6d8a3ee780cf63652badc8c527f55a075c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocess2setunmanagedbreakpoint-method"></a>Método ICorDebugProcess2::SetUnmanagedBreakpoint
Define um ponto de interrupção não gerenciado no deslocamento especificado de imagem nativa.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetUnmanagedBreakpoint (  
    [in]  CORDB_ADDRESS    address,  
    [in]  ULONG32          bufsize,  
    [out, size_is(bufsize), length_is(*bufLen)]   
        BYTE               buffer[],  
    [out] ULONG32          *bufLen  
);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `address`  
 [in] Um `CORDB_ADDRESS` objeto que especifica o deslocamento de imagem nativa.  
  
 `bufsize`  
 [in] O tamanho, em bytes, do `buffer` matriz.  
  
 `buffer`  
 [out] Uma matriz que contém o código de operação que é substituído pelo ponto de interrupção.  
  
 `bufLen`  
 [out] Um ponteiro para o número de bytes retornados a `buffer` matriz.  
  
## <a name="remarks"></a>Comentários  
 Se o deslocamento de imagem nativa estiver dentro o common language runtime (CLR), o ponto de interrupção será ignorado. Isso permite que o CLR evitar a distribuição de um ponto de interrupção de fora da banda, quando o ponto de interrupção é definido pelo depurador.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
