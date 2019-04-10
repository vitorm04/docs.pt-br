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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59219675"
---
# <a name="cordebugsteprange-structure"></a><span data-ttu-id="b5a3f-102">Estrutura COR_DEBUG_STEP_RANGE</span><span class="sxs-lookup"><span data-stu-id="b5a3f-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="b5a3f-103">Contém as informações de deslocamento para um intervalo de código.</span><span class="sxs-lookup"><span data-stu-id="b5a3f-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="b5a3f-104">Essa estrutura é usada o [ICorDebugStepper:: Steprange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="b5a3f-104">This structure is used by the [ICorDebugStepper::StepRange](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5a3f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5a3f-105">Syntax</span></span>  
  
```  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="b5a3f-106">Membros</span><span class="sxs-lookup"><span data-stu-id="b5a3f-106">Members</span></span>  
  
|<span data-ttu-id="b5a3f-107">Membro</span><span class="sxs-lookup"><span data-stu-id="b5a3f-107">Member</span></span>|<span data-ttu-id="b5a3f-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="b5a3f-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="b5a3f-109">O deslocamento do início do intervalo.</span><span class="sxs-lookup"><span data-stu-id="b5a3f-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="b5a3f-110">O deslocamento do final do intervalo.</span><span class="sxs-lookup"><span data-stu-id="b5a3f-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="b5a3f-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b5a3f-111">Requirements</span></span>  
 <span data-ttu-id="b5a3f-112">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b5a3f-112">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b5a3f-113">**Cabeçalho:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="b5a3f-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="b5a3f-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b5a3f-114">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="b5a3f-115">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="b5a3f-115">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="b5a3f-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5a3f-116">See also</span></span>

- [<span data-ttu-id="b5a3f-117">Método StepRange</span><span class="sxs-lookup"><span data-stu-id="b5a3f-117">StepRange Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-steprange-method.md)
- [<span data-ttu-id="b5a3f-118">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="b5a3f-118">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="b5a3f-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="b5a3f-119">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
