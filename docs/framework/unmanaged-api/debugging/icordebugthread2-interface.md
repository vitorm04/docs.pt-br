---
title: Interface ICorDebugThread2
ms.date: 03/30/2017
api_name:
- ICorDebugThread2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread2
helpviewer_keywords:
- ICorDebugThread2 interface [.NET Framework debugging]
ms.assetid: 678f89f9-cce7-46d1-af87-5e989abaa93c
topic_type:
- apiref
ms.openlocfilehash: a7a8d96548704f223f05826af79a4e227bdfab06
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/13/2020
ms.locfileid: "83379827"
---
# <a name="icordebugthread2-interface"></a>Interface ICorDebugThread2
Serve como uma extensão lógica para a interface ICorDebugThread.  
  
## <a name="methods"></a>Métodos  
  
|Método|Descrição|  
|------------|-----------------|  
|[Método GetActiveFunctions](icordebugthread2-getactivefunctions-method.md)|Obtém uma matriz de instâncias de COR_ACTIVE_FUNCTION que contêm dados sobre as funções ativas nos quadros de um thread.|  
|[Método GetConnectionID](icordebugthread2-getconnectionid-method.md)|Obtém um identificador de conexão para isso `ICorDebugThread2` .|  
|[Método GetTaskID](icordebugthread2-gettaskid-method.md)|Obtém um identificador de tarefa para isso `ICorDebugThread2` .|  
|[Método GetVolatileOSThreadID](icordebugthread2-getvolatileosthreadid-method.md)|Obtém o identificador de thread do sistema operacional para isso `ICorDebugThread2` .|  
|[Método InterceptCurrentException](icordebugthread2-interceptcurrentexception-method.md)|Permite que um depurador intercepte a exceção atual em um thread.|  
  
## <a name="remarks"></a>Comentários  
  
> [!NOTE]
> Esta interface não dá suporte para chamada remota, seja entre computadores ou processos cruzados.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).  
  
 **Cabeçalho:** CorDebug.idl, CorDebug.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Confira também

- [Depurando interfaces](debugging-interfaces.md)
