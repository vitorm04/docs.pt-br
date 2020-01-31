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
ms.openlocfilehash: 23e168b0f322a580917c3fcfcb767a7d4d4628f6
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793880"
---
# <a name="cordebugunmappedstop-enumeration"></a><span data-ttu-id="99464-102">Enumeração CorDebugUnmappedStop</span><span class="sxs-lookup"><span data-stu-id="99464-102">CorDebugUnmappedStop Enumeration</span></span>
<span data-ttu-id="99464-103">Especifica o tipo de código não mapeado que pode disparar uma interrupção na execução do código pelo passador.</span><span class="sxs-lookup"><span data-stu-id="99464-103">Specifies the type of unmapped code that can trigger a halt in code execution by the stepper.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="99464-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="99464-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="99464-105">Membros</span><span class="sxs-lookup"><span data-stu-id="99464-105">Members</span></span>  
  
|<span data-ttu-id="99464-106">{1&gt;Membro&lt;1}</span><span class="sxs-lookup"><span data-stu-id="99464-106">Member</span></span>|<span data-ttu-id="99464-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="99464-107">Description</span></span>|  
|------------|-----------------|  
|`STOP_NONE`|<span data-ttu-id="99464-108">Não pare em nenhum tipo de código não mapeado.</span><span class="sxs-lookup"><span data-stu-id="99464-108">Do not stop in any type of unmapped code.</span></span>|  
|`STOP_PROLOG`|<span data-ttu-id="99464-109">Parar no código de prólogo.</span><span class="sxs-lookup"><span data-stu-id="99464-109">Stop in prolog code.</span></span>|  
|`STOP_EPILOG`|<span data-ttu-id="99464-110">Pare no código epílogo.</span><span class="sxs-lookup"><span data-stu-id="99464-110">Stop in epilog code.</span></span>|  
|`STOP_NO_MAPPING_INFO`|<span data-ttu-id="99464-111">Pare no código que não tem informações de mapeamento.</span><span class="sxs-lookup"><span data-stu-id="99464-111">Stop in code that has no mapping information.</span></span>|  
|`STOP_OTHER_UNMAPPED`|<span data-ttu-id="99464-112">Pare no código não mapeado que não caiba nas categorias prólogo, epílogo, no-Mapping-Information ou unmanaged.</span><span class="sxs-lookup"><span data-stu-id="99464-112">Stop in unmapped code that does not fit into the prolog, epilog, no-mapping-information, or unmanaged category.</span></span>|  
|`STOP_UNMANAGED`|<span data-ttu-id="99464-113">Parar em código não gerenciado.</span><span class="sxs-lookup"><span data-stu-id="99464-113">Stop in unmanaged code.</span></span> <span data-ttu-id="99464-114">Esse valor é válido somente com depuração de interoperabilidade.</span><span class="sxs-lookup"><span data-stu-id="99464-114">This value is valid only with interop debugging.</span></span>|  
|`STOP_ALL`|<span data-ttu-id="99464-115">Parar em todos os tipos de código não mapeado.</span><span class="sxs-lookup"><span data-stu-id="99464-115">Stop in all types of unmapped code.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="99464-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="99464-116">Remarks</span></span>  
 <span data-ttu-id="99464-117">Use o método [ICorDebugStepper:: SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) para definir os sinalizadores que especificam o código não mapeado no qual o stepper será interrompido.</span><span class="sxs-lookup"><span data-stu-id="99464-117">Use the [ICorDebugStepper::SetUnmappedStopMask](icordebugstepper-setunmappedstopmask-method.md) method to set the flags that specify the unmapped code in which the stepper will stop.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="99464-118">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="99464-118">Requirements</span></span>  
 <span data-ttu-id="99464-119">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="99464-119">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="99464-120">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="99464-120">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="99464-121">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="99464-121">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="99464-122">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="99464-122">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="99464-123">Veja também</span><span class="sxs-lookup"><span data-stu-id="99464-123">See also</span></span>

- [<span data-ttu-id="99464-124">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="99464-124">Debugging Enumerations</span></span>](debugging-enumerations.md)
