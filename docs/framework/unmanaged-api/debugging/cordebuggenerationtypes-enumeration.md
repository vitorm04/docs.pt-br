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
ms.openlocfilehash: 6133b34a60fd06c1b75d69783760741b8de62071
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789350"
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="12f32-102">Enumeração CorDebugGenerationTypes</span><span class="sxs-lookup"><span data-stu-id="12f32-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="12f32-103">Especifica a geração de uma região de memória no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="12f32-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="12f32-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="12f32-104">Syntax</span></span>  
  
```cpp  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="12f32-105">Membros</span><span class="sxs-lookup"><span data-stu-id="12f32-105">Members</span></span>  
  
|<span data-ttu-id="12f32-106">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="12f32-106">Member name</span></span>|<span data-ttu-id="12f32-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="12f32-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="12f32-108">Geração 0.</span><span class="sxs-lookup"><span data-stu-id="12f32-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="12f32-109">Geração 1.</span><span class="sxs-lookup"><span data-stu-id="12f32-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="12f32-110">Geração 2.</span><span class="sxs-lookup"><span data-stu-id="12f32-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="12f32-111">A heap de objeto grande.</span><span class="sxs-lookup"><span data-stu-id="12f32-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="12f32-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="12f32-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="12f32-113">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="12f32-113">Requirements</span></span>  
 <span data-ttu-id="12f32-114">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="12f32-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="12f32-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="12f32-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="12f32-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="12f32-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="12f32-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="12f32-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12f32-118">Veja também</span><span class="sxs-lookup"><span data-stu-id="12f32-118">See also</span></span>

- [<span data-ttu-id="12f32-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="12f32-119">Debugging Enumerations</span></span>](debugging-enumerations.md)
