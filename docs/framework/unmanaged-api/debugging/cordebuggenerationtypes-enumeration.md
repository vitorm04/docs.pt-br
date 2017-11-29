---
title: "Enumeração CorDebugGenerationTypes"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CorDebugGenerationTypes
api_location: mscordbi.dll
api_type: COM
f1_keywords: CorDebugGenerationTypes
helpviewer_keywords: CorDebugGenerationTypes enumeration [.NET Framework debugging]
ms.assetid: 9f25b64f-eedd-4ae5-8b0e-cfdfb9b6c5d8
topic_type: apiref
caps.latest.revision: "3"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: adefc0de4ba09419660c214df75365c90ec2c66e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="cordebuggenerationtypes-enumeration"></a><span data-ttu-id="9cdcd-102">Enumeração CorDebugGenerationTypes</span><span class="sxs-lookup"><span data-stu-id="9cdcd-102">CorDebugGenerationTypes Enumeration</span></span>
<span data-ttu-id="9cdcd-103">Especifica a geração de uma região de memória no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="9cdcd-103">Specifies the generation of a region of memory on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cdcd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9cdcd-104">Syntax</span></span>  
  
```  
typedef enum CorDebugGenerationTypes {  
    CorDebug_Gen0 = 0,  
    CorDebug_Gen1 = 1,  
    CorDebug_Gen2 = 2,  
    CorDebug_LOH  = 3,  
} CorDebugRegionTypes;  
```  
  
## <a name="members"></a><span data-ttu-id="9cdcd-105">Membros</span><span class="sxs-lookup"><span data-stu-id="9cdcd-105">Members</span></span>  
  
|<span data-ttu-id="9cdcd-106">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="9cdcd-106">Member name</span></span>|<span data-ttu-id="9cdcd-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="9cdcd-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorDebug_Gen0`|<span data-ttu-id="9cdcd-108">Geração 0.</span><span class="sxs-lookup"><span data-stu-id="9cdcd-108">Generation 0.</span></span>|  
|`CorDebug_Gen1`|<span data-ttu-id="9cdcd-109">Geração 1.</span><span class="sxs-lookup"><span data-stu-id="9cdcd-109">Generation 1.</span></span>|  
|`CorDebug_Gen2`|<span data-ttu-id="9cdcd-110">Geração 2.</span><span class="sxs-lookup"><span data-stu-id="9cdcd-110">Generation 2.</span></span>|  
|`CorDebug_LOH`|<span data-ttu-id="9cdcd-111">Heap de objeto grande.</span><span class="sxs-lookup"><span data-stu-id="9cdcd-111">The large object heap.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cdcd-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="9cdcd-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="9cdcd-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="9cdcd-113">Requirements</span></span>  
 <span data-ttu-id="9cdcd-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="9cdcd-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="9cdcd-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="9cdcd-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="9cdcd-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="9cdcd-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="9cdcd-117">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="9cdcd-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cdcd-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9cdcd-118">See Also</span></span>  
 [<span data-ttu-id="9cdcd-119">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="9cdcd-119">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
