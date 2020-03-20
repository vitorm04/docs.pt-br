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
ms.openlocfilehash: efb3d913e1d8ef0c486d7e5e1d9777ae7d88bc71
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179329"
---
# <a name="cor_heapobject-structure"></a><span data-ttu-id="291a1-102">Estrutura COR_HEAPOBJECT</span><span class="sxs-lookup"><span data-stu-id="291a1-102">COR_HEAPOBJECT Structure</span></span>
<span data-ttu-id="291a1-103">Fornece informações sobre um objeto no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="291a1-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="291a1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="291a1-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;
    ULONG64 size;
    COR_TYPEID type;
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="291a1-105">Membros</span><span class="sxs-lookup"><span data-stu-id="291a1-105">Members</span></span>  
  
|<span data-ttu-id="291a1-106">Membro</span><span class="sxs-lookup"><span data-stu-id="291a1-106">Member</span></span>|<span data-ttu-id="291a1-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="291a1-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="291a1-108">O endereço do objeto na memória.</span><span class="sxs-lookup"><span data-stu-id="291a1-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="291a1-109">O tamanho total do objeto, em bytes.</span><span class="sxs-lookup"><span data-stu-id="291a1-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="291a1-110">Um token [COR_TYPEID](cor-typeid-structure.md) que representa o tipo do objeto.</span><span class="sxs-lookup"><span data-stu-id="291a1-110">A [COR_TYPEID](cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="291a1-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="291a1-111">Remarks</span></span>  
 <span data-ttu-id="291a1-112">`COR_HEAPOBJECT`as instâncias podem ser recuperadas enumerando um objeto de interface [ICorDebugHeapEnum](icordebugheapenum-interface.md) que é preenchido chamando o método [ICorDebugProcess5::EnumerateHeap.](icordebugprocess5-enumerateheap-method.md)</span><span class="sxs-lookup"><span data-stu-id="291a1-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="291a1-113">Uma `COR_HEAPOBJECT` instância fornece informações sobre um objeto vivo no heap gerenciado ou sobre um objeto que não está enraizado em nenhum objeto, mas ainda não foi coletado pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="291a1-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="291a1-114">Para um melhor `COR_HEAPOBJECT.address` desempenho, `CORDB_ADDRESS` o campo é um valor em vez do valor de interface ICorDebugValue usado em grande parte da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="291a1-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="291a1-115">Para obter um objeto ICorDebugValue para um determinado `CORDB_ADDRESS` endereço de objeto, você pode passar o valor para o método [ICorDebugProcess5::GetObject.](icordebugprocess5-getobject-method.md)</span><span class="sxs-lookup"><span data-stu-id="291a1-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="291a1-116">Para um melhor `COR_HEAPOBJECT.type` desempenho, `COR_TYPEID` o campo é um valor em vez do valor de interface ICorDebugType usado em grande parte da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="291a1-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="291a1-117">Para obter um objeto ICorDebugType para um determinado `COR_TYPEID` tipo DeI, você pode passar o valor para o método [ICorDebugProcess5::GetTypeForTypeID.](icordebugprocess5-gettypefortypeid-method.md)</span><span class="sxs-lookup"><span data-stu-id="291a1-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="291a1-118">A `COR_HEAPOBJECT` estrutura inclui uma interface COM contada com referência.</span><span class="sxs-lookup"><span data-stu-id="291a1-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="291a1-119">Se você `COR_HEAPOBJECT` recuperar uma instância do enumerador chamando o [método ICorDebugHeapEnum::Next,](icordebugheapenum-next-method.md) você deve posteriormente liberar a referência.</span><span class="sxs-lookup"><span data-stu-id="291a1-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="291a1-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="291a1-120">Requirements</span></span>  
 <span data-ttu-id="291a1-121">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="291a1-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="291a1-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="291a1-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="291a1-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="291a1-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="291a1-124">**.NET Framework Versions:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="291a1-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="291a1-125">Confira também</span><span class="sxs-lookup"><span data-stu-id="291a1-125">See also</span></span>

- [<span data-ttu-id="291a1-126">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="291a1-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="291a1-127">Depuração</span><span class="sxs-lookup"><span data-stu-id="291a1-127">Debugging</span></span>](index.md)
