---
title: Método ICorProfilerInfo::GetHandleFromThread
ms.date: 03/30/2017
api_name:
- ICorProfilerInfo.GetHandleFromThread
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- ICorProfilerInfo::GetHandleFromThread
helpviewer_keywords:
- GetHandleFromThread method [.NET Framework profiling]
- ICorProfilerInfo::GetHandleFromThread method [.NET Framework profiling]
ms.assetid: 36cdc9f5-7579-4cd2-aa36-fc05c741584c
topic_type:
- apiref
ms.openlocfilehash: e508ccd81d25aa3d303456fa88554903ec71d633
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74439057"
---
# <a name="icorprofilerinfogethandlefromthread-method"></a><span data-ttu-id="446b4-102">Método ICorProfilerInfo::GetHandleFromThread</span><span class="sxs-lookup"><span data-stu-id="446b4-102">ICorProfilerInfo::GetHandleFromThread Method</span></span>
<span data-ttu-id="446b4-103">Maps the ID of a thread to a Win32 thread handle.</span><span class="sxs-lookup"><span data-stu-id="446b4-103">Maps the ID of a thread to a Win32 thread handle.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="446b4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="446b4-104">Syntax</span></span>  
  
```cpp  
HRESULT GetHandleFromThread(  
    [in]  ThreadID threadId,  
    [out] HANDLE  *phThread);  
```  
  
## <a name="parameters"></a><span data-ttu-id="446b4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="446b4-105">Parameters</span></span>  
 `threadId`  
 <span data-ttu-id="446b4-106">[in] The thread ID to be mapped.</span><span class="sxs-lookup"><span data-stu-id="446b4-106">[in] The thread ID to be mapped.</span></span>  
  
 `phThread`  
 <span data-ttu-id="446b4-107">[out] A pointer to a Win32 thread handle.</span><span class="sxs-lookup"><span data-stu-id="446b4-107">[out] A pointer to a Win32 thread handle.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="446b4-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="446b4-108">Remarks</span></span>  
 <span data-ttu-id="446b4-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span><span class="sxs-lookup"><span data-stu-id="446b4-109">The profiler must call the Win32 `DuplicateHandle` function on the handle before using it.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="446b4-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="446b4-110">Requirements</span></span>  
 <span data-ttu-id="446b4-111">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="446b4-111">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="446b4-112">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="446b4-112">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="446b4-113">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="446b4-113">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="446b4-114">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="446b4-114">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="446b4-115">Consulte também</span><span class="sxs-lookup"><span data-stu-id="446b4-115">See also</span></span>

- [<span data-ttu-id="446b4-116">Interface ICorProfilerInfo</span><span class="sxs-lookup"><span data-stu-id="446b4-116">ICorProfilerInfo Interface</span></span>](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)
