---
title: Enumeração CorDebugMappingResult
ms.date: 03/30/2017
api_name:
- CorDebugMappingResult
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugMappingResult
helpviewer_keywords:
- CorDebugMappingResult enumeration [.NET Framework debugging]
ms.assetid: 701281dd-2936-45c8-a1f0-3bf7332b093b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7ca3f5a6af6ea19ec81af3f6ac0a028440f80d56
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="cordebugmappingresult-enumeration"></a><span data-ttu-id="8b64b-102">Enumeração CorDebugMappingResult</span><span class="sxs-lookup"><span data-stu-id="8b64b-102">CorDebugMappingResult Enumeration</span></span>
<span data-ttu-id="8b64b-103">Fornece os detalhes sobre como o valor do ponteiro de instrução (IP) foi obtido.</span><span class="sxs-lookup"><span data-stu-id="8b64b-103">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8b64b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="8b64b-104">Syntax</span></span>  
  
```  
typedef enum CorDebugMappingResult {  
    MAPPING_PROLOG              = 0x1,  
    MAPPING_EPILOG              = 0x2,  
    MAPPING_NO_INFO             = 0x4,  
    MAPPING_UNMAPPED_ADDRESS    = 0x8,  
    MAPPING_EXACT               = 0x10,  
    MAPPING_APPROXIMATE         = 0x20,  
} CorDebugMappingResult;  
```  
  
## <a name="members"></a><span data-ttu-id="8b64b-105">Membros</span><span class="sxs-lookup"><span data-stu-id="8b64b-105">Members</span></span>  
  
|<span data-ttu-id="8b64b-106">Membro</span><span class="sxs-lookup"><span data-stu-id="8b64b-106">Member</span></span>|<span data-ttu-id="8b64b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="8b64b-107">Description</span></span>|  
|------------|-----------------|  
|`MAPPING_PROLOG`|<span data-ttu-id="8b64b-108">O código nativo está no prólogo, portanto, o valor do IP é 0.</span><span class="sxs-lookup"><span data-stu-id="8b64b-108">The native code is in the prolog, so the value of the IP is 0.</span></span>|  
|`MAPPING_EPILOG`|<span data-ttu-id="8b64b-109">O código nativo está em um epílogo, portanto, o valor do IP é o endereço da última instrução do método.</span><span class="sxs-lookup"><span data-stu-id="8b64b-109">The native code is in an epilog, so the value of the IP is the address of the last instruction of the method.</span></span>|  
|`MAPPING_NO_INFO`|<span data-ttu-id="8b64b-110">Nenhuma informação de mapeamento está disponível para o método, portanto, o valor do IP é 0.</span><span class="sxs-lookup"><span data-stu-id="8b64b-110">No mapping information is available for the method, so the value of the IP is 0.</span></span>|  
|`MAPPING_UNMAPPED_ADDRESS`|<span data-ttu-id="8b64b-111">Embora não haja informações de mapeamento para o método, o endereço atual não pode ser mapeado para o código Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="8b64b-111">Although there is mapping information for the method, the current address cannot be mapped to Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="8b64b-112">O valor do IP é 0.</span><span class="sxs-lookup"><span data-stu-id="8b64b-112">The value of the IP is 0.</span></span>|  
|`MAPPING_EXACT`|<span data-ttu-id="8b64b-113">O método mapeia exatamente ao código MSIL tanto o quadro foi interpretado, portanto, o valor do IP é preciso.</span><span class="sxs-lookup"><span data-stu-id="8b64b-113">Either the method maps exactly to MSIL code or the frame has been interpreted, so the value of the IP is accurate.</span></span>|  
|`MAPPING_APPROXIMATE`|<span data-ttu-id="8b64b-114">O método foi mapeado com êxito, mas o valor do IP pode ser aproximado.</span><span class="sxs-lookup"><span data-stu-id="8b64b-114">The method was successfully mapped, but the value of the IP may be approximate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8b64b-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="8b64b-115">Remarks</span></span>  
 <span data-ttu-id="8b64b-116">Você pode usar o [Icordebugilframe](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) método para obter o valor do ponteiro de instrução.</span><span class="sxs-lookup"><span data-stu-id="8b64b-116">You can use the [ICorDebugILFrame::GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) method to obtain the value of the instruction pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="8b64b-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="8b64b-117">Requirements</span></span>  
 <span data-ttu-id="8b64b-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="8b64b-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="8b64b-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="8b64b-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="8b64b-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="8b64b-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="8b64b-121">**Versões do .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="8b64b-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8b64b-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="8b64b-122">See Also</span></span>  
 [<span data-ttu-id="8b64b-123">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="8b64b-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
