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
ms.openlocfilehash: 78e34d9d33d34047e3ebd2effb4894bc7b709585
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73132350"
---
# <a name="cor_field-structure"></a><span data-ttu-id="cc963-102">Estrutura COR_FIELD</span><span class="sxs-lookup"><span data-stu-id="cc963-102">COR_FIELD Structure</span></span>
<span data-ttu-id="cc963-103">Fornece informações sobre um campo em um objeto.</span><span class="sxs-lookup"><span data-stu-id="cc963-103">Provides information about a field in an object.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cc963-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cc963-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_FIELD{  
    mdFieldDef token;  
    ULONG32 offset;  
    COR_TYPEID id;  
    CorElementType fieldType;  
} COR_FIELD;  
```  
  
## <a name="members"></a><span data-ttu-id="cc963-105">Membros</span><span class="sxs-lookup"><span data-stu-id="cc963-105">Members</span></span>  
  
|<span data-ttu-id="cc963-106">Membro</span><span class="sxs-lookup"><span data-stu-id="cc963-106">Member</span></span>|<span data-ttu-id="cc963-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="cc963-107">Description</span></span>|  
|------------|-----------------|  
|`token`|<span data-ttu-id="cc963-108">Um `mdFieldDef` token que pode ser usado para obter informações de campo.</span><span class="sxs-lookup"><span data-stu-id="cc963-108">An `mdFieldDef` token that can be used to get field information.</span></span>|  
|`offset`|<span data-ttu-id="cc963-109">O deslocamento, em bytes, para os dados de campo no objeto.</span><span class="sxs-lookup"><span data-stu-id="cc963-109">The offset, in bytes, to the field data in the object.</span></span>|  
|`id`|<span data-ttu-id="cc963-110">Um valor [COR_TYPEID](cor-typeid-structure.md) que identifica o tipo desse campo.</span><span class="sxs-lookup"><span data-stu-id="cc963-110">A [COR_TYPEID](cor-typeid-structure.md) value that identifies the type of this field.</span></span>|  
|`fieldType`|<span data-ttu-id="cc963-111">Um valor de enumeração CorElementType que indica o tipo do campo.</span><span class="sxs-lookup"><span data-stu-id="cc963-111">A CorElementType enumeration value that indicates the type of the field.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cc963-112">Comentários</span><span class="sxs-lookup"><span data-stu-id="cc963-112">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cc963-113">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cc963-113">Requirements</span></span>  
 <span data-ttu-id="cc963-114">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cc963-114">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cc963-115">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="cc963-115">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="cc963-116">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="cc963-116">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="cc963-117">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="cc963-117">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cc963-118">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cc963-118">See also</span></span>

- [<span data-ttu-id="cc963-119">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="cc963-119">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="cc963-120">Depuração</span><span class="sxs-lookup"><span data-stu-id="cc963-120">Debugging</span></span>](index.md)
