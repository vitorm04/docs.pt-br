---
title: Método ICorDebugMutableDataTarget::SetThreadContext
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee2ee66a5129bcf5f6c7c6881e50264b3c41773d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54664467"
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a>Método ICorDebugMutableDataTarget::SetThreadContext
Define o contexto (valores do registro) para um thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwThreadID`  
 [in] O identificador de thread definidos pelo sistema operacional.  
  
 `contextSize`  
 [in] O tamanho do `pContext` buffer a ser gravado.  
  
 `pContext`  
 [in] Um ponteiro para os bytes a serem gravados.  
  
## <a name="remarks"></a>Comentários  
 O `SetThreadContext` método atualiza o contexto atual para o thread especificado pelo sistema operacional definido `dwThreadID` argumento. O formato do registro de contexto é determinado pela plataforma indicada pela [icordebugdatatarget:: Getplatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) método. No Windows, essa é uma [contexto](/windows/desktop/api/winnt/ns-winnt-_arm64_nt_context) estrutura.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Consulte também
- [Interface ICorDebugMutableDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)
- [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
