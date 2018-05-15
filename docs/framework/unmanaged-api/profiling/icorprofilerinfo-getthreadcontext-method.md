---
title: Método ICorProfilerInfo::GetThreadContext
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetThreadContext
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadContext
helpviewer_keywords:
- ICorProfilerInfo::GetThreadContext method [.NET Framework profiling]
- GetThreadContext method, ICorProfilerInfo interface [.NET Framework profiling]
ms.assetid: 79446216-4b8b-484c-8fe3-e87dbf9df2fd
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: acb4d67f41b1434fe8052a74e976907f24fecd31
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="7736b-102">Método ICorProfilerInfo::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="7736b-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="7736b-103">Obtém a identidade de contexto atualmente associada com o segmento especificado.</span><span class="sxs-lookup"><span data-stu-id="7736b-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7736b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7736b-104">Syntax</span></span>  
  
```  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7736b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7736b-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="7736b-106">[in] A ID do thread.</span><span class="sxs-lookup"><span data-stu-id="7736b-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="7736b-107">[out] Um ponteiro para a ID do contexto atualmente associado com o segmento especificado.</span><span class="sxs-lookup"><span data-stu-id="7736b-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="7736b-108">Se o thread não tem nenhum contexto associado a ela, essa função retornará CORPROF_E_DATAINCOMPLETE.</span><span class="sxs-lookup"><span data-stu-id="7736b-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7736b-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7736b-109">Requirements</span></span>  
 <span data-ttu-id="7736b-110">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7736b-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7736b-111">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7736b-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7736b-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7736b-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7736b-113">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7736b-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7736b-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7736b-114">See Also</span></span>  
 [<span data-ttu-id="7736b-115">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="7736b-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
