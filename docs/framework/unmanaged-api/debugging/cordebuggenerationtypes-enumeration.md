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
ms.openlocfilehash: 0443f58b79e60111756308cc4843daf86d1fc823
ms.sourcegitcommit: de7f589de07a9979b6ac28f54c3e534a617d9425
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/05/2020
ms.locfileid: "82795859"
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="d685a-102">Enumeração CorDebugGenerationTypes</span><span class="sxs-lookup"><span data-stu-id="d685a-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="d685a-103">Especifica a geração de uma região de memória no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="d685a-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d685a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="d685a-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="d685a-105">Membros</span><span class="sxs-lookup"><span data-stu-id="d685a-105">Members</span></span>  
  
|<span data-ttu-id="d685a-106">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="d685a-106">Member name</span></span>|<span data-ttu-id="d685a-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="d685a-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="d685a-108">Geração 0.</span><span class="sxs-lookup"><span data-stu-id="d685a-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="d685a-109">Geração 1.</span><span class="sxs-lookup"><span data-stu-id="d685a-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="d685a-110">Geração 2.</span><span class="sxs-lookup"><span data-stu-id="d685a-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="d685a-111">A heap de objeto grande.</span><span class="sxs-lookup"><span data-stu-id="d685a-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d685a-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="d685a-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d685a-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d685a-113">Requirements</span></span>  
 <span data-ttu-id="d685a-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d685a-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d685a-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d685a-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d685a-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d685a-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d685a-117">**.NET Framework versões:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d685a-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d685a-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d685a-118">See also</span></span>

- [<span data-ttu-id="d685a-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="d685a-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
