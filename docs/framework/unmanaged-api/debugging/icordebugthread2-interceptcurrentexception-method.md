---
title: Método ICorDebugThread2::InterceptCurrentException
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.InterceptCurrentException
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::InterceptCurrentException
helpviewer_keywords:
- InterceptCurrentException method [.NET Framework debugging]
- ICorDebugThread2::InterceptCurrentException method [.NET Framework debugging]
ms.assetid: 536d2357-1b97-49e0-a10c-c860aed74e6e
topic_type:
- apiref
ms.openlocfilehash: d87f07e6cadf8c9b5a4d8bb3063333c26e2c4ff1
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379038"
---
# <a name="icordebugthread2interceptcurrentexception-method"></a>Método ICorDebugThread2::InterceptCurrentException
Permite que um depurador intercepte a exceção atual neste thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT InterceptCurrentException (  
    [in] ICorDebugFrame  *pFrame  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pFrame`  
 no Um ponteiro para um ICorDebugFrame que representa o quadro de ativação ativo.  
  
## <a name="remarks"></a>Comentários  
 O `InterceptCurrentException` método pode ser chamado entre um retorno de chamada de exceção ([ICorDebugManagedCallback:: Exception](icordebugmanagedcallback-exception-method.md) ou [ICorDebugManagedCallback2:: Exception](icordebugmanagedcallback2-exception-method.md)) e a chamada associada a [ICorDebugController:: Continue](icordebugcontroller-continue-method.md).  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
