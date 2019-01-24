---
title: Enumeração CorDebugStateChange
ms.date: 03/30/2017
api_name:
- CorDebugStateChange
api_location:
- mscordbi.dll
api_type:
- COM
ms.assetid: 1d4424ab-5143-4e50-a84a-ceeb4ddf3bba
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 0f0f692b692628d50755ce813c66823f940dccb8
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513771"
---
# <a name="cordebugstatechange-enumeration"></a><span data-ttu-id="d3812-102">Enumeração CorDebugStateChange</span><span class="sxs-lookup"><span data-stu-id="d3812-102">CorDebugStateChange Enumeration</span></span>
<span data-ttu-id="d3812-103">Descreve a quantidade de dados armazenados em cache que devem ser descartados com base em alterações no processo.</span><span class="sxs-lookup"><span data-stu-id="d3812-103">Describes the amount of cached data that must be discarded based on changes to the process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d3812-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d3812-104">Syntax</span></span>  
  
```  
typedef enum CorDebugStateChange  
{  
    PROCESS_RUNNING = 0x0000001,   
    FLUSH_ALL       = 0x0000002,   
} CorDebugStateChange;  
```  
  
## <a name="members"></a><span data-ttu-id="d3812-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d3812-105">Members</span></span>  
  
|<span data-ttu-id="d3812-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d3812-106">Member</span></span>|<span data-ttu-id="d3812-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d3812-107">Description</span></span>|  
|------------|-----------------|  
|`PROCESS_RUNNING`|<span data-ttu-id="d3812-108">O processo atingiu um novo estado de memória por meio da execução do encaminhamento.</span><span class="sxs-lookup"><span data-stu-id="d3812-108">The process reached a new memory state via forward execution.</span></span>|  
|`SET_CONTEXT_FLAG_UNWIND_FRAME`|<span data-ttu-id="d3812-109">A memória do processo pode ser arbitrariamente diferente do que era anteriormente.</span><span class="sxs-lookup"><span data-stu-id="d3812-109">The process' memory may be arbitrarily different than it was previously.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d3812-110">Comentários</span><span class="sxs-lookup"><span data-stu-id="d3812-110">Remarks</span></span>  
 <span data-ttu-id="d3812-111">Um membro do `CorDebugStateChange` enumeração é fornecida como um argumento quando o depurador chama o [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) método</span><span class="sxs-lookup"><span data-stu-id="d3812-111">A member of the `CorDebugStateChange` enumeration is provided as an argument when the debugger calls the [ProcessStateChanged](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess6-processstatechanged-method.md) method</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d3812-112">Essa enumeração destina-se para uso no .NET Native somente para cenários de depuração.</span><span class="sxs-lookup"><span data-stu-id="d3812-112">This enumeration is intended for use in .NET Native debugging scenarios only.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d3812-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d3812-113">Requirements</span></span>  
 <span data-ttu-id="d3812-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d3812-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d3812-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d3812-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d3812-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d3812-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d3812-117">**Versões do .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d3812-117">**.NET Framework Versions:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d3812-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d3812-118">See also</span></span>
- [<span data-ttu-id="d3812-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="d3812-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [<span data-ttu-id="d3812-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="d3812-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
