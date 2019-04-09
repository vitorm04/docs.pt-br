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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 802072f3a0151aabc5ca5796df57ea7c694a2070
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179030"
---
# <a name="icorprofilerinfogetcurrentthreadid-method"></a><span data-ttu-id="d71b6-102">Método ICorProfilerInfo::GetCurrentThreadID</span><span class="sxs-lookup"><span data-stu-id="d71b6-102">ICorProfilerInfo::GetCurrentThreadID Method</span></span>
<span data-ttu-id="d71b6-103">Obtém a ID do thread atual, se ele for um thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d71b6-103">Gets the ID of the current thread, if it is a managed thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d71b6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d71b6-104">Syntax</span></span>  
  
```  
HRESULT GetCurrentThreadID(  
    [out] ThreadID *pThreadId);  
```  
  
## <a name="parameters"></a><span data-ttu-id="d71b6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="d71b6-105">Parameters</span></span>  
 `pThreadId`  
 <span data-ttu-id="d71b6-106">[out] Um ponteiro para a ID retornada do thread gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d71b6-106">[out] A pointer to the returned ID of the managed thread.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d71b6-107">Comentários</span><span class="sxs-lookup"><span data-stu-id="d71b6-107">Remarks</span></span>  
 <span data-ttu-id="d71b6-108">Se o thread atual é um segmento de tempo de execução interno ou de outro thread não gerenciado, `GetCurrentThreadID` retorna CORPROF_E_NOT_MANAGED_THREAD como o HRESULT e o valor retornado do `pThreadId` parâmetro será nulo.</span><span class="sxs-lookup"><span data-stu-id="d71b6-108">If the current thread is an internal runtime thread or other unmanaged thread, `GetCurrentThreadID` returns CORPROF_E_NOT_MANAGED_THREAD as the HRESULT, and the returned value of the `pThreadId` parameter will be null.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d71b6-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d71b6-109">Requirements</span></span>  
 <span data-ttu-id="d71b6-110">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d71b6-110">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d71b6-111">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="d71b6-111">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="d71b6-112">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d71b6-112">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="d71b6-113">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="d71b6-113">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d71b6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d71b6-114">See also</span></span>

- [<span data-ttu-id="d71b6-115">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="d71b6-115">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
