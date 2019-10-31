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
ms.openlocfilehash: cc02f63808b1929b93777c8bbc67c47000b0b424
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132740"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="597ba-102">Enumeração CorDebugUnmappedStop</span><span class="sxs-lookup"><span data-stu-id="597ba-102">CorDebugUnmappedStop Enumeration</span></span>
<span data-ttu-id="597ba-103">Especifica o tipo de código não mapeado que pode disparar uma interrupção na execução do código pelo passador.</span><span class="sxs-lookup"><span data-stu-id="597ba-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="597ba-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="597ba-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="597ba-105">Membros</span><span class="sxs-lookup"><span data-stu-id="597ba-105">Members</span></span>  
  
|<span data-ttu-id="597ba-106">Membro</span><span class="sxs-lookup"><span data-stu-id="597ba-106">Member</span></span>|<span data-ttu-id="597ba-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="597ba-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="597ba-108">Não pare em nenhum tipo de código não mapeado.</span><span class="sxs-lookup"><span data-stu-id="597ba-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="597ba-109">Parar no código de prólogo.</span><span class="sxs-lookup"><span data-stu-id="597ba-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="597ba-110">Pare no código epílogo.</span><span class="sxs-lookup"><span data-stu-id="597ba-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="597ba-111">Pare no código que não tem informações de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="597ba-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="597ba-112">Pare no código não mapeado que não caiba nas categorias prólogo, epílogo, no-Mapping-Information ou unmanaged.</span><span class="sxs-lookup"><span data-stu-id="597ba-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="597ba-113">Parar em código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="597ba-113">Stop in unmanaged code.</span></span> <span data-ttu-id="597ba-114">Esse valor é válido somente com depuração de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="597ba-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="597ba-115">Parar em todos os tipos de código não mapeado.</span><span class="sxs-lookup"><span data-stu-id="597ba-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="597ba-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="597ba-116">Remarks</span></span>  
 <span data-ttu-id="597ba-117">Use o método [ICorDebugStepper:: SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) para definir os sinalizadores que especificam o código não mapeado no qual o stepper será interrompido.</span><span class="sxs-lookup"><span data-stu-id="597ba-117">Use the [ICorDebugStepper::SetUnmappedStopMask](../../../../docs/framework/unmanaged-api/debugging/icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="597ba-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="597ba-118">Requirements</span></span>  
 <span data-ttu-id="597ba-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="597ba-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="597ba-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="597ba-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="597ba-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="597ba-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="597ba-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="597ba-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="597ba-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="597ba-123">See also</span></span>

- [<span data-ttu-id="597ba-124">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="597ba-124">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
