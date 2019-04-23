---
title: Estrutura COR_DEBUG_STEP_RANGE
ms.date: 03/30/2017
api_name:
- COR_DEBUG_STEP_RANGE
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_DEBUG_STEP_RANGE
helpviewer_keywords:
- COR_DEBUG_STEP_RANGE structure [.NET Framework debugging]
ms.assetid: 8809d00e-beaa-4dcf-b4e8-e89d0a5406b7
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 57d7c3256d7b52a4e55dbb5bc420b0438983d2f2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59219675"
---
# <a name="cordebugsteprange-structure"></a><span data-ttu-id="540e2-102">Estrutura COR_DEBUG_STEP_RANGE</span><span class="sxs-lookup"><span data-stu-id="540e2-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="540e2-103">Contém as informações de deslocamento para um intervalo de código.</span><span class="sxs-lookup"><span data-stu-id="540e2-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="540e2-104">Essa estrutura é usada o [ICorDebugStepper:: Steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="540e2-104">This structure is used by the [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="540e2-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="540e2-105">Syntax</span></span>  
  
```  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="540e2-106">Membros</span><span class="sxs-lookup"><span data-stu-id="540e2-106">Members</span></span>  
  
|<span data-ttu-id="540e2-107">Membro</span><span class="sxs-lookup"><span data-stu-id="540e2-107">Member</span></span>|<span data-ttu-id="540e2-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="540e2-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="540e2-109">O deslocamento do início do intervalo.</span><span class="sxs-lookup"><span data-stu-id="540e2-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="540e2-110">O deslocamento do final do intervalo.</span><span class="sxs-lookup"><span data-stu-id="540e2-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="540e2-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="540e2-111">Requirements</span></span>  
 <span data-ttu-id="540e2-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="540e2-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="540e2-113">**Cabeçalho:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="540e2-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="540e2-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="540e2-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="540e2-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="540e2-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="540e2-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="540e2-116">See also</span></span>

- [<span data-ttu-id="540e2-117">Método StepRange</span><span class="sxs-lookup"><span data-stu-id="540e2-117">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)
- [<span data-ttu-id="540e2-118">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="540e2-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="540e2-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="540e2-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
