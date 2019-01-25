---
title: Estrutura COR_HEAPOBJECT
ms.date: 03/30/2017
api_name:
- COR_HEAPOBJECT
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- COR_HEAPOBJECT
helpviewer_keywords:
- COR_HEAPOBJECT structure [.NET Framework debugging]
ms.assetid: a92fdf95-492b-49ae-a741-2186e5c1d7c5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 34b02dfa3fb0f1e5f4cfadc297194dc4f3160c8a
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628468"
---
# <a name="corheapobject-structure"></a><span data-ttu-id="e9a1c-102">Estrutura COR_HEAPOBJECT</span><span class="sxs-lookup"><span data-stu-id="e9a1c-102">COR_HEAPOBJECT Structure</span></span>
<span data-ttu-id="e9a1c-103">Fornece informações sobre um objeto no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="e9a1c-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e9a1c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e9a1c-104">Syntax</span></span>  
  
```  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="e9a1c-105">Membros</span><span class="sxs-lookup"><span data-stu-id="e9a1c-105">Members</span></span>  
  
|<span data-ttu-id="e9a1c-106">Membro</span><span class="sxs-lookup"><span data-stu-id="e9a1c-106">Member</span></span>|<span data-ttu-id="e9a1c-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="e9a1c-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="e9a1c-108">O endereço do objeto na memória.</span><span class="sxs-lookup"><span data-stu-id="e9a1c-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="e9a1c-109">O tamanho total do objeto, em bytes.</span><span class="sxs-lookup"><span data-stu-id="e9a1c-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="e9a1c-110">Um [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token que representa o tipo do objeto.</span><span class="sxs-lookup"><span data-stu-id="e9a1c-110">A [COR_TYPEID](../../../../docs/framework/unmanaged-api/debugging/cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e9a1c-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="e9a1c-111">Remarks</span></span>  
 <span data-ttu-id="e9a1c-112">`COR_HEAPOBJECT` instâncias podem ser recuperadas, enumerando uma [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) objeto de interface que é preenchido com a chamada a [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="e9a1c-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="e9a1c-113">Um `COR_HEAPOBJECT` instância fornece informações sobre um objeto vivo no heap gerenciado, ou sobre um objeto que não está na raiz por qualquer objeto, mas ainda não foi coletado pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="e9a1c-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="e9a1c-114">Para obter melhor desempenho, o `COR_HEAPOBJECT.address` campo é um `CORDB_ADDRESS` valor em vez do ICorDebugValue valor usado em grande parte da API de depuração da interface.</span><span class="sxs-lookup"><span data-stu-id="e9a1c-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="e9a1c-115">Para obter um objeto ICorDebugValue para um endereço de determinado objeto, você pode passar o `CORDB_ADDRESS` de valor para o [ICorDebugProcess5::GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="e9a1c-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="e9a1c-116">Para obter melhor desempenho, o `COR_HEAPOBJECT.type` campo é um `COR_TYPEID` valor em vez de ICorDebugType valor usado em grande parte da API de depuração da interface.</span><span class="sxs-lookup"><span data-stu-id="e9a1c-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="e9a1c-117">Para obter um objeto ICorDebugType para uma ID de tipo em questão, você pode passar o `COR_TYPEID` de valor para o [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="e9a1c-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="e9a1c-118">O `COR_HEAPOBJECT` estrutura inclui uma interface de COM contado por referência.</span><span class="sxs-lookup"><span data-stu-id="e9a1c-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="e9a1c-119">Se você recuperar um `COR_HEAPOBJECT` instância do enumerador chamando o [icordebugheapenum:: Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) método, posteriormente, você deve liberar a referência.</span><span class="sxs-lookup"><span data-stu-id="e9a1c-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e9a1c-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e9a1c-120">Requirements</span></span>  
 <span data-ttu-id="e9a1c-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="e9a1c-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="e9a1c-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="e9a1c-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="e9a1c-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="e9a1c-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="e9a1c-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="e9a1c-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e9a1c-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e9a1c-125">See also</span></span>
- [<span data-ttu-id="e9a1c-126">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="e9a1c-126">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="e9a1c-127">Depuração</span><span class="sxs-lookup"><span data-stu-id="e9a1c-127">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
