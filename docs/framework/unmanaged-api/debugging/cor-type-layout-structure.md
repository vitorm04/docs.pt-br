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
ms.openlocfilehash: 7efb2c3e8033b8bd8fa736a29b2ab9b3bedebeaa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59109636"
---
# <a name="cortypelayout-structure"></a><span data-ttu-id="a018e-102">Estrutura COR_TYPE_LAYOUT</span><span class="sxs-lookup"><span data-stu-id="a018e-102">COR_TYPE_LAYOUT Structure</span></span>
<span data-ttu-id="a018e-103">Fornece informações sobre o layout de um objeto na memória.</span><span class="sxs-lookup"><span data-stu-id="a018e-103">Provides information about the layout of an object in memory.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a018e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a018e-104">Syntax</span></span>  
  
```  
typedef struct COR_TYPE_LAYOUT {  
    COR_TYPEID parentID;  
    ULONG32 objectSize;  
    ULONG32 numFields;  
    ULONG32 boxOffset;  
    CorElementType type;  
} COR_TYPE_LAYOUT;  
```  
  
## <a name="members"></a><span data-ttu-id="a018e-105">Membros</span><span class="sxs-lookup"><span data-stu-id="a018e-105">Members</span></span>  
  
|<span data-ttu-id="a018e-106">Membro</span><span class="sxs-lookup"><span data-stu-id="a018e-106">Member</span></span>|<span data-ttu-id="a018e-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a018e-107">Description</span></span>|  
|------------|-----------------|  
|`parentID`|<span data-ttu-id="a018e-108">O identificador do tipo pai para esse tipo.</span><span class="sxs-lookup"><span data-stu-id="a018e-108">The identifier of the parent type to this type.</span></span> <span data-ttu-id="a018e-109">Esta será a id de tipo nulo (token1 = 0, token2 = 0) se a id de tipo corresponde ao <xref:System.Object?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="a018e-109">This will be the NULL type id (token1= 0, token2 = 0) if the type id corresponds to <xref:System.Object?displayProperty=nameWithType>.</span></span>|  
|`objectSize`|<span data-ttu-id="a018e-110">O tamanho da base de um objeto desse tipo.</span><span class="sxs-lookup"><span data-stu-id="a018e-110">The base size of an object of this type.</span></span> <span data-ttu-id="a018e-111">Esse é o tamanho total de objetos de tamanho não variável.</span><span class="sxs-lookup"><span data-stu-id="a018e-111">This is the total size for non-variable sized objects.</span></span>|  
|`numFields`|<span data-ttu-id="a018e-112">O número de campos incluídos em objetos desse tipo.</span><span class="sxs-lookup"><span data-stu-id="a018e-112">The number of fields included in objects of this type.</span></span>|  
|`boxOffset`|<span data-ttu-id="a018e-113">Se esse tipo é demarcado, o início de deslocamento de campos de um objeto.</span><span class="sxs-lookup"><span data-stu-id="a018e-113">If this type is boxed, the beginning offset of an object's fields.</span></span> <span data-ttu-id="a018e-114">Este campo é válido somente para tipos de valor, como primitivos e estruturas.</span><span class="sxs-lookup"><span data-stu-id="a018e-114">This field is valid only for value types such as primitives and structures.</span></span>|  
|`type`|<span data-ttu-id="a018e-115">O CorElementType ao qual pertence esse tipo.</span><span class="sxs-lookup"><span data-stu-id="a018e-115">The CorElementType to which this type belongs.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="a018e-116">Comentários</span><span class="sxs-lookup"><span data-stu-id="a018e-116">Remarks</span></span>  
 <span data-ttu-id="a018e-117">Se `numFields` é maior que zero, você pode chamar o [ICorDebugProcess5::GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) método para obter informações sobre os campos nesse tipo.</span><span class="sxs-lookup"><span data-stu-id="a018e-117">If `numFields` is greater than zero, you can call the [ICorDebugProcess5::GetTypeFields](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefields-method.md) method to obtain information about the fields in this type.</span></span> <span data-ttu-id="a018e-118">Se `type` está `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, ou `ELEMENT_TYPE_SZARRAY`, o tamanho dos objetos desse tipo é variável, e você pode passar o [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) estrutura para o [ICorDebugProcess5::GetArrayLayout ](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="a018e-118">If `type` is `ELEMENT_TYPE_STRING`, `ELEMENT_TYPE_ARRAY`, or `ELEMENT_TYPE_SZARRAY`, the size of objects of this type is variable, and you can pass the [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) structure to the [ICorDebugProcess5::GetArrayLayout](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getarraylayout-method.md) method.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a018e-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a018e-119">Requirements</span></span>  
 <span data-ttu-id="a018e-120">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="a018e-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="a018e-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="a018e-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="a018e-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="a018e-122">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="a018e-123">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="a018e-123">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a018e-124">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a018e-124">See also</span></span>

- [<span data-ttu-id="a018e-125">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="a018e-125">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="a018e-126">Depuração</span><span class="sxs-lookup"><span data-stu-id="a018e-126">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
