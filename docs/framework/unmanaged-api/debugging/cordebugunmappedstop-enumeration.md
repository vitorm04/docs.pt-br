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
ms.openlocfilehash: 772f1f0dee260ad3752b2f89e5fbe0d6bc27b87b
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795645"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="a1e05-102">Enumeração CorDebugUnmappedStop</span><span class="sxs-lookup"><span data-stu-id="a1e05-102">CorDebugUnmappedStop Enumeration</span></span>
<span data-ttu-id="a1e05-103">Especifica o tipo de código não mapeado que pode disparar uma interrupção na execução do código pelo passador.</span><span class="sxs-lookup"><span data-stu-id="a1e05-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a1e05-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a1e05-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="a1e05-105">Membros</span><span class="sxs-lookup"><span data-stu-id="a1e05-105">Members</span></span>  
  
|<span data-ttu-id="a1e05-106">Membro</span><span class="sxs-lookup"><span data-stu-id="a1e05-106">Member</span></span>|<span data-ttu-id="a1e05-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a1e05-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="a1e05-108">Não pare em nenhum tipo de código não mapeado.</span><span class="sxs-lookup"><span data-stu-id="a1e05-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="a1e05-109">Parar no código de prólogo.</span><span class="sxs-lookup"><span data-stu-id="a1e05-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="a1e05-110">Pare no código epílogo.</span><span class="sxs-lookup"><span data-stu-id="a1e05-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="a1e05-111">Pare no código que não tem informações de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="a1e05-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="a1e05-112">Pare no código não mapeado que não caiba nas categorias prólogo, epílogo, no-Mapping-Information ou unmanaged.</span><span class="sxs-lookup"><span data-stu-id="a1e05-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="a1e05-113">Parar em código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="a1e05-113">Stop in unmanaged code.</span></span> <span data-ttu-id="a1e05-114">Esse valor é válido somente com depuração de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="a1e05-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="a1e05-115">Parar em todos os tipos de código não mapeado.</span><span class="sxs-lookup"><span data-stu-id="a1e05-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a1e05-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="a1e05-116">Remarks</span></span>  
 <span data-ttu-id="a1e05-117">Use o método [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) para definir os sinalizadores que especificam o código não mapeado no qual o stepper será interrompido.</span><span class="sxs-lookup"><span data-stu-id="a1e05-117">Use the [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a1e05-118">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a1e05-118">Requirements</span></span>  
 <span data-ttu-id="a1e05-119">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a1e05-119">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a1e05-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a1e05-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a1e05-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a1e05-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="a1e05-122">**.NET Framework versões:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="a1e05-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1e05-123">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a1e05-123">See also</span></span>

- [<span data-ttu-id="a1e05-124">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="a1e05-124">Debugging Enumerations</span></span>](debugging-enumerations.md)
