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
ms.openlocfilehash: f8eff85392d355ea54980ac6b29e3c4cebb1b240
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76869589"
---
# <a name="icorprofilerinfogetthreadcontext-method"></a><span data-ttu-id="f5faa-102">Método ICorProfilerInfo::GetThreadContext</span><span class="sxs-lookup"><span data-stu-id="f5faa-102">ICorProfilerInfo::GetThreadContext Method</span></span>
<span data-ttu-id="f5faa-103">Obtém a identidade de contexto atualmente associada ao thread especificado.</span><span class="sxs-lookup"><span data-stu-id="f5faa-103">Gets the context identity currently associated with the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f5faa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f5faa-104">Syntax</span></span>  
  
```cpp  
HRESULT GetThreadContext(  
    [in]  ThreadID  threadId,  
    [out] ContextID *pContextId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="f5faa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f5faa-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="f5faa-106">no A ID do thread.</span><span class="sxs-lookup"><span data-stu-id="f5faa-106">[in] The ID of the thread.</span></span>  
  
 `pContextId`  
 <span data-ttu-id="f5faa-107">fora Um ponteiro para a ID de contexto atualmente associada ao thread especificado.</span><span class="sxs-lookup"><span data-stu-id="f5faa-107">[out] A pointer to the context ID currently associated with the specified thread.</span></span> <span data-ttu-id="f5faa-108">Se o thread não tiver nenhum contexto associado a ele no momento, essa função retornará CORPROF_E_DATAINCOMPLETE.</span><span class="sxs-lookup"><span data-stu-id="f5faa-108">If the thread has no context currently associated with it, this function will return CORPROF_E_DATAINCOMPLETE.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f5faa-109">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="f5faa-109">Requirements</span></span>  
 <span data-ttu-id="f5faa-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f5faa-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f5faa-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="f5faa-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="f5faa-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f5faa-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f5faa-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f5faa-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f5faa-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="f5faa-114">See also</span></span>

- [<span data-ttu-id="f5faa-115">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="f5faa-115">ICorProfilerInfo Interface</span></span>](icorprofilerinfo-interface.md)
