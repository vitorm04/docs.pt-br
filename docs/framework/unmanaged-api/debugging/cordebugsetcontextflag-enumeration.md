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
ms.openlocfilehash: a3214fc4e52918716f183720c7c616b1fff74bdb
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795671"
---
# <a name="cordebugsetcontextflag-enumeration"></a><span data-ttu-id="48aa4-102">Enumeração CorDebugSetContextFlag</span><span class="sxs-lookup"><span data-stu-id="48aa4-102">CorDebugSetContextFlag Enumeration</span></span>
<span data-ttu-id="48aa4-103">Indica se o contexto é do quadro ativo (ou folha) na pilha ou se foi computado pelo desenrolamento de outro quadro.</span><span class="sxs-lookup"><span data-stu-id="48aa4-103">Indicates whether the context is from the active (or leaf) frame on the stack or has been computed by unwinding from another frame.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="48aa4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="48aa4-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugSetContextFlag  
{  
   SET_CONTEXT_FLAG_ACTIVE_FRAME = 1  
   SET_CONTEXT_FLAG_UNWIND_FRAME = 2  
}  CorDebugSetContextFlag;  
```  
  
## <a name="members"></a><span data-ttu-id="48aa4-105">Membros</span><span class="sxs-lookup"><span data-stu-id="48aa4-105">Members</span></span>  
  
|<span data-ttu-id="48aa4-106">Membro</span><span class="sxs-lookup"><span data-stu-id="48aa4-106">Member</span></span>|<span data-ttu-id="48aa4-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="48aa4-107">Description</span></span>|  
|------------|-----------------|  
|<span data-ttu-id="48aa4-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span><span class="sxs-lookup"><span data-stu-id="48aa4-108">SET_CONTEXT_FLAG_ACTIVE_FRAME</span></span>|<span data-ttu-id="48aa4-109">O contexto é o contexto ativo do thread.</span><span class="sxs-lookup"><span data-stu-id="48aa4-109">The context is the thread’s active context.</span></span>|  
|<span data-ttu-id="48aa4-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span><span class="sxs-lookup"><span data-stu-id="48aa4-110">SET_CONTEXT_FLAG_UNWIND_FRAME</span></span>|<span data-ttu-id="48aa4-111">O contexto foi calculado com o desenrolamento de outro quadro.</span><span class="sxs-lookup"><span data-stu-id="48aa4-111">The context has been computed by unwinding from another frame.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="48aa4-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="48aa4-112">Remarks</span></span>  
 <span data-ttu-id="48aa4-113">`CorDebugSetContextFlag`Fornece valores que são usados pelo método [ICorDebugStackWalk:: SetContext](icordebugstackwalk-setcontext-method.md) .</span><span class="sxs-lookup"><span data-stu-id="48aa4-113">`CorDebugSetContextFlag` provides values that are used by the [ICorDebugStackWalk::SetContext](icordebugstackwalk-setcontext-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="48aa4-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="48aa4-114">Requirements</span></span>  
 <span data-ttu-id="48aa4-115">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="48aa4-115">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="48aa4-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="48aa4-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="48aa4-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="48aa4-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="48aa4-118">**.NET Framework versões:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="48aa4-118">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="48aa4-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="48aa4-119">See also</span></span>

- [<span data-ttu-id="48aa4-120">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="48aa4-120">Debugging Enumerations</span></span>](debugging-enumerations.md)
- [<span data-ttu-id="48aa4-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="48aa4-121">Debugging</span></span>](index.md)
