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
ms.openlocfilehash: 16c4e03667d4af3ab5cc8b653d77f15eaef25843
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54691821"
---
# <a name="cordebugmappingresult-enumeration"></a><span data-ttu-id="d92c2-102">Enumeração CorDebugMappingResult</span><span class="sxs-lookup"><span data-stu-id="d92c2-102">CorDebugMappingResult Enumeration</span></span>
<span data-ttu-id="d92c2-103">Fornece os detalhes sobre como o valor do ponteiro de instrução (IP) foi obtido.</span><span class="sxs-lookup"><span data-stu-id="d92c2-103">Provides the details of how the value of the instruction pointer (IP) was obtained.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d92c2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d92c2-104">Syntax</span></span>  
  
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
  
## <a name="members"></a><span data-ttu-id="d92c2-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d92c2-105">Members</span></span>  
  
|<span data-ttu-id="d92c2-106">Membro</span><span class="sxs-lookup"><span data-stu-id="d92c2-106">Member</span></span>|<span data-ttu-id="d92c2-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d92c2-107">Description</span></span>|  
|------------|-----------------|  
|`MAPPING_PROLOG`|<span data-ttu-id="d92c2-108">O código nativo está no prólogo, portanto, o valor do IP é 0.</span><span class="sxs-lookup"><span data-stu-id="d92c2-108">The native code is in the prolog, so the value of the IP is 0.</span></span>|  
|`MAPPING_EPILOG`|<span data-ttu-id="d92c2-109">O código nativo está em um epílogo, portanto, o valor do IP é o endereço da última instrução do método.</span><span class="sxs-lookup"><span data-stu-id="d92c2-109">The native code is in an epilog, so the value of the IP is the address of the last instruction of the method.</span></span>|  
|`MAPPING_NO_INFO`|<span data-ttu-id="d92c2-110">Nenhuma informação de mapeamento está disponível para o método, portanto, o valor do IP é 0.</span><span class="sxs-lookup"><span data-stu-id="d92c2-110">No mapping information is available for the method, so the value of the IP is 0.</span></span>|  
|`MAPPING_UNMAPPED_ADDRESS`|<span data-ttu-id="d92c2-111">Embora haja informações de mapeamento para o método, o endereço atual não pode ser mapeado para o código Microsoft intermediate language (MSIL).</span><span class="sxs-lookup"><span data-stu-id="d92c2-111">Although there is mapping information for the method, the current address cannot be mapped to Microsoft intermediate language (MSIL) code.</span></span> <span data-ttu-id="d92c2-112">O valor do IP é 0.</span><span class="sxs-lookup"><span data-stu-id="d92c2-112">The value of the IP is 0.</span></span>|  
|`MAPPING_EXACT`|<span data-ttu-id="d92c2-113">O método mapeia exatamente para o código MSIL ou o quadro foi interpretado, portanto, o valor do IP é preciso.</span><span class="sxs-lookup"><span data-stu-id="d92c2-113">Either the method maps exactly to MSIL code or the frame has been interpreted, so the value of the IP is accurate.</span></span>|  
|`MAPPING_APPROXIMATE`|<span data-ttu-id="d92c2-114">O método foi mapeado com êxito, mas o valor do IP pode ser aproximado.</span><span class="sxs-lookup"><span data-stu-id="d92c2-114">The method was successfully mapped, but the value of the IP may be approximate.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d92c2-115">Comentários</span><span class="sxs-lookup"><span data-stu-id="d92c2-115">Remarks</span></span>  
 <span data-ttu-id="d92c2-116">Você pode usar o [icordebugilframe:: Getip](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) método para obter o valor do ponteiro de instrução.</span><span class="sxs-lookup"><span data-stu-id="d92c2-116">You can use the [ICorDebugILFrame::GetIP](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe-getip-method.md) method to obtain the value of the instruction pointer.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d92c2-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d92c2-117">Requirements</span></span>  
 <span data-ttu-id="d92c2-118">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d92c2-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d92c2-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d92c2-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d92c2-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d92c2-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d92c2-121">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d92c2-121">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d92c2-122">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d92c2-122">See also</span></span>
- [<span data-ttu-id="d92c2-123">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="d92c2-123">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
