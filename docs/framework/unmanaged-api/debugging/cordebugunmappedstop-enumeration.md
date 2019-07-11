---
title: Enumeração CorDebugUnmappedStop
ms.date: 03/30/2017
api_name:
- CorDebugUnmappedStop
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugUnmappedStop
helpviewer_keywords:
- CorDebugUnmappedStop enumeration [.NET Framework debugging]
ms.assetid: a684f7d7-d0c2-4690-b721-639e613f11f8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c2ea0bf215c0d2abfe9beb29d736f893073d3be8
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67739516"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="92916-102">Enumeração CorDebugUnmappedStop</span><span class="sxs-lookup"><span data-stu-id="92916-102">CorDebugUnmappedStop Enumeration</span></span>
<span data-ttu-id="92916-103">Especifica o tipo de código não mapeado que pode disparar uma interrupção na execução do código pelo passador.</span><span class="sxs-lookup"><span data-stu-id="92916-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="92916-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="92916-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugUnmappedStop {  
    STOP_NONE               = 0x0,  
    STOP_PROLOG             = 0x01,  
    STOP_EPILOG             = 0x02,  
    STOP_NO_MAPPING_INFO    = 0x04,  
    STOP_OTHER_UNMAPPED     = 0x08,  
    STOP_UNMANAGED          = 0x10,  
    STOP_ALL                = 0xffff,  
} CorDebugUnmappedStop;  
```  
  
## <a name="members"></a><span data-ttu-id="92916-105">Membros</span><span class="sxs-lookup"><span data-stu-id="92916-105">Members</span></span>  
  
|<span data-ttu-id="92916-106">Membro</span><span class="sxs-lookup"><span data-stu-id="92916-106">Member</span></span>|<span data-ttu-id="92916-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="92916-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="92916-108">Não pare em qualquer tipo de código não mapeado.</span><span class="sxs-lookup"><span data-stu-id="92916-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="92916-109">Interrompa no código de prólogo.</span><span class="sxs-lookup"><span data-stu-id="92916-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="92916-110">Interrompa no código de epílogo.</span><span class="sxs-lookup"><span data-stu-id="92916-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="92916-111">Interrompa no código que não tem nenhuma informação de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="92916-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="92916-112">Interrompa no código não mapeado que não se ajustam o prólogo, epílogo, nenhuma informação de mapeamento ou categoria não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="92916-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="92916-113">Pare em código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="92916-113">Stop in unmanaged code.</span></span> <span data-ttu-id="92916-114">Esse valor é válido somente com depuração interop.</span><span class="sxs-lookup"><span data-stu-id="92916-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="92916-115">Pare em todos os tipos de código não mapeado.</span><span class="sxs-lookup"><span data-stu-id="92916-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="92916-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="92916-116">Remarks</span></span>  
 <span data-ttu-id="92916-117">Use o [ICorDebugStepper:: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) método para definir os sinalizadores que especificam o código não mapeado no qual o escalonador será interrompida.</span><span class="sxs-lookup"><span data-stu-id="92916-117">Use the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="92916-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="92916-118">Requirements</span></span>  
 <span data-ttu-id="92916-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="92916-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="92916-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="92916-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="92916-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="92916-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="92916-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="92916-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92916-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="92916-123">See also</span></span>

- [<span data-ttu-id="92916-124">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="92916-124">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
