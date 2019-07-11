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
ms.openlocfilehash: 8bda8079cff8f5e8fafade03a02c3dfe8798c5ca
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740776"
---
# <a name="cordebugsteprange-structure"></a><span data-ttu-id="46d71-102">Estrutura COR_DEBUG_STEP_RANGE</span><span class="sxs-lookup"><span data-stu-id="46d71-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="46d71-103">Contém as informações de deslocamento para um intervalo de código.</span><span class="sxs-lookup"><span data-stu-id="46d71-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="46d71-104">Essa estrutura é usada o [ICorDebugStepper:: Steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="46d71-104">This structure is used by the [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="46d71-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="46d71-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="46d71-106">Membros</span><span class="sxs-lookup"><span data-stu-id="46d71-106">Members</span></span>  
  
|<span data-ttu-id="46d71-107">Membro</span><span class="sxs-lookup"><span data-stu-id="46d71-107">Member</span></span>|<span data-ttu-id="46d71-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="46d71-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="46d71-109">O deslocamento do início do intervalo.</span><span class="sxs-lookup"><span data-stu-id="46d71-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="46d71-110">O deslocamento do final do intervalo.</span><span class="sxs-lookup"><span data-stu-id="46d71-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="46d71-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="46d71-111">Requirements</span></span>  
 <span data-ttu-id="46d71-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="46d71-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="46d71-113">**Cabeçalho:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="46d71-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="46d71-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="46d71-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="46d71-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="46d71-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="46d71-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="46d71-116">See also</span></span>

- [<span data-ttu-id="46d71-117">Método StepRange</span><span class="sxs-lookup"><span data-stu-id="46d71-117">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)
- [<span data-ttu-id="46d71-118">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="46d71-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="46d71-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="46d71-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
