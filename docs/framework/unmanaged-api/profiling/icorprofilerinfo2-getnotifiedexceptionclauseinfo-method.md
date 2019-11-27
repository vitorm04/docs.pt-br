---
title: Método ICorProfilerInfo2::GetNotifiedExceptionClauseInfo
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo2.GetNotifiedExceptionClauseInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo2::GetNotifiedExceptionClauseInfo
helpviewer_keywords:
- ICorProfilerInfo2::GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
- GetNotifiedExceptionCaluseInfo method [.NET Framework profiling]
ms.assetid: f9594a7e-cb0c-4c48-accb-29f762aa0c21
topic_type:
- apiref
ms.openlocfilehash: 52ad124638a1c1ec7d39fa41b9163f3ab50ffe70
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74433076"
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a>Método ICorProfilerInfo2::GetNotifiedExceptionClauseInfo
Obtém as informações de endereço nativo e de quadro da cláusula de exceção (`catch`/`finally`/`filter`) que está prestes a ser executada ou que acabou de ser executada.  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a>Parâmetros  
 `pinfo`  
 fora Um ponteiro para uma estrutura de [COR_PRF_EX_CLAUSE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) que descreve a instância da cláusula de exceção atual e seu quadro associado.  
  
## <a name="remarks"></a>Comentários  
 Quando uma notificação de exceção é recebida, `GetNotifiedExceptionClauseInfo` pode ser usada para obter o endereço nativo e as informações de quadro da cláusula de exceção (`catch`/`finally`/`filter`) que está prestes a ser executada ([ICorProfilerCallback:: ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback:: ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md)ou [ICorProfilerCallback:: ExceptionSearchFilterEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md) o retorno de chamada é recebido pelo criador de perfil) ou acabou de ser executada ([ICorProfilerCallback:: ExceptionCatcherLeave ](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback:: ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md)ou [ICorProfilerCallback:: ExceptionSearchFilterLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) callback é recebido pelo criador de perfil).  
  
 Essa chamada pode ser feita a qualquer momento após um dos retornos de chamada Enter acima até que o retorno de chamada Leave correspondente seja recebido ou uma exceção aninhada seja gerada na cláusula Current; nesse caso, não há nenhuma notificação de licença para essa cláusula. Observe que não é possível que uma exceção gerada saia de um `filter` cláusula de exceção, portanto, sempre há uma notificação de licença nesse caso.  
  
## <a name="requirements"></a>{1&gt;{2&gt;Requisitos&lt;2}&lt;1}  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** CorProf. idl, CorProf. h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
