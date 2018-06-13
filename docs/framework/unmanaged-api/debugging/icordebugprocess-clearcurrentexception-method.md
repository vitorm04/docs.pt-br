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
ms.openlocfilehash: d2515e21ec00bd656eafd21a092a27304f7b1769
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419010"
---
# <a name="icordebugprocessclearcurrentexception-method"></a>Método ICorDebugProcess::ClearCurrentException
Limpa a exceção atual não gerenciada em um determinado thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT ClearCurrentException([in] DWORD threadID);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `threadID`  
 [in] A ID do thread no qual a exceção não gerenciada atual será limpo.  
  
## <a name="remarks"></a>Comentários  
 Chamar esse método antes de chamar [Icordebugcontroller](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) quando um thread relatou uma exceção não gerenciada que deve ser ignorada pelo elemento a ser depurado. Isso limpará o pendentes em banda (IB) e os eventos do fora de banda (OOB) em um determinado thread. Todos os pontos de interrupção OOB e única etapa exceções serão desmarcadas automaticamente.  
  
 Use [Icordebugthread2](../../../../docs/framework/unmanaged-api/debugging/icordebugthread2-interceptcurrentexception-method.md) para interceptar atual gerenciado exceção em um thread.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
