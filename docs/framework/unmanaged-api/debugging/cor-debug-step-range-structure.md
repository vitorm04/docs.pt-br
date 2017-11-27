---
title: Estrutura COR_DEBUG_STEP_RANGE
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_DEBUG_STEP_RANGE
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_DEBUG_STEP_RANGE
helpviewer_keywords: COR_DEBUG_STEP_RANGE structure [.NET Framework debugging]
ms.assetid: 8809d00e-beaa-4dcf-b4e8-e89d0a5406b7
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 4a696b69cf08d15ecd39a87920ecaa1934c00578
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="cordebugsteprange-structure"></a><span data-ttu-id="a0ac0-102">Estrutura COR_DEBUG_STEP_RANGE</span><span class="sxs-lookup"><span data-stu-id="a0ac0-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="a0ac0-103">Contém as informações de deslocamento para um intervalo de código.</span><span class="sxs-lookup"><span data-stu-id="a0ac0-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="a0ac0-104">Essa estrutura é usada pelo [: Steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="a0ac0-104">This structure is used by the [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a0ac0-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a0ac0-105">Syntax</span></span>  
  
```  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="a0ac0-106">Membros</span><span class="sxs-lookup"><span data-stu-id="a0ac0-106">Members</span></span>  
  
|<span data-ttu-id="a0ac0-107">Membro</span><span class="sxs-lookup"><span data-stu-id="a0ac0-107">Member</span></span>|<span data-ttu-id="a0ac0-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="a0ac0-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="a0ac0-109">O deslocamento do início do intervalo.</span><span class="sxs-lookup"><span data-stu-id="a0ac0-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="a0ac0-110">O deslocamento de final do intervalo.</span><span class="sxs-lookup"><span data-stu-id="a0ac0-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a0ac0-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a0ac0-111">Requirements</span></span>  
 <span data-ttu-id="a0ac0-112">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a0ac0-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a0ac0-113">**Cabeçalho:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="a0ac0-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="a0ac0-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a0ac0-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a0ac0-115">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a0ac0-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0ac0-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a0ac0-116">See Also</span></span>  
 [<span data-ttu-id="a0ac0-117">Método StepRange</span><span class="sxs-lookup"><span data-stu-id="a0ac0-117">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)  
 [<span data-ttu-id="a0ac0-118">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="a0ac0-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="a0ac0-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="a0ac0-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
