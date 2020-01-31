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
ms.openlocfilehash: 1c3c311fd431b6c0b18af3d6516973b2471cfabd
ms.sourcegitcommit: b11efd71c3d5ce3d9449c8d4345481b9f21392c6
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/29/2020
ms.locfileid: "76867036"
---
# <a name="cor_prf_transition_reason-enumeration"></a><span data-ttu-id="7b57b-102">Enumeração COR_PRF_TRANSITION_REASON</span><span class="sxs-lookup"><span data-stu-id="7b57b-102">COR_PRF_TRANSITION_REASON Enumeration</span></span>
<span data-ttu-id="7b57b-103">Indica o motivo para uma transição de código gerenciado para não gerenciado ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="7b57b-103">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b57b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7b57b-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="7b57b-105">Membros</span><span class="sxs-lookup"><span data-stu-id="7b57b-105">Members</span></span>  
  
|<span data-ttu-id="7b57b-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="7b57b-106">Member</span></span>|<span data-ttu-id="7b57b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="7b57b-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="7b57b-108">A transição é devido a uma chamada em uma função.</span><span class="sxs-lookup"><span data-stu-id="7b57b-108">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="7b57b-109">A transição é devido a um retorno de uma função.</span><span class="sxs-lookup"><span data-stu-id="7b57b-109">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7b57b-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="7b57b-110">Remarks</span></span>  
 <span data-ttu-id="7b57b-111">Quando ocorre uma transição, o criador de perfil recebe um retorno de chamada [ICorProfilerCallback:: ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) ou [ICorProfilerCallback:: UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) , o que fornece um valor da enumeração `COR_PRF_TRANSITION_REASON` para indicar o motivo da transição.</span><span class="sxs-lookup"><span data-stu-id="7b57b-111">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7b57b-112">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="7b57b-112">Requirements</span></span>  
 <span data-ttu-id="7b57b-113">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7b57b-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7b57b-114">**Cabeçalho:** CorProf. idl, CorProf. h</span><span class="sxs-lookup"><span data-stu-id="7b57b-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="7b57b-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="7b57b-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="7b57b-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7b57b-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
