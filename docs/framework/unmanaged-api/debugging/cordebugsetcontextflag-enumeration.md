---
title: "Enumeração CorDebugSetContextFlag"
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
- CorDebugSetContextFlag
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugSetContextFlag
helpviewer_keywords:
- CorDebugSetContextFlag enumeration [.NET Framework debugging]
ms.assetid: b30280bb-fe75-44ed-8589-bcff081fae44
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 27e9fd561da74a3b88015e7820c2cbbd56ab2a7a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="586cd-102">Enumeração CorDebugSetContextFlag</span><span class="sxs-lookup"><span data-stu-id="586cd-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="586cd-103">Indica se o contexto é do quadro ativo (ou folha) na pilha ou se foi computado pelo desenrolamento de outro quadro.</span><span class="sxs-lookup"><span data-stu-id="586cd-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="586cd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="586cd-104">Syntax</span></span>  
  
```  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="586cd-105">Membros</span><span class="sxs-lookup"><span data-stu-id="586cd-105">Members</span></span>  
  
|<span data-ttu-id="586cd-106">Membro</span><span class="sxs-lookup"><span data-stu-id="586cd-106">Member</span></span>|<span data-ttu-id="586cd-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="586cd-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="586cd-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="586cd-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="586cd-109">O contexto é o contexto do thread ativo.</span><span class="sxs-lookup"><span data-stu-id="586cd-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="586cd-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="586cd-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="586cd-111">O contexto foi calculado pelo desenrolamento de outro quadro.</span><span class="sxs-lookup"><span data-stu-id="586cd-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="586cd-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="586cd-112">Remarks</span></span>  
 <span data-ttu-id="586cd-113">`CorDebugSetContextFlag`fornece valores que são usados pelo [Icordebugstackwalk](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="586cd-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="586cd-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="586cd-114">Requirements</span></span>  
 <span data-ttu-id="586cd-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="586cd-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="586cd-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="586cd-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="586cd-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="586cd-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="586cd-118">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="586cd-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="586cd-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="586cd-119">See Also</span></span>  
 [<span data-ttu-id="586cd-120">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="586cd-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [<span data-ttu-id="586cd-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="586cd-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
