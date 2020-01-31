---
title: Método ICorProfilerInfo::GetCurrentThreadID
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetCurrentThreadID
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetCurrentThreadID
helpviewer_keywords:
- GetCurrentThreadID method, ICorProfilerInfo interface [.NET Framework profiling]
- ICorProfilerInfo::GetCurrentThreadID method [.NET Framework profiling]
ms.assetid: 39bbdb30-6a7a-4202-8da3-67ae9a0ab3a8
topic_type:
- apiref
ms.openlocfilehash: e70d8ee40e16e37a12f8ed4033d2aa7489f0f25e
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76863940"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a>Método ICorProfilerInfo::GetCurrentThreadID
Obtém a ID do thread atual, se for um thread gerenciado.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pThreadId`  
 fora Um ponteiro para a ID retornada do thread gerenciado.  
  
## <a name="remarks"></a>Comentários  
 Se o thread atual for um thread de tempo de execução interno ou outro thread não gerenciado, `GetCurrentThreadID` retornará CORPROF_E_NOT_MANAGED_THREAD como HRESULT, e o valor retornado do parâmetro `pThreadId` será NULL.  
  
## <a name="requirements"></a>Requisitos do  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Veja também

- [Interface ICorProfilerInfo](icorprofilerinfo-interface.md)
