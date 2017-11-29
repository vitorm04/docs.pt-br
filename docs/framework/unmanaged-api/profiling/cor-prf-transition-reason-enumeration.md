---
title: "Enumeração COR_PRF_TRANSITION_REASON"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_PRF_TRANSITION_REASON
api_location: mscorwks.dll
api_type: COM
f1_keywords: COR_PRF_TRANSITION_REASON
helpviewer_keywords: COR_PRF_TRANSITION_REASON enumeration [.NET Framework profiling]
ms.assetid: da941118-01b7-4197-ae5b-9f2f8adcd623
topic_type: apiref
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 9f11b5fb5409ee30b0456e0c562545718ed46bb6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="corprftransitionreason-enumeration"></a><span data-ttu-id="a6a0c-102">Enumeração COR_PRF_TRANSITION_REASON</span><span class="sxs-lookup"><span data-stu-id="a6a0c-102">COR_PRF_TRANSITION_REASON Enumeration</span></span>
<span data-ttu-id="a6a0c-103">Indica o motivo para uma transição de código gerenciado para não gerenciado ou vice-versa.</span><span class="sxs-lookup"><span data-stu-id="a6a0c-103">Indicates the reason for a transition from managed to unmanaged code, or vice versa.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a6a0c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a6a0c-104">Syntax</span></span>  
  
```  
typedef enum {  
    COR_PRF_TRANSITION_CALL,  
    COR_PRF_TRANSITION_RETURN  
} COR_PRF_TRANSITION_REASON;  
```  
  
## <a name="members"></a><span data-ttu-id="a6a0c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="a6a0c-105">Members</span></span>  
  
|<span data-ttu-id="a6a0c-106">Membro</span><span class="sxs-lookup"><span data-stu-id="a6a0c-106">Member</span></span>|<span data-ttu-id="a6a0c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a6a0c-107">Description</span></span>|  
|------------|-----------------|  
|`COR_PRF_TRANSITION_CALL`|<span data-ttu-id="a6a0c-108">A transição é devido a uma chamada em uma função.</span><span class="sxs-lookup"><span data-stu-id="a6a0c-108">The transition is due to a call into a function.</span></span>|  
|`COR_PRF_TRANSITION_RETURN`|<span data-ttu-id="a6a0c-109">A transição é devido a um retorno de uma função.</span><span class="sxs-lookup"><span data-stu-id="a6a0c-109">The transition is due to a return from a function.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a6a0c-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="a6a0c-110">Remarks</span></span>  
 <span data-ttu-id="a6a0c-111">Quando uma transição ocorre, o criador de perfil recebe um [: Managedtounmanagedtransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) ou [: Unmanagedtomanagedtransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) retorno de chamada, que Fornece um valor de `COR_PRF_TRANSITION_REASON` enumeração para indicar o motivo da transição.</span><span class="sxs-lookup"><span data-stu-id="a6a0c-111">When a transition occurs, the profiler receives an [ICorProfilerCallback::ManagedToUnmanagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-managedtounmanagedtransition-method.md) or [ICorProfilerCallback::UnmanagedToManagedTransition](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-unmanagedtomanagedtransition-method.md) callback, either of which provides a value of the `COR_PRF_TRANSITION_REASON` enumeration to indicate the reason for the transition.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a6a0c-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a6a0c-112">Requirements</span></span>  
 <span data-ttu-id="a6a0c-113">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a6a0c-113">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a6a0c-114">**Cabeçalho:** Corprof. idl, CorProf.h</span><span class="sxs-lookup"><span data-stu-id="a6a0c-114">**Header:** CorProf.idl, CorProf.h</span></span>  
  
 <span data-ttu-id="a6a0c-115">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a6a0c-115">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a6a0c-116">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a6a0c-116">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>
