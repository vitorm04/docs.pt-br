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
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59175923"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="17499-102">Enumeração CorDebugUnmappedStop</span><span class="sxs-lookup"><span data-stu-id="17499-102">CorDebugUnmappedStop Enumeration</span></span>
<span data-ttu-id="17499-103">Especifica o tipo de código não mapeado que pode disparar uma interrupção na execução do código pelo passador.</span><span class="sxs-lookup"><span data-stu-id="17499-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17499-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17499-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="17499-105">Membros</span><span class="sxs-lookup"><span data-stu-id="17499-105">Members</span></span>  
  
|<span data-ttu-id="17499-106">Membro</span><span class="sxs-lookup"><span data-stu-id="17499-106">Member</span></span>|<span data-ttu-id="17499-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="17499-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="17499-108">Não pare em qualquer tipo de código não mapeado.</span><span class="sxs-lookup"><span data-stu-id="17499-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="17499-109">Interrompa no código de prólogo.</span><span class="sxs-lookup"><span data-stu-id="17499-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="17499-110">Interrompa no código de epílogo.</span><span class="sxs-lookup"><span data-stu-id="17499-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="17499-111">Interrompa no código que não tem nenhuma informação de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="17499-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="17499-112">Interrompa no código não mapeado que não se ajustam o prólogo, epílogo, nenhuma informação de mapeamento ou categoria não gerenciada.</span><span class="sxs-lookup"><span data-stu-id="17499-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="17499-113">Pare em código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="17499-113">Stop in unmanaged code.</span></span> <span data-ttu-id="17499-114">Esse valor é válido somente com depuração interop.</span><span class="sxs-lookup"><span data-stu-id="17499-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="17499-115">Pare em todos os tipos de código não mapeado.</span><span class="sxs-lookup"><span data-stu-id="17499-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="17499-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="17499-116">Remarks</span></span>  
 <span data-ttu-id="17499-117">Use o [ICorDebugStepper:: Setunmappedstopmask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) método para definir os sinalizadores que especificam o código não mapeado no qual o escalonador será interrompida.</span><span class="sxs-lookup"><span data-stu-id="17499-117">Use the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17499-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="17499-118">Requirements</span></span>  
 <span data-ttu-id="17499-119">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="17499-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="17499-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="17499-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="17499-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="17499-121">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="17499-122">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="17499-122">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="17499-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17499-123">See also</span></span>

- [<span data-ttu-id="17499-124">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="17499-124">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
