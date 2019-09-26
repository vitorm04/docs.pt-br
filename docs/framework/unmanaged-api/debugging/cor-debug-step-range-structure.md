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
ms.openlocfilehash: 11d5e2eb5e2743fca4876ed09add79be3eba514f
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274198"
---
# <a name="cor_debug_step_range-structure"></a><span data-ttu-id="3a309-102">Estrutura COR_DEBUG_STEP_RANGE</span><span class="sxs-lookup"><span data-stu-id="3a309-102">COR_DEBUG_STEP_RANGE Structure</span></span>
<span data-ttu-id="3a309-103">Contém as informações de deslocamento para um intervalo de código.</span><span class="sxs-lookup"><span data-stu-id="3a309-103">Contains the offset information for a range of code.</span></span>  
  
 <span data-ttu-id="3a309-104">Essa estrutura é usada pelo método [ICorDebugStepper:: StepRange](icordebugstepper-steprange-method.md) .</span><span class="sxs-lookup"><span data-stu-id="3a309-104">This structure is used by the [ICorDebugStepper::StepRange](icordebugstepper-steprange-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3a309-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3a309-105">Syntax</span></span>  
  
```cpp  
typedef struct {  
    ULONG32 startOffset;  
    ULONG32 endOffset;  
} COR_DEBUG_STEP_RANGE;  
```  
  
## <a name="members"></a><span data-ttu-id="3a309-106">Membros</span><span class="sxs-lookup"><span data-stu-id="3a309-106">Members</span></span>  
  
|<span data-ttu-id="3a309-107">Membro</span><span class="sxs-lookup"><span data-stu-id="3a309-107">Member</span></span>|<span data-ttu-id="3a309-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="3a309-108">Description</span></span>|  
|------------|-----------------|  
|`startOffset`|<span data-ttu-id="3a309-109">O deslocamento do início do intervalo.</span><span class="sxs-lookup"><span data-stu-id="3a309-109">The offset of the beginning of the range.</span></span>|  
|`endOffset`|<span data-ttu-id="3a309-110">O deslocamento do final do intervalo.</span><span class="sxs-lookup"><span data-stu-id="3a309-110">The offset of the end of the range.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="3a309-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3a309-111">Requirements</span></span>  
 <span data-ttu-id="3a309-112">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3a309-112">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3a309-113">**Cabeçalho:** CorDebug.idl</span><span class="sxs-lookup"><span data-stu-id="3a309-113">**Header:** CorDebug.idl</span></span>  
  
 <span data-ttu-id="3a309-114">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3a309-114">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3a309-115">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3a309-115">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a309-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3a309-116">See also</span></span>

- [<span data-ttu-id="3a309-117">Método StepRange</span><span class="sxs-lookup"><span data-stu-id="3a309-117">StepRange Method</span></span>](icordebugstepper-steprange-method.md)
- [<span data-ttu-id="3a309-118">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="3a309-118">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="3a309-119">Depuração</span><span class="sxs-lookup"><span data-stu-id="3a309-119">Debugging</span></span>](index.md)
