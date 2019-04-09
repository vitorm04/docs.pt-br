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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59115681"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="1b632-102">Enumeração CorDebugSetContextFlag</span><span class="sxs-lookup"><span data-stu-id="1b632-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="1b632-103">Indica se o contexto é do quadro ativo (ou folha) na pilha ou se foi computado pelo desenrolamento de outro quadro.</span><span class="sxs-lookup"><span data-stu-id="1b632-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1b632-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1b632-104">Syntax</span></span>  
  
```  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="1b632-105">Membros</span><span class="sxs-lookup"><span data-stu-id="1b632-105">Members</span></span>  
  
|<span data-ttu-id="1b632-106">Membro</span><span class="sxs-lookup"><span data-stu-id="1b632-106">Member</span></span>|<span data-ttu-id="1b632-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1b632-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="1b632-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="1b632-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="1b632-109">O contexto é o contexto do thread ativo.</span><span class="sxs-lookup"><span data-stu-id="1b632-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="1b632-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="1b632-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="1b632-111">O contexto foi computado pelo desenrolamento de outro quadro.</span><span class="sxs-lookup"><span data-stu-id="1b632-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1b632-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="1b632-112">Remarks</span></span>  
 `CorDebugSetContextFlag` <span data-ttu-id="1b632-113">fornece valores que são usados pela [icordebugstackwalk:: SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="1b632-113">provides values that are used by the [ICorDebugStackWalk::SetContext](../../../../docs/framework/unmanaged-api/debugging/icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1b632-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1b632-114">Requirements</span></span>  
 <span data-ttu-id="1b632-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1b632-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1b632-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1b632-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1b632-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1b632-117">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="1b632-118">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="1b632-118">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="1b632-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1b632-119">See also</span></span>

- [<span data-ttu-id="1b632-120">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="1b632-120">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="1b632-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="1b632-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
