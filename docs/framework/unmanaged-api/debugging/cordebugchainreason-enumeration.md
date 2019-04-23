---
title: Enumeração CorDebugChainReason
ms.date: 03/30/2017
api_name:
- CorDebugChainReason
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugChainReason
helpviewer_keywords:
- CorDebugChainReason enumeration [.NET Framework debugging]
ms.assetid: c915da51-50b2-41df-841a-2b971f4d0975
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: cac790ebbf25ee3095db293ba90612be37fff9b9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59190438"
---
# <a name="cordebugchainreason-enumeration"></a><span data-ttu-id="2ad04-102">Enumeração CorDebugChainReason</span><span class="sxs-lookup"><span data-stu-id="2ad04-102">CorDebugChainReason Enumeration</span></span>
<span data-ttu-id="2ad04-103">Indica o motivo ou os motivos para o início de uma cadeia de chamadas.</span><span class="sxs-lookup"><span data-stu-id="2ad04-103">Indicates the reason or reasons for the initiation of a call chain.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2ad04-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2ad04-104">Syntax</span></span>  
  
```  
typedef enum CorDebugChainReason {  
    CHAIN_NONE              = 0x000,  
    CHAIN_CLASS_INIT        = 0x001,  
    CHAIN_EXCEPTION_FILTER  = 0x002,  
    CHAIN_SECURITY          = 0x004,  
    CHAIN_CONTEXT_POLICY    = 0x008,  
    CHAIN_INTERCEPTION      = 0x010,  
    CHAIN_PROCESS_START     = 0x020,  
    CHAIN_THREAD_START      = 0x040,  
    CHAIN_ENTER_MANAGED     = 0x080,  
    CHAIN_ENTER_UNMANAGED   = 0x100,  
    CHAIN_DEBUGGER_EVAL     = 0x200,  
    CHAIN_CONTEXT_SWITCH    = 0x400,  
    CHAIN_FUNC_EVAL         = 0x800  
} CorDebugChainReason;  
```  
  
## <a name="members"></a><span data-ttu-id="2ad04-105">Membros</span><span class="sxs-lookup"><span data-stu-id="2ad04-105">Members</span></span>  
  
|<span data-ttu-id="2ad04-106">Membro</span><span class="sxs-lookup"><span data-stu-id="2ad04-106">Member</span></span>|<span data-ttu-id="2ad04-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="2ad04-107">Description</span></span>|  
|------------|-----------------|  
|`CHAIN_NONE`|<span data-ttu-id="2ad04-108">Nenhuma cadeia de chamada foi iniciada.</span><span class="sxs-lookup"><span data-stu-id="2ad04-108">No call chain has been initiated.</span></span>|  
|`CHAIN_CLASS_INIT`|<span data-ttu-id="2ad04-109">A cadeia foi iniciada por um construtor.</span><span class="sxs-lookup"><span data-stu-id="2ad04-109">The chain was initiated by a constructor.</span></span>|  
|`CHAIN_EXCEPTION_FILTER`|<span data-ttu-id="2ad04-110">A cadeia foi iniciada por um filtro de exceção.</span><span class="sxs-lookup"><span data-stu-id="2ad04-110">The chain was initiated by an exception filter.</span></span>|  
|`CHAIN_SECURITY`|<span data-ttu-id="2ad04-111">A cadeia foi iniciada pelo código que impõe a segurança.</span><span class="sxs-lookup"><span data-stu-id="2ad04-111">The chain was initiated by code that enforces security.</span></span>|  
|`CHAIN_CONTEXT_POLICY`|<span data-ttu-id="2ad04-112">A cadeia foi iniciada por uma política de contexto.</span><span class="sxs-lookup"><span data-stu-id="2ad04-112">The chain was initiated by a context policy.</span></span>|  
|`CHAIN_INTERCEPTION`|<span data-ttu-id="2ad04-113">Não usado.</span><span class="sxs-lookup"><span data-stu-id="2ad04-113">Not used.</span></span>|  
|`CHAIN_PROCESS_START`|<span data-ttu-id="2ad04-114">Não usado.</span><span class="sxs-lookup"><span data-stu-id="2ad04-114">Not used.</span></span>|  
|`CHAIN_THREAD_START`|<span data-ttu-id="2ad04-115">A cadeia foi iniciada no início de uma execução de thread.</span><span class="sxs-lookup"><span data-stu-id="2ad04-115">The chain was initiated by the start of a thread execution.</span></span>|  
|`CHAIN_ENTER_MANAGED`|<span data-ttu-id="2ad04-116">A cadeia foi iniciada por entrada no código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="2ad04-116">The chain was initiated by entry into managed code.</span></span>|  
|`CHAIN_ENTER_UNMANAGED`|<span data-ttu-id="2ad04-117">A cadeia foi iniciada por entrada de código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="2ad04-117">The chain was initiated by entry into unmanaged code.</span></span>|  
|`CHAIN_DEBUGGER_EVAL`|<span data-ttu-id="2ad04-118">Não usado.</span><span class="sxs-lookup"><span data-stu-id="2ad04-118">Not used.</span></span>|  
|`CHAIN_CONTEXT_SWITCH`|<span data-ttu-id="2ad04-119">Não usado.</span><span class="sxs-lookup"><span data-stu-id="2ad04-119">Not used.</span></span>|  
|`CHAIN_FUNC_EVAL`|<span data-ttu-id="2ad04-120">A cadeia foi iniciada por uma avaliação de função.</span><span class="sxs-lookup"><span data-stu-id="2ad04-120">The chain was initiated by a function evaluation.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2ad04-121">Comentários</span><span class="sxs-lookup"><span data-stu-id="2ad04-121">Remarks</span></span>  
 <span data-ttu-id="2ad04-122">Use o [icordebugchain:: Getreason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) método para determinar as razões para o início de uma cadeia de chamada.</span><span class="sxs-lookup"><span data-stu-id="2ad04-122">Use the [ICorDebugChain::GetReason](../../../../docs/framework/unmanaged-api/debugging/icordebugchain-getreason-method.md) method to ascertain the reasons for the initiation of a call chain.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2ad04-123">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2ad04-123">Requirements</span></span>  
 <span data-ttu-id="2ad04-124">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="2ad04-124">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="2ad04-125">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="2ad04-125">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="2ad04-126">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="2ad04-126">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="2ad04-127">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="2ad04-127">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2ad04-128">Consulte também</span><span class="sxs-lookup"><span data-stu-id="2ad04-128">See also</span></span>

- [<span data-ttu-id="2ad04-129">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="2ad04-129">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
