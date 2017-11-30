---
title: Estrutura CorDebugExceptionObjectStackFrame
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugExceptionObjectStackFrame
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugExceptionObjectStackFrame
helpviewer_keywords: CorDebugExceptionObjectStackFrame structure [.NET Framework debugging]
ms.assetid: 542cdd81-5ae7-4361-b0ef-1ae4775df258
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: cf166f606aa2c0e0900356395c36bd6875897e3d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="e621c-102">Estrutura CorDebugExceptionObjectStackFrame</span><span class="sxs-lookup"><span data-stu-id="e621c-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="e621c-103">Representa informações de quadro de pilha de um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="e621c-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e621c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e621c-104">Syntax</span></span>  
  
```  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="e621c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e621c-105">Members</span></span>  
  
|<span data-ttu-id="e621c-106">Membro</span><span class="sxs-lookup"><span data-stu-id="e621c-106">Member</span></span>|<span data-ttu-id="e621c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e621c-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="e621c-108">Um ponteiro para o objeto ICorDebugModule para o quadro atual.</span><span class="sxs-lookup"><span data-stu-id="e621c-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="e621c-109">O valor do ponteiro de instrução (EIP/RIP) para o quadro atual.</span><span class="sxs-lookup"><span data-stu-id="e621c-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="e621c-110">O token de método para o quadro atual.</span><span class="sxs-lookup"><span data-stu-id="e621c-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="e621c-111">Um valor que indica se o quadro é o último quadro de uma exceção externa.</span><span class="sxs-lookup"><span data-stu-id="e621c-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e621c-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="e621c-112">Remarks</span></span>  
 <span data-ttu-id="e621c-113">O chamador deve liberar o ponteiro para o objeto ICorDebugModule depois que ele não está mais em uso.</span><span class="sxs-lookup"><span data-stu-id="e621c-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e621c-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e621c-114">Requirements</span></span>  
 <span data-ttu-id="e621c-115">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e621c-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e621c-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e621c-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e621c-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e621c-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e621c-118">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e621c-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e621c-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e621c-119">See Also</span></span>  
 [<span data-ttu-id="e621c-120">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="e621c-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="e621c-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="e621c-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
