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
ms.openlocfilehash: 9452f238bd84c9c185ca8e007acac563474d29df
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/12/2020
ms.locfileid: "83212055"
---
# <a name="icordebugprocessisossuspended-method"></a>Método ICorDebugProcess::IsOSSuspended
Obtém um valor que indica se o thread especificado foi suspenso como resultado do depurador parar esse processo.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `threadID`  
 no A ID do thread em questão.  
  
 `pbSuspended`  
 fora Um ponteiro para um valor booliano que é `true` se o thread especificado tiver sido suspenso; caso contrário, * `pbSuspended` será `false` .  
  
## <a name="remarks"></a>Comentários  
 Quando o thread especificado tiver sido suspenso como resultado do depurador parar esse processo, a contagem de suspensões do Win32 do thread especificado será incrementada em um. A interface do usuário do depurador pode querer levar essas informações em conta se ele exibir a contagem de suspensões do sistema operacional (SO) do thread para o usuário.  
  
 O `IsOSSuspended` método faz sentido apenas no contexto de depuração não gerenciada. Durante a depuração gerenciada, OS threads são suspensos de cooperabilidade em vez do so suspenso.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
