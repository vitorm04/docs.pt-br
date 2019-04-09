---
title: Enumeração CorDebugGenerationTypes
ms.date: 03/30/2017
api_name:
- CorDebugGenerationTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugGenerationTypes
helpviewer_keywords:
- CorDebugGenerationTypes enumeration [.NET Framework debugging]
ms.assetid: 9f25b64f-eedd-4ae5-8b0e-cfdfb9b6c5d8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c1707a09f14fbab6150c2ecbcd188d7bf88064fa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59085890"
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="e6a04-102">Enumeração CorDebugGenerationTypes</span><span class="sxs-lookup"><span data-stu-id="e6a04-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="e6a04-103">Especifica a geração de uma região de memória no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e6a04-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e6a04-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e6a04-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="e6a04-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e6a04-105">Members</span></span>  
  
|<span data-ttu-id="e6a04-106">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="e6a04-106">Member name</span></span>|<span data-ttu-id="e6a04-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e6a04-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="e6a04-108">Geração 0.</span><span class="sxs-lookup"><span data-stu-id="e6a04-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="e6a04-109">Geração 1.</span><span class="sxs-lookup"><span data-stu-id="e6a04-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="e6a04-110">Geração 2.</span><span class="sxs-lookup"><span data-stu-id="e6a04-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="e6a04-111">O heap de objeto grande.</span><span class="sxs-lookup"><span data-stu-id="e6a04-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e6a04-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="e6a04-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e6a04-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e6a04-113">Requirements</span></span>  
 <span data-ttu-id="e6a04-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e6a04-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e6a04-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e6a04-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e6a04-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e6a04-116">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="e6a04-117">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="e6a04-117">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e6a04-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e6a04-118">See also</span></span>

- [<span data-ttu-id="e6a04-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="e6a04-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
