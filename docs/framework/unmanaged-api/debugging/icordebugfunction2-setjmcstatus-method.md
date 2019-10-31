---
title: Método ICorDebugFunction2::SetJMCStatus
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type:
- apiref
ms.openlocfilehash: 758364b2d63343e464b727d5a1c1817533a6acea
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73137788"
---
# <a name="icordebugfunction2setjmcstatus-method"></a>Método ICorDebugFunction2::SetJMCStatus
Marca a função representada por este ICorDebugFunction2 para Apenas Meu Código stepping.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `bIsJustMyCode`  
 no Defina como `true` para marcar a função como código de usuário; caso contrário, defina como `false`.  
  
## <a name="return-values"></a>Valores de Retorno  
  
|HRESULT|Descrição|  
|-------------|-----------------|  
|`S_OK`|A função foi marcada com êxito.|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|A função não pôde ser marcada como código de usuário porque não pode ser depurada.|  
  
## <a name="remarks"></a>Comentários  
 Um Apenas Meu Código stepper ignorará o código que não é do usuário. O código do usuário deve ser um subconjunto de código depurável.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
