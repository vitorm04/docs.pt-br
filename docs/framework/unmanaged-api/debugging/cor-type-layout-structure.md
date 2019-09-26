---
title: Estrutura COR_TYPE_LAYOUT
ms.date: 03/30/2017
api_name:
- COR_TYPE_LAYOUT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_TYPE_LAYOUT
helpviewer_keywords:
- COR_TYPE_LAYOUT structure [.NET Framework debugging]
ms.assetid: 43a7addd-f25a-4049-9907-abec3eb17af2
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 6bd274b1eb14532629580e777288317186544912
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274159"
---
# <a name="cor_type_layout-structure"></a><span data-ttu-id="b58cf-102">Estrutura COR_TYPE_LAYOUT</span><span class="sxs-lookup"><span data-stu-id="b58cf-102">COR_TYPE_LAYOUT Structure</span></span>
<span data-ttu-id="b58cf-103">Fornece informações sobre o layout de um objeto na memória.</span><span class="sxs-lookup"><span data-stu-id="b58cf-103">Provides information about the layout of an object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b58cf-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b58cf-104">Syntax</span></span>  
  
```cpp  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="b58cf-105">Membros</span><span class="sxs-lookup"><span data-stu-id="b58cf-105">Members</span></span>  
  
|<span data-ttu-id="b58cf-106">Membro</span><span class="sxs-lookup"><span data-stu-id="b58cf-106">Member</span></span>|<span data-ttu-id="b58cf-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="b58cf-107">Description</span></span>|  
|------------|-----------------|  
|`parentID`|<span data-ttu-id="b58cf-108">O identificador do tipo pai para esse tipo.</span><span class="sxs-lookup"><span data-stu-id="b58cf-108">The identifier of the parent type to this type.</span></span> <span data-ttu-id="b58cf-109">Essa será a ID de tipo nulo (token1 = 0, token2 = 0) se a ID de tipo corresponder <xref:System.Object?displayProperty=nameWithType>a.</span><span class="sxs-lookup"><span data-stu-id="b58cf-109">This will be the NULL type id (token1= 0, token2 = 0) if the type id corresponds to <xref:System.Object?displayProperty=nameWithType>.</span></span>|  
|`objectSize`|<span data-ttu-id="b58cf-110">O tamanho de base de um objeto deste tipo.</span><span class="sxs-lookup"><span data-stu-id="b58cf-110">The base size of an object of this type.</span></span> <span data-ttu-id="b58cf-111">Este é o tamanho total para objetos que não são de tamanho variável.</span><span class="sxs-lookup"><span data-stu-id="b58cf-111">This is the total size for non-variable sized objects.</span></span>|  
|`numFields`|<span data-ttu-id="b58cf-112">O número de campos incluídos em objetos deste tipo.</span><span class="sxs-lookup"><span data-stu-id="b58cf-112">The number of fields included in objects of this type.</span></span>|  
|`boxOffset`|<span data-ttu-id="b58cf-113">Se esse tipo for in box, o deslocamento inicial dos campos de um objeto.</span><span class="sxs-lookup"><span data-stu-id="b58cf-113">If this type is boxed, the beginning offset of an object's fields.</span></span> <span data-ttu-id="b58cf-114">Esse campo é válido somente para tipos de valor como primitivos e estruturas.</span><span class="sxs-lookup"><span data-stu-id="b58cf-114">This field is valid only for value types such as primitives and structures.</span></span>|  
|`type`|<span data-ttu-id="b58cf-115">O CorElementType ao qual esse tipo pertence.</span><span class="sxs-lookup"><span data-stu-id="b58cf-115">The CorElementType to which this type belongs.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b58cf-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="b58cf-116">Remarks</span></span>  
 <span data-ttu-id="b58cf-117">Se `numFields` for maior que zero, você poderá chamar o método [ICorDebugProcess5:: GetTypeFields](icordebugprocess5-gettypefields-method.md) para obter informações sobre os campos nesse tipo.</span><span class="sxs-lookup"><span data-stu-id="b58cf-117">If `numFields` is greater than zero, you can call the [ICorDebugProcess5::GetTypeFields](icordebugprocess5-gettypefields-method.md) method to obtain information about the fields in this type.</span></span> <span data-ttu-id="b58cf-118">Se `type` for `ELEMENT_TYPE_STRING` ,`ELEMENT_TYPE_ARRAY`, ou`ELEMENT_TYPE_SZARRAY`, o tamanho dos objetos desse tipo é variável e você pode passar a estrutura [COR_TYPEID](cor-typeid-structure.md) para o método [ICorDebugProcess5:: GetArrayLayout](icordebugprocess5-getarraylayout-method.md) .</span><span class="sxs-lookup"><span data-stu-id="b58cf-118">If `type` is `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, or `ELEMENT_TYPE_SZARRAY`, the size of objects of this type is variable, and you can pass the [COR_TYPEID](cor-typeid-structure.md) structure to the [ICorDebugProcess5::GetArrayLayout](icordebugprocess5-getarraylayout-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b58cf-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b58cf-119">Requirements</span></span>  
 <span data-ttu-id="b58cf-120">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b58cf-120">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b58cf-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="b58cf-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="b58cf-122">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="b58cf-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="b58cf-123">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="b58cf-123">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b58cf-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b58cf-124">See also</span></span>

- [<span data-ttu-id="b58cf-125">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="b58cf-125">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="b58cf-126">Depuração</span><span class="sxs-lookup"><span data-stu-id="b58cf-126">Debugging</span></span>](index.md)
