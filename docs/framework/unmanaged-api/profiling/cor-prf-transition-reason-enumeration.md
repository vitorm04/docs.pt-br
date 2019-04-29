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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2556196b7c8f81709e6880962e8ff36e126dd8b0
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61599033"
---
# <a name="corprftransitionreason-enumeration"></a><span data-ttu-id="1cedd-102">Enumeração COR_PRF_TRANSITION_REASON</span><span class="sxs-lookup"><span data-stu-id="1cedd-102">COR_PRF_TRANSITION_REASON Enumeration</span></span>
<span data-ttu-id="1cedd-103">Indica o motivo para uma transição de código gerenciado para não gerenciado ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="1cedd-103">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1cedd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1cedd-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="1cedd-105">Membros</span><span class="sxs-lookup"><span data-stu-id="1cedd-105">Members</span></span>  
  
|<span data-ttu-id="1cedd-106">Membro</span><span class="sxs-lookup"><span data-stu-id="1cedd-106">Member</span></span>|<span data-ttu-id="1cedd-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1cedd-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="1cedd-108">A transição é devido a uma chamada para uma função.</span><span class="sxs-lookup"><span data-stu-id="1cedd-108">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="1cedd-109">A transição é devido a um retorno de uma função.</span><span class="sxs-lookup"><span data-stu-id="1cedd-109">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1cedd-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="1cedd-110">Remarks</span></span>  
 <span data-ttu-id="1cedd-111">Quando uma transição ocorre, o criador de perfil recebe um [ICorProfilerCallback:: Managedtounmanagedtransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) ou [ICorProfilerCallback:: Unmanagedtomanagedtransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) retorno de chamada, que Fornece um valor da `COR_PRF_TRANSITION_REASON` enumeração para indicar o motivo para a transição.</span><span class="sxs-lookup"><span data-stu-id="1cedd-111">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1cedd-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1cedd-112">Requirements</span></span>  
 <span data-ttu-id="1cedd-113">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1cedd-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1cedd-114">**Cabeçalho:** CorProf.idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="1cedd-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="1cedd-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1cedd-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1cedd-116">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1cedd-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
