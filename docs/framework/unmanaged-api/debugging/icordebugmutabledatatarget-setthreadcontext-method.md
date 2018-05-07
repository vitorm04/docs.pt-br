---
title: Método ICorDebugMutableDataTarget::SetThreadContext
ms.date: 03/30/2017
ms.assetid: 8c0d01d5-67e5-4522-9ccf-c8f3a78cb4fd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 05f0c0d23b4885f2d6fd351fdf845a25c899228e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugmutabledatatargetsetthreadcontext-method"></a>Método ICorDebugMutableDataTarget::SetThreadContext
Define o contexto (valores do registro) de um thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT SetThreadContext(  
   [in] DWORD dwThreadID,  
   [in] ULONG32 contextSize,   [in, size_is(contextSize)] const BYTE * pContext);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `dwThreadID`  
 [in] O identificador de thread definido pelo sistema operacional.  
  
 `contextSize`  
 [in] O tamanho do `pContext` buffer a ser gravado.  
  
 `pContext`  
 [in] Um ponteiro para os bytes a serem gravados.  
  
## <a name="remarks"></a>Comentários  
 O `SetThreadContext` método atualizará o contexto atual para o segmento especificado, o sistema operacional definido `dwThreadID` argumento. O formato do registro de contexto é determinado pela plataforma indicada pelo [Icordebugdatatarget](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) método. No Windows, este é um [contexto](http://msdn.microsoft.com/library/windows/desktop/ms679284.aspx) estrutura.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v46plus](../../../../includes/net-current-v46plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorDebugMutableDataTarget](../../../../docs/framework/unmanaged-api/debugging/icordebugmutabledatatarget-interface.md)  
 [Depurando interfaces](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
