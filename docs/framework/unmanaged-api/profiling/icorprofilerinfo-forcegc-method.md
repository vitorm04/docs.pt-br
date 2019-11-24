---
title: Método ICorProfilerInfo::ForceGC
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.ForceGC
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::ForceGC
helpviewer_keywords:
- ICorProfilerInfo::ForceGC method [.NET Framework profiling]
- ForceGC method [.NET Framework profiling]
ms.assetid: 0da1ef80-d242-4636-87d0-43e0470b342a
topic_type:
- apiref
ms.openlocfilehash: 9f97da4e68d4b76178198e91c3fb8f08b56dda7b
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448194"
---
# <a name="icorprofilerinfoforcegc-method"></a><span data-ttu-id="7a0d4-102">Método ICorProfilerInfo::ForceGC</span><span class="sxs-lookup"><span data-stu-id="7a0d4-102">ICorProfilerInfo::ForceGC Method</span></span>
<span data-ttu-id="7a0d4-103">Forces garbage collection to occur within the common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="7a0d4-103">Forces garbage collection to occur within the common language runtime (CLR).</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7a0d4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7a0d4-104">Syntax</span></span>  
  
```cpp  
HRESULT ForceGC();  
```  
  
## <a name="remarks"></a><span data-ttu-id="7a0d4-105">Comentários</span><span class="sxs-lookup"><span data-stu-id="7a0d4-105">Remarks</span></span>  
 <span data-ttu-id="7a0d4-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span><span class="sxs-lookup"><span data-stu-id="7a0d4-106">The `ForceGC` method must be called only from a thread that has never run managed code and does not have any profiler callbacks on its stack.</span></span> <span data-ttu-id="7a0d4-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span><span class="sxs-lookup"><span data-stu-id="7a0d4-107">The most convenient implementation is to create a separate thread within the profiler that calls `ForceGC` when signaled.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7a0d4-108">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7a0d4-108">Requirements</span></span>  
 <span data-ttu-id="7a0d4-109">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7a0d4-109">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7a0d4-110">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="7a0d4-110">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7a0d4-111">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7a0d4-111">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7a0d4-112">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7a0d4-112">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7a0d4-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7a0d4-113">See also</span></span>

- [<span data-ttu-id="7a0d4-114">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="7a0d4-114">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
