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
ms.openlocfilehash: 41c5116d23655730f3586dc656aa69c8ae817b6c
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76792620"
---
# <a name="icordebugprocessgetthreadcontext-method"></a>Método ICorDebugProcess::GetThreadContext
Obtém o contexto para o thread determinado neste processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetThreadContext(  
    [in] DWORD threadID,  
    [in] ULONG32 contextSize,  
    [in, out, length_is(contextSize), size_is(contextSize)]  
    BYTE context[]);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `threadID`  
 no A ID do thread para o qual recuperar o contexto.  
  
 `contextSize`  
 no O tamanho da matriz de `context`.  
  
 `context`  
 [entrada, saída] Uma matriz de bytes que descreve o contexto do thread.  
  
 O contexto especifica a arquitetura do processador no qual o thread está sendo executado.  
  
## <a name="remarks"></a>Comentários  
 O depurador deve chamar esse método em vez do método Win32 `GetThreadContext`, pois o thread pode realmente estar em um estado "seqüestrado", no qual seu contexto foi alterado temporariamente. Esse método deve ser usado somente quando um thread estiver em código nativo. Use [ICorDebugRegisterSet](icordebugregisterset-interface.md) para threads em código gerenciado.  
  
 Os dados retornados são uma estrutura de contexto para a plataforma atual. Assim como ocorre com o método de `GetThreadContext` do Win32, o chamador deve inicializar o parâmetro `context` antes de chamar esse método.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
