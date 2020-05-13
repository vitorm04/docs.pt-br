---
title: Método ICorDebugThread2::GetTaskID
ms.date: 03/30/2017
api_name:
- ICorDebugThread2.GetTaskID
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2::GetTaskID
helpviewer_keywords:
- ICorDebugThread2::GetTaskID method [.NET Framework debugging]
- GetTaskID method [.NET Framework debugging]
ms.assetid: 6ba3c6ee-4ba1-4c98-bf1e-8531acd3da09
topic_type:
- apiref
ms.openlocfilehash: 841af546cc3586529fe290c69e686438f634b90d
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83377791"
---
# <a name="icordebugthread2gettaskid-method"></a>Método ICorDebugThread2::GetTaskID
Obtém o identificador da tarefa em execução neste thread.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetTaskID (  
    [out] TASKID  *pTaskId  
);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pTaskId`  
 fora Um ponteiro para o identificador da tarefa em execução no thread representado por esse objeto ICorDebugThread2.  
  
## <a name="remarks"></a>Comentários  
 Uma tarefa só poderá ser executada no thread se o thread estiver associado a uma conexão. `GetTaskID`retornará zero `pTaskId` se o thread não estiver associado a uma conexão.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
