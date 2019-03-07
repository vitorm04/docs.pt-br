---
title: Método ICorDebugProcess::ClearCurrentException
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.ClearCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::ClearCurrentException
helpviewer_keywords:
- ClearCurrentException method, ICorDebugProcess interface [.NET Framework debugging]
- ICorDebugProcess::ClearCurrentException method [.NET Framework debugging]
ms.assetid: 9e02ee1a-e495-4578-bfb5-b946274bede7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f014f9213a4b9a2d5119af9a6dceebb9a9d54b52
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57473456"
---
# <a name="icordebugprocessclearcurrentexception-method"></a>Método ICorDebugProcess::ClearCurrentException
Limpa a exceção atual não gerenciada em um determinado thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `threadID`  
 [in] A ID do thread no qual a exceção não gerenciada atual será limpo.  
  
## <a name="remarks"></a>Comentários  
 Chame esse método antes de chamar [icordebugcontroller:: continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) quando um thread relatou uma exceção não gerenciada que deve ser ignorada pelo elemento a ser depurado. Isso limpará o pendentes em banda (IB) e os eventos do fora de banda (OOB) em um determinado thread. Todos os pontos de interrupção OOB e exceções do passo a passo são removidas automaticamente.  
  
 Use [ICorDebugThread2::InterceptCurrentException](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) interceptar atual exceção em um thread gerenciado.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
