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
ms.openlocfilehash: 2efe159eaa8b49d4d3825e9737593d0a12fc4d4c
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67740739"
---
# <a name="corfield-structure"></a><span data-ttu-id="1243b-102">Estrutura COR_FIELD</span><span class="sxs-lookup"><span data-stu-id="1243b-102">COR_FIELD Structure</span></span>
<span data-ttu-id="1243b-103">Fornece informações sobre um campo em um objeto.</span><span class="sxs-lookup"><span data-stu-id="1243b-103">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1243b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1243b-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="1243b-105">Membros</span><span class="sxs-lookup"><span data-stu-id="1243b-105">Members</span></span>  
  
|<span data-ttu-id="1243b-106">Membro</span><span class="sxs-lookup"><span data-stu-id="1243b-106">Member</span></span>|<span data-ttu-id="1243b-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="1243b-107">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="1243b-108">Um `mdFieldDef` token que pode ser usado para obter informações de campo.</span><span class="sxs-lookup"><span data-stu-id="1243b-108">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="1243b-109">O deslocamento, em bytes, para os dados do campo no objeto.</span><span class="sxs-lookup"><span data-stu-id="1243b-109">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="1243b-110">Um [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) valor que identifica o tipo desse campo.</span><span class="sxs-lookup"><span data-stu-id="1243b-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="1243b-111">Um valor de enumeração CorElementType que indica o tipo do campo.</span><span class="sxs-lookup"><span data-stu-id="1243b-111">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1243b-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="1243b-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1243b-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1243b-113">Requirements</span></span>  
 <span data-ttu-id="1243b-114">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1243b-114">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1243b-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="1243b-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="1243b-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="1243b-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="1243b-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1243b-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1243b-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1243b-118">See also</span></span>

- [<span data-ttu-id="1243b-119">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="1243b-119">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="1243b-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="1243b-120">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
