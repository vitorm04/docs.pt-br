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
ms.openlocfilehash: fc5356f097f869403212cd234a508f1f29c5ec94
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74450390"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="045f6-102">Método ICorProfilerInfo::GetCurrentThreadID</span><span class="sxs-lookup"><span data-stu-id="045f6-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="045f6-103">Obtém a ID do thread atual, se for um thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="045f6-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="045f6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="045f6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="045f6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="045f6-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="045f6-106">fora Um ponteiro para a ID retornada do thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="045f6-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="045f6-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="045f6-107">Remarks</span></span>  
 <span data-ttu-id="045f6-108">Se o thread atual for um thread de tempo de execução interno ou outro thread não gerenciado, `GetCurrentThreadID` retornará CORPROF_E_NOT_MANAGED_THREAD como HRESULT, e o valor retornado do parâmetro `pThreadId` será NULL.</span><span class="sxs-lookup"><span data-stu-id="045f6-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="045f6-109">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="045f6-109">Requirements</span></span>  
 <span data-ttu-id="045f6-110">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="045f6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="045f6-111">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="045f6-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="045f6-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="045f6-112">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="045f6-113">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="045f6-113">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="045f6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="045f6-114">See also</span></span>

- [<span data-ttu-id="045f6-115">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="045f6-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
