---
title: 'Método ICorDebugMutableDataTarget:: SetThreadContext'
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 21a24b3ae3563db09f1f7e9229f388abf8de654c
ms.sourcegitcommit: cf9515122fce716bcfb6618ba366e39b5a2eb81e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69038306"
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
 no O tamanho do `pContext` buffer a ser gravado.  
  
 `pContext`  
 no Um ponteiro para os bytes a serem gravados.  
  
## <a name="remarks"></a>Comentários  
 O `SetThreadContext` método atualiza o contexto atual para o thread especificado pelo argumento definido `dwThreadID` pelo sistema operacional. O formato do registro de contexto é determinado pela plataforma indicada pelo método [ICorDebugDataTarget:: GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) . No Windows, essa é uma estrutura de [contexto](/windows/win32/api/winnt/ns-winnt-arm64_nt_context) .  
  
## <a name="requirements"></a>Requisitos  
 **Compatíveis** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorDebugMutableDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
