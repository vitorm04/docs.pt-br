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
ms.openlocfilehash: 275f62c8211f71f067d310dd4b3af2ddb11e93d7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755466"
---
# <a name="icordebugprocessisossuspended-method"></a>Método ICorDebugProcess::IsOSSuspended
Obtém um valor que indica se o thread especificado foi suspenso como resultado o depurador interromper este processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `threadID`  
 [in] A ID do thread em questão.  
  
 `pbSuspended`  
 [out] Um ponteiro para um valor booliano que será `true` se o thread especificado tiver sido suspenso; caso contrário *`pbSuspended` é `false`.  
  
## <a name="remarks"></a>Comentários  
 Quando o thread especificado foi suspenso como resultado o depurador interromper esse processo, a contagem de suspensões Win32 do thread especificado é incrementado em um. Da interface de usuário (IU) do depurador poderá querer colocar essas informações em conta se ela exibir o sistema operacional (SO) suspender a contagem do thread para o usuário.  
  
 O `IsOSSuspended` método só faz sentido no contexto de depuração não gerenciada. Durante a depuração gerenciada, os threads são cooperativamente suspenso em vez de suspenso pelo sistema operacional.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
