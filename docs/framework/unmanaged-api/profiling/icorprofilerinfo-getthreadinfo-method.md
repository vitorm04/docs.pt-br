---
title: "Método ICorProfilerInfo::GetThreadInfo"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorProfilerInfo.GetThreadInfo
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetThreadInfo
helpviewer_keywords:
- ICorProfilerInfo::GetThreadInfo method [.NET Framework profiling]
- GetThreadInfo method [.NET Framework profiling]
ms.assetid: fc994fef-65c9-432a-84cb-66c8141147e7
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 2ab887cf4aaded260903cf1b91498c7641eeb0a8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorprofilerinfogetthreadinfo-method"></a><span data-ttu-id="144dd-102">Método ICorProfilerInfo::GetThreadInfo</span><span class="sxs-lookup"><span data-stu-id="144dd-102">ICorProfilerInfo::GetThreadInfo Method</span></span>
<span data-ttu-id="144dd-103">Obtém a identidade atual do thread Win32 do thread especificado.</span><span class="sxs-lookup"><span data-stu-id="144dd-103">Gets the current Win32 thread identity for the specified thread.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="144dd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="144dd-104">Syntax</span></span>  
  
```  
HRESULT GetThreadInfo(  
    [in]  ThreadID threadId,  
    [out] DWORD    *pdwWin32ThreadId);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="144dd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="144dd-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="144dd-106">[in] A ID do thread para o qual obter a identificação do Win32.</span><span class="sxs-lookup"><span data-stu-id="144dd-106">[in] The ID of the thread for which to get the current Win32 ID.</span></span>  
  
 `pdwWin32ThreadId`  
 <span data-ttu-id="144dd-107">[out] ID de um ponteiro para o thread atual de Win32 do thread especificado.</span><span class="sxs-lookup"><span data-stu-id="144dd-107">[out] A pointer to the specified thread's current Win32 thread ID.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="144dd-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="144dd-108">Requirements</span></span>  
 <span data-ttu-id="144dd-109">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="144dd-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="144dd-110">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="144dd-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="144dd-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="144dd-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="144dd-112">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="144dd-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="144dd-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="144dd-113">See Also</span></span>  
 [<span data-ttu-id="144dd-114">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="144dd-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
