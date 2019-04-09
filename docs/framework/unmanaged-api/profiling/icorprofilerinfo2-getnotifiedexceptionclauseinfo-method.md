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
ms.openlocfilehash: cabe2f1ad5b586fed24c7317bb3a7b8407e09158
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59167005"
---
# <a name="icorprofilerinfo2getnotifiedexceptionclauseinfo-method"></a><span data-ttu-id="7cb84-102">Método ICorProfilerInfo2::GetNotifiedExceptionClauseInfo</span><span class="sxs-lookup"><span data-stu-id="7cb84-102">ICorProfilerInfo2::GetNotifiedExceptionClauseInfo Method</span></span>
<span data-ttu-id="7cb84-103">Obtém as informações de endereço e o quadro nativas para a cláusula de exceção (`catch`/`finally`/`filter`) que está prestes a ser executado ou foi executado.</span><span class="sxs-lookup"><span data-stu-id="7cb84-103">Gets the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run or has just been run.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7cb84-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7cb84-104">Syntax</span></span>  
  
```  
HRESULT GetNotifiedExceptionClauseInfo(  
    [out] COR_PRF_EX_CLAUSE_INFO *pinfo);  
```  
  
## <a name="parameters"></a><span data-ttu-id="7cb84-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7cb84-105">Parameters</span></span>  
 `pinfo`  
 <span data-ttu-id="7cb84-106">[out] Um ponteiro para um [COR_PRF_EX_CLAUSE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) estrutura que descreve a instância de cláusula de exceção atual e seu quadro associado.</span><span class="sxs-lookup"><span data-stu-id="7cb84-106">[out] A pointer to a [COR_PRF_EX_CLAUSE_INFO](../../../../docs/framework/unmanaged-api/profiling/cor-prf-ex-clause-info-structure.md) structure that describes the current exception clause instance and its associated frame.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7cb84-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="7cb84-107">Remarks</span></span>  
 <span data-ttu-id="7cb84-108">Quando uma notificação de exceção é recebida, `GetNotifiedExceptionClauseInfo` pode ser usado para obter as informações de endereço e o quadro nativas para a cláusula de exceção (`catch`/`finally`/`filter`) que está prestes a ser executado ([ ICorProfilerCallback:: Exceptioncatcherenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback:: Exceptionunwindfinallyenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md), ou [ICorProfilerCallback:: Exceptionsearchfilterenter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md)retorno de chamada é recebido pelo criador de perfil) ou foi executado ([ICorProfilerCallback:: Exceptioncatcherleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback:: Exceptionunwindfinallyleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md), ou [ ICorProfilerCallback:: Exceptionsearchfilterleave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) retorno de chamada é recebido pelo criador de perfil).</span><span class="sxs-lookup"><span data-stu-id="7cb84-108">When an exception notification is received, `GetNotifiedExceptionClauseInfo` can be used to get the native address and frame information for the exception clause (`catch`/`finally`/`filter`) that is about to be run ([ICorProfilerCallback::ExceptionCatcherEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherenter-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyenter-method.md), or [ICorProfilerCallback::ExceptionSearchFilterEnter](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterenter-method.md) callback is received by the profiler) or has just been run ([ICorProfilerCallback::ExceptionCatcherLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptioncatcherleave-method.md), [ICorProfilerCallback::ExceptionUnwindFinallyLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionunwindfinallyleave-method.md), or [ICorProfilerCallback::ExceptionSearchFilterLeave](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-exceptionsearchfilterleave-method.md) callback is received by the profiler).</span></span>  
  
 <span data-ttu-id="7cb84-109">Essa chamada pode ser feita a qualquer momento depois que um os retornos de chamada de Enter acima até que o retorno de chamada deixe correspondente é recebido ou uma exceção aninhada na cláusula atual, nesse caso não é nenhuma notificação deixe dessa cláusula.</span><span class="sxs-lookup"><span data-stu-id="7cb84-109">This call can be made at any time after one of the Enter callbacks above until either the matching Leave callback is received or a nested exception is thrown in the current clause, in which case there is no Leave notification for that clause.</span></span> <span data-ttu-id="7cb84-110">Observe que não é possível que uma exceção lançada escapar um `filter` cláusula de exceção, portanto, há sempre uma notificação deixe nesse caso.</span><span class="sxs-lookup"><span data-stu-id="7cb84-110">Note that it is not possible for a thrown exception to escape a `filter` exception clause, so there is always a Leave notification in that case.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cb84-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7cb84-111">Requirements</span></span>  
 <span data-ttu-id="7cb84-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7cb84-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7cb84-113">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7cb84-113">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7cb84-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7cb84-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="7cb84-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="7cb84-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="7cb84-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7cb84-116">See also</span></span>

- [<span data-ttu-id="7cb84-117">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="7cb84-117">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
- [<span data-ttu-id="7cb84-118">Interface ICorProfilerInfo2</span><span class="sxs-lookup"><span data-stu-id="7cb84-118">ICorProfilerInfo2 Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-interface.md)
