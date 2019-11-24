---
title: Enumeração COR_PRF_TRANSITION_REASON
ms.date: 03/30/2017
api_name:
- COR_PRF_TRANSITION_REASON
api_location:
- mscorwks.dll
api_type:
- COM
f1_keywords:
- COR_PRF_TRANSITION_REASON
helpviewer_keywords:
- COR_PRF_TRANSITION_REASON enumeration [.NET Framework profiling]
ms.assetid: da941118-01b7-4197-ae5b-9f2f8adcd623
topic_type:
- apiref
ms.openlocfilehash: 6d8b408675127cde399a8346f2b9734a0e038cb5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74427143"
---
# <a name="cor_prf_transition_reason-enumeration"></a><span data-ttu-id="2b867-102">Enumeração COR_PRF_TRANSITION_REASON</span><span class="sxs-lookup"><span data-stu-id="2b867-102">COR_PRF_TRANSITION_REASON Enumeration</span></span>
<span data-ttu-id="2b867-103">Indica o motivo para uma transição de código gerenciado para não gerenciado ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="2b867-103">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2b867-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2b867-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="2b867-105">Membros</span><span class="sxs-lookup"><span data-stu-id="2b867-105">Members</span></span>  
  
|<span data-ttu-id="2b867-106">Membro</span><span class="sxs-lookup"><span data-stu-id="2b867-106">Member</span></span>|<span data-ttu-id="2b867-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2b867-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="2b867-108">The transition is due to a call into a function.</span><span class="sxs-lookup"><span data-stu-id="2b867-108">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="2b867-109">The transition is due to a return from a function.</span><span class="sxs-lookup"><span data-stu-id="2b867-109">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2b867-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="2b867-110">Remarks</span></span>  
 <span data-ttu-id="2b867-111">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span><span class="sxs-lookup"><span data-stu-id="2b867-111">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2b867-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2b867-112">Requirements</span></span>  
 <span data-ttu-id="2b867-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2b867-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2b867-114">**Header:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="2b867-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="2b867-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2b867-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2b867-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2b867-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
