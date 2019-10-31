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
ms.openlocfilehash: 206e4fb232f4786a76525d24aa379b25d6d2f71d
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73099355"
---
# <a name="cor_debug_step_range-structure"></a><span data-ttu-id="d37ad-102">Estrutura COR_DEBUG_STEP_RANGE</span><span class="sxs-lookup"><span data-stu-id="d37ad-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="d37ad-103">Contém as informações de deslocamento para um intervalo de código.</span><span class="sxs-lookup"><span data-stu-id="d37ad-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="d37ad-104">Essa estrutura é usada pelo método [ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md) .</span><span class="sxs-lookup"><span data-stu-id="d37ad-104">This structure is used by the [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d37ad-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d37ad-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="d37ad-106">Membros</span><span class="sxs-lookup"><span data-stu-id="d37ad-106">Members</span></span>  
  
|<span data-ttu-id="d37ad-107">Membro</span><span class="sxs-lookup"><span data-stu-id="d37ad-107">Member</span></span>|<span data-ttu-id="d37ad-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="d37ad-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="d37ad-109">O deslocamento do início do intervalo.</span><span class="sxs-lookup"><span data-stu-id="d37ad-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="d37ad-110">O deslocamento do final do intervalo.</span><span class="sxs-lookup"><span data-stu-id="d37ad-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="d37ad-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d37ad-111">Requirements</span></span>  
 <span data-ttu-id="d37ad-112">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d37ad-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d37ad-113">**Cabeçalho:** CorDebug. idl</span><span class="sxs-lookup"><span data-stu-id="d37ad-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="d37ad-114">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d37ad-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d37ad-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d37ad-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d37ad-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d37ad-116">See also</span></span>

- [<span data-ttu-id="d37ad-117">Método StepRange</span><span class="sxs-lookup"><span data-stu-id="d37ad-117">StepRange Method</span></span>](icordebugstepper-steprange-method.md)
- [<span data-ttu-id="d37ad-118">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="d37ad-118">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="d37ad-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="d37ad-119">Debugging</span></span>](index.md)
