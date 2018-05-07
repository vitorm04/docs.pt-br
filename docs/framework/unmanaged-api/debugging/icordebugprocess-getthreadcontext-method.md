---
title: Método ICorDebugProcess::GetThreadContext
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.GetThreadContext
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::GetThreadContext
helpviewer_keywords:
- ICorDebugProcess::GetThreadContext method [.NET Framework debugging]
- GetThreadContext method, ICorDebugProcess interface [.NET Framework debugging]
ms.assetid: 5b132ef1-8d4b-4525-89b3-54123596c194
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ea977b1ccecf9de5a04e1f1127658ca6c15043a4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocessgetthreadcontext-method"></a>Método ICorDebugProcess::GetThreadContext
Obtém o contexto do thread especificado neste processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `threadID`  
 [in] A ID do thread para o qual recuperar o contexto.  
  
 `contextSize`  
 [in] O tamanho do `context` matriz.  
  
 `context`  
 [out no] Uma matriz de bytes que descrevem o contexto do thread.  
  
 O contexto Especifica a arquitetura do processador que o thread está em execução.  
  
## <a name="remarks"></a>Comentários  
 O depurador deve chamar esse método em vez de Win32 `GetThreadContext` método, porque o thread, na verdade, pode estar em um estado "capturado", no qual seu contexto foi temporariamente alterado. Esse método deve ser usado somente quando um thread está no código nativo. Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) para segmentos no código gerenciado.  
  
 Os dados retornados são uma estrutura de contexto para a plataforma atual. Assim como ocorre com o Win32 `GetThreadContext` método, o chamador deve inicializar o `context` parâmetro antes de chamar esse método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
