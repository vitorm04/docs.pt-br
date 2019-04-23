---
title: Estrutura CorDebugExceptionObjectStackFrame
ms.date: 03/30/2017
api_name:
- CorDebugExceptionObjectStackFrame
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugExceptionObjectStackFrame
helpviewer_keywords:
- CorDebugExceptionObjectStackFrame structure [.NET Framework debugging]
ms.assetid: 542cdd81-5ae7-4361-b0ef-1ae4775df258
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 5a4cd4d353c22921ed3dba1dc08fe2cee7e429f8
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59173076"
---
# <a name="cordebugexceptionobjectstackframe-structure"></a><span data-ttu-id="f9f61-102">Estrutura CorDebugExceptionObjectStackFrame</span><span class="sxs-lookup"><span data-stu-id="f9f61-102">CorDebugExceptionObjectStackFrame Structure</span></span>
<span data-ttu-id="f9f61-103">Representa informações de quadro de pilha de um objeto de exceção.</span><span class="sxs-lookup"><span data-stu-id="f9f61-103">Represents stack frame information from an exception object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f9f61-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f9f61-104">Syntax</span></span>  
  
```  
typedef struct CorDebugExceptionObjectStackFrame {  
    ICorDebugModule* pModule;  
    CORDB_ADDRESS ip;  
    mdMethodDef methodDef;  
    BOOL isLastForeignExceptionFrame;  
} CorDebugExceptionObjectStackFrame;  
```  
  
## <a name="members"></a><span data-ttu-id="f9f61-105">Membros</span><span class="sxs-lookup"><span data-stu-id="f9f61-105">Members</span></span>  
  
|<span data-ttu-id="f9f61-106">Membro</span><span class="sxs-lookup"><span data-stu-id="f9f61-106">Member</span></span>|<span data-ttu-id="f9f61-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="f9f61-107">Description</span></span>|  
|------------|-----------------|  
|`pModule`|<span data-ttu-id="f9f61-108">Um ponteiro para o objeto ICorDebugModule para o quadro atual.</span><span class="sxs-lookup"><span data-stu-id="f9f61-108">A pointer to the ICorDebugModule object for the current frame.</span></span>|  
|`ip`|<span data-ttu-id="f9f61-109">O valor do ponteiro de instrução (EIP/RIP) para o quadro atual.</span><span class="sxs-lookup"><span data-stu-id="f9f61-109">The value of the instruction pointer (EIP/RIP) for the current frame.</span></span>|  
|`methodDef`|<span data-ttu-id="f9f61-110">O token de método para o quadro atual.</span><span class="sxs-lookup"><span data-stu-id="f9f61-110">The method token for the current frame.</span></span>|  
|`isLastForeignExceptionFrame`|<span data-ttu-id="f9f61-111">Um valor que indica se o quadro é o último quadro em uma exceção externa.</span><span class="sxs-lookup"><span data-stu-id="f9f61-111">A value that indicates whether the frame is the last frame in a foreign exception.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f9f61-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="f9f61-112">Remarks</span></span>  
 <span data-ttu-id="f9f61-113">O chamador deve liberar o ponteiro para o objeto ICorDebugModule depois que ele não está mais em uso.</span><span class="sxs-lookup"><span data-stu-id="f9f61-113">The caller must release the pointer to the ICorDebugModule object once it is no longer in use.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f9f61-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f9f61-114">Requirements</span></span>  
 <span data-ttu-id="f9f61-115">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="f9f61-115">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="f9f61-116">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="f9f61-116">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="f9f61-117">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="f9f61-117">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="f9f61-118">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="f9f61-118">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9f61-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f9f61-119">See also</span></span>

- [<span data-ttu-id="f9f61-120">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="f9f61-120">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="f9f61-121">Depuração</span><span class="sxs-lookup"><span data-stu-id="f9f61-121">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
