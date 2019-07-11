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
ms.openlocfilehash: 193f5ffe96e89a00bed8a3c88ee346ba3ea9f2b4
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740021"
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="32d58-102">Enumeração CorDebugGenerationTypes</span><span class="sxs-lookup"><span data-stu-id="32d58-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="32d58-103">Especifica a geração de uma região de memória no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="32d58-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="32d58-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="32d58-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="32d58-105">Membros</span><span class="sxs-lookup"><span data-stu-id="32d58-105">Members</span></span>  
  
|<span data-ttu-id="32d58-106">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="32d58-106">Member name</span></span>|<span data-ttu-id="32d58-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="32d58-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="32d58-108">Geração 0.</span><span class="sxs-lookup"><span data-stu-id="32d58-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="32d58-109">Geração 1.</span><span class="sxs-lookup"><span data-stu-id="32d58-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="32d58-110">Geração 2.</span><span class="sxs-lookup"><span data-stu-id="32d58-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="32d58-111">O heap de objeto grande.</span><span class="sxs-lookup"><span data-stu-id="32d58-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="32d58-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="32d58-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="32d58-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="32d58-113">Requirements</span></span>  
 <span data-ttu-id="32d58-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="32d58-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="32d58-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="32d58-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="32d58-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="32d58-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="32d58-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="32d58-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="32d58-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="32d58-118">See also</span></span>

- [<span data-ttu-id="32d58-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="32d58-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
