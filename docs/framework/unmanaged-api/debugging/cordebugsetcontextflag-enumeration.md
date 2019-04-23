---
title: Enumeração CorDebugSetContextFlag
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5754968511f7b2db48f60b99748f10f5d27e8d21
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59115681"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="2af77-102">Enumeração CorDebugSetContextFlag</span><span class="sxs-lookup"><span data-stu-id="2af77-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="2af77-103">Indica se o contexto é do quadro ativo (ou folha) na pilha ou se foi computado pelo desenrolamento de outro quadro.</span><span class="sxs-lookup"><span data-stu-id="2af77-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2af77-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2af77-104">Syntax</span></span>  
  
```  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="2af77-105">Membros</span><span class="sxs-lookup"><span data-stu-id="2af77-105">Members</span></span>  
  
|<span data-ttu-id="2af77-106">Membro</span><span class="sxs-lookup"><span data-stu-id="2af77-106">Member</span></span>|<span data-ttu-id="2af77-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2af77-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="2af77-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="2af77-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="2af77-109">O contexto é o contexto do thread ativo.</span><span class="sxs-lookup"><span data-stu-id="2af77-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="2af77-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="2af77-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="2af77-111">O contexto foi computado pelo desenrolamento de outro quadro.</span><span class="sxs-lookup"><span data-stu-id="2af77-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2af77-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="2af77-112">Remarks</span></span>  
 <span data-ttu-id="2af77-113">`CorDebugSetContextFlag` fornece valores que são usados pela [icordebugstackwalk:: SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="2af77-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2af77-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2af77-114">Requirements</span></span>  
 <span data-ttu-id="2af77-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2af77-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2af77-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2af77-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2af77-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2af77-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2af77-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2af77-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2af77-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2af77-119">See also</span></span>

- [<span data-ttu-id="2af77-120">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="2af77-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="2af77-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="2af77-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
