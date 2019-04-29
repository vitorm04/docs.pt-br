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
ms.openlocfilehash: c1cea8adcd12ecb3078e4469e6b018ed49064e0b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723310"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="bb413-102">Enumeração CorDebugUnmappedStop</span><span class="sxs-lookup"><span data-stu-id="bb413-102">CorDebugUnmappedStop Enumeration</span></span>
<span data-ttu-id="bb413-103">Especifica o tipo de código não mapeado que pode disparar uma interrupção na execução do código pelo passador.</span><span class="sxs-lookup"><span data-stu-id="bb413-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bb413-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bb413-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="bb413-105">Membros</span><span class="sxs-lookup"><span data-stu-id="bb413-105">Members</span></span>  
  
|<span data-ttu-id="bb413-106">Membro</span><span class="sxs-lookup"><span data-stu-id="bb413-106">Member</span></span>|<span data-ttu-id="bb413-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb413-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="bb413-108">Não pare em qualquer tipo de código não mapeado.</span><span class="sxs-lookup"><span data-stu-id="bb413-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="bb413-109">Interrompa no código de prólogo.</span><span class="sxs-lookup"><span data-stu-id="bb413-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="bb413-110">Interrompa no código de epílogo.</span><span class="sxs-lookup"><span data-stu-id="bb413-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="bb413-111">Interrompa no código que não tem nenhuma informação de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="bb413-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="bb413-112">Interrompa no código não mapeado que não se ajustam o prólogo, epílogo, nenhuma informação de mapeamento ou categoria não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="bb413-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="bb413-113">Pare em código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="bb413-113">Stop in unmanaged code.</span></span> <span data-ttu-id="bb413-114">Esse valor é válido somente com depuração interop.</span><span class="sxs-lookup"><span data-stu-id="bb413-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="bb413-115">Pare em todos os tipos de código não mapeado.</span><span class="sxs-lookup"><span data-stu-id="bb413-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb413-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="bb413-116">Remarks</span></span>  
 <span data-ttu-id="bb413-117">Use o [ICorDebugStepper:: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) método para definir os sinalizadores que especificam o código não mapeado no qual o escalonador será interrompida.</span><span class="sxs-lookup"><span data-stu-id="bb413-117">Use the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb413-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bb413-118">Requirements</span></span>  
 <span data-ttu-id="bb413-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb413-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb413-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb413-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb413-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb413-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb413-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb413-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb413-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb413-123">See also</span></span>

- [<span data-ttu-id="bb413-124">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="bb413-124">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
