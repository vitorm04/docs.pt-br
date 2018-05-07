---
title: Método ICorDebugProcess::IsOSSuspended
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsOSSuspended
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b65a621541f2b4a800f6b3708a6b257374c5866
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icordebugprocessisossuspended-method"></a>Método ICorDebugProcess::IsOSSuspended
Obtém um valor que indica se o thread especificado foi suspenso como resultado o depurador interromper este processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `threadID`  
 [in] A ID do thread em questão.  
  
 `pbSuspended`  
 [out] Um ponteiro para um valor booliano que é `true` se o thread especificado tiver sido suspenso; caso contrário *`pbSuspended` é `false`.  
  
## <a name="remarks"></a>Comentários  
 Quando o thread especificado foi suspenso como resultado o depurador interromper este processo, Win32 do thread especificado suspender a contagem é incrementado em um. A interface do usuário do depurador (UI) poderá querer colocar essas informações em conta se ele exibe o sistema operacional (SO) suspender a contagem de thread para o usuário.  
  
 O `IsOSSuspended` método apenas faz sentido no contexto de depuração não gerenciada. Durante a depuração gerenciada, threads são cooperativamente suspenso em vez de suspenso pelo sistema operacional.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
