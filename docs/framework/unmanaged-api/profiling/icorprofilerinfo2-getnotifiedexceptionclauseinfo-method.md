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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 07606bf58709f088db486e0263e5cb519ab5b4cf
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a>Método ICorProfilerInfo2::GetNotifiedExceptionClauseInfo
Obtém as informações de endereço e o quadro nativo para a cláusula de exceção (`catch`/`finally`/`filter`) que está prestes a ser executado ou executado anteriormente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `pinfo`  
 [out] Um ponteiro para um [COR_PRF_EX_CLAUSE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) estrutura que descreve a instância de cláusula da exceção atual e seu quadro associado.  
  
## <a name="remarks"></a>Comentários  
 Quando uma notificação de exceção é recebida, `GetNotifiedExceptionClauseInfo` pode ser usado para obter as informações de endereço e o quadro nativo para a cláusula de exceção (`catch`/`finally`/`filter`) que está prestes a ser executado ([ : Exceptioncatcherenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [: Exceptionunwindfinallyenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md), ou [: Exceptionsearchfilterenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)retorno de chamada é recebido pelo criador de perfil) ou foi executado ([Exceptioncatcherleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [Exceptionunwindfinallyleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md), ou [ : Exceptionsearchfilterleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) retorno de chamada é recebido pelo criador de perfil).  
  
 Essa chamada pode ser feita a qualquer momento depois que um os retornos de chamada de Enter acima até que o retorno de chamada de licença correspondente é recebido ou uma exceção aninhada na cláusula atual, em que o caso de haver não é nenhuma notificação de sair dessa cláusula. Observe que não é possível que uma exceção lançada escapar um `filter` cláusula de exceção, para que haja sempre uma notificação deixe nesse caso.  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Corprof. idl, CorProf.h  
  
 **Biblioteca:** CorGuids.lib  
  
 **Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Interface ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)  
 [Interface ICorProfilerInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
