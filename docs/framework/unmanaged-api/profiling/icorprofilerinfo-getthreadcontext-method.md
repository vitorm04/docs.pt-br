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
ms.openlocfilehash: 45ae164e79f077549a1d685aa060484240546a10
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 06/08/2020
ms.locfileid: "84497940"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="4feed-102">Método ICorProfilerInfo::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="4feed-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="4feed-103">Obtém a identidade de contexto atualmente associada ao thread especificado.</span><span class="sxs-lookup"><span data-stu-id="4feed-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4feed-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4feed-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="4feed-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4feed-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="4feed-106">no A ID do thread.</span><span class="sxs-lookup"><span data-stu-id="4feed-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="4feed-107">fora Um ponteiro para a ID de contexto atualmente associada ao thread especificado.</span><span class="sxs-lookup"><span data-stu-id="4feed-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="4feed-108">Se o thread não tiver nenhum contexto associado a ele no momento, essa função retornará CORPROF_E_DATAINCOMPLETE.</span><span class="sxs-lookup"><span data-stu-id="4feed-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4feed-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4feed-109">Requirements</span></span>  
 <span data-ttu-id="4feed-110">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="4feed-110">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="4feed-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="4feed-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="4feed-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="4feed-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="4feed-113">**.NET Framework versões:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="4feed-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4feed-114">Confira também</span><span class="sxs-lookup"><span data-stu-id="4feed-114">See also</span></span>

- [<span data-ttu-id="4feed-115">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="4feed-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
