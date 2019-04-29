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
ms.openlocfilehash: 28d54becc2d7cd4359c78415f25f579b968cb3f4
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775590"
---
# <a name="icordebugprocessgetthreadcontext-method"></a>Método ICorDebugProcess::GetThreadContext
Obtém o contexto para o thread determinado nesse processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `threadID`  
 [in] A ID do thread para o qual recuperar o contexto.  
  
 `contextSize`  
 [in] O tamanho do `context` matriz.  
  
 `context`  
 [no, out] Uma matriz de bytes que descrevem o contexto do thread.  
  
 O contexto Especifica a arquitetura do processador no qual o thread está em execução.  
  
## <a name="remarks"></a>Comentários  
 O depurador deve chamar esse método em vez de Win32 `GetThreadContext` método, porque o thread pode ficar em um estado "sequestrado", em que seu contexto foi alterado temporariamente. Esse método deve ser usado somente quando um thread está no código nativo. Use [ICorDebugRegisterSet](../../../../docs/framework/unmanaged-api/debugging/icordebugregisterset-interface.md) para threads em código gerenciado.  
  
 Os dados retornados são uma estrutura de contexto para a plataforma atual. Assim como ocorre com o Win32 `GetThreadContext` método, o chamador deve inicializar o `context` parâmetro antes de chamar esse método.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
