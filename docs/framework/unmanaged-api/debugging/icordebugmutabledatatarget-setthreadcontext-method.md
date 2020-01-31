---
title: 'Método ICorDebugMutableDataTarget:: SetThreadContext'
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
ms.openlocfilehash: 063c7954543174caece6f3dcbe005a4b2d059c64
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792843"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a>Método ICorDebugMutableDataTarget:: SetThreadContext
Define o contexto (valores de registro) para um thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `dwThreadID`  
 no O identificador de thread definido pelo sistema operacional.  
  
 `contextSize`  
 no O tamanho do buffer de `pContext` a ser gravado.  
  
 `pContext`  
 no Um ponteiro para os bytes a serem gravados.  
  
## <a name="remarks"></a>Comentários  
 O método `SetThreadContext` atualiza o contexto atual para o thread especificado pelo argumento `dwThreadID` definido pelo sistema operacional. O formato do registro de contexto é determinado pela plataforma indicada pelo método [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) . No Windows, essa é uma estrutura de [contexto](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) .  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorDebugMutableDataTarget](icordebugmutabledatatarget-interface.md)
- [Depurando interfaces](debugging-interfaces.md)
