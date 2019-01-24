---
title: Estrutura COR_FIELD
ms.date: 03/30/2017
api_name:
- COR_FIELD
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_FIELD
helpviewer_keywords:
- COR_FIELD structure [.NET Framework debugging]
ms.assetid: c0822423-a9df-4961-950d-50dcc152f863
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d570f9392bbd66f0d9031c776b139ee3b30541b1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698213"
---
# <a name="corfield-structure"></a><span data-ttu-id="3e91f-102">Estrutura COR_FIELD</span><span class="sxs-lookup"><span data-stu-id="3e91f-102">COR_FIELD Structure</span></span>
<span data-ttu-id="3e91f-103">Fornece informações sobre um campo em um objeto.</span><span class="sxs-lookup"><span data-stu-id="3e91f-103">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e91f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3e91f-104">Syntax</span></span>  
  
```  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="3e91f-105">Membros</span><span class="sxs-lookup"><span data-stu-id="3e91f-105">Members</span></span>  
  
|<span data-ttu-id="3e91f-106">Membro</span><span class="sxs-lookup"><span data-stu-id="3e91f-106">Member</span></span>|<span data-ttu-id="3e91f-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="3e91f-107">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="3e91f-108">Um `mdFieldDef` token que pode ser usado para obter informações de campo.</span><span class="sxs-lookup"><span data-stu-id="3e91f-108">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="3e91f-109">O deslocamento, em bytes, para os dados do campo no objeto.</span><span class="sxs-lookup"><span data-stu-id="3e91f-109">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="3e91f-110">Um [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) valor que identifica o tipo desse campo.</span><span class="sxs-lookup"><span data-stu-id="3e91f-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="3e91f-111">Um valor de enumeração CorElementType que indica o tipo do campo.</span><span class="sxs-lookup"><span data-stu-id="3e91f-111">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e91f-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="3e91f-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3e91f-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3e91f-113">Requirements</span></span>  
 <span data-ttu-id="3e91f-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3e91f-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3e91f-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="3e91f-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="3e91f-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="3e91f-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="3e91f-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3e91f-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e91f-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3e91f-118">See also</span></span>
- [<span data-ttu-id="3e91f-119">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="3e91f-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="3e91f-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="3e91f-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
