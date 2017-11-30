---
title: Estrutura COR_FIELD
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: COR_FIELD
api_location: mscordbi.dll
api_type: COM
f1_keywords: COR_FIELD
helpviewer_keywords: COR_FIELD structure [.NET Framework debugging]
ms.assetid: c0822423-a9df-4961-950d-50dcc152f863
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: a01687b5a49bb64ab037dc408c8cc5bd381be589
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="corfield-structure"></a><span data-ttu-id="47323-102">Estrutura COR_FIELD</span><span class="sxs-lookup"><span data-stu-id="47323-102">COR_FIELD Structure</span></span>
<span data-ttu-id="47323-103">Fornece informações sobre um campo em um objeto.</span><span class="sxs-lookup"><span data-stu-id="47323-103">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="47323-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="47323-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="47323-105">Membros</span><span class="sxs-lookup"><span data-stu-id="47323-105">Members</span></span>  
  
|<span data-ttu-id="47323-106">Membro</span><span class="sxs-lookup"><span data-stu-id="47323-106">Member</span></span>|<span data-ttu-id="47323-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="47323-107">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="47323-108">Um `mdFieldDef` token que pode ser usado para obter informações de campo.</span><span class="sxs-lookup"><span data-stu-id="47323-108">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="47323-109">O deslocamento, em bytes, para os dados do campo no objeto.</span><span class="sxs-lookup"><span data-stu-id="47323-109">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="47323-110">Um [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) valor que identifica o tipo do campo.</span><span class="sxs-lookup"><span data-stu-id="47323-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="47323-111">Um valor de enumeração CorElementType que indica o tipo do campo.</span><span class="sxs-lookup"><span data-stu-id="47323-111">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="47323-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="47323-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="47323-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="47323-113">Requirements</span></span>  
 <span data-ttu-id="47323-114">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="47323-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="47323-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="47323-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="47323-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="47323-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="47323-117">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="47323-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="47323-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="47323-118">See Also</span></span>  
 [<span data-ttu-id="47323-119">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="47323-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="47323-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="47323-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
