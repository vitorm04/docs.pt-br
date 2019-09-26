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
ms.openlocfilehash: c59ddec655f3127e8dab8d8c41543f03a896cf63
ms.sourcegitcommit: 3caa92cb97e9f6c31f21769c7a3f7c4304024b39
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2019
ms.locfileid: "71274031"
---
# <a name="cor_heapobject-structure"></a><span data-ttu-id="fa122-102">Estrutura COR_HEAPOBJECT</span><span class="sxs-lookup"><span data-stu-id="fa122-102">COR_HEAPOBJECT Structure</span></span>
<span data-ttu-id="fa122-103">Fornece informações sobre um objeto no heap gerenciado.</span><span class="sxs-lookup"><span data-stu-id="fa122-103">Provides information about an object on the managed heap.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa122-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fa122-104">Syntax</span></span>  
  
```cpp  
typedef struct _COR_HEAPOBJECT {  
    CORDB_ADDRESS address;    
    ULONG64 size;             
    COR_TYPEID type;          
} COR_HEAPOBJECT;  
```  
  
## <a name="members"></a><span data-ttu-id="fa122-105">Membros</span><span class="sxs-lookup"><span data-stu-id="fa122-105">Members</span></span>  
  
|<span data-ttu-id="fa122-106">Membro</span><span class="sxs-lookup"><span data-stu-id="fa122-106">Member</span></span>|<span data-ttu-id="fa122-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="fa122-107">Description</span></span>|  
|------------|-----------------|  
|`address`|<span data-ttu-id="fa122-108">O endereço do objeto na memória.</span><span class="sxs-lookup"><span data-stu-id="fa122-108">The address of the object in memory.</span></span>|  
|`size`|<span data-ttu-id="fa122-109">O tamanho total do objeto, em bytes.</span><span class="sxs-lookup"><span data-stu-id="fa122-109">The total size of the object, in bytes.</span></span>|  
|`type`|<span data-ttu-id="fa122-110">Um token [COR_TYPEID](cor-typeid-structure.md) que representa o tipo do objeto.</span><span class="sxs-lookup"><span data-stu-id="fa122-110">A [COR_TYPEID](cor-typeid-structure.md) token that represents the type of the object.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa122-111">Comentários</span><span class="sxs-lookup"><span data-stu-id="fa122-111">Remarks</span></span>  
 <span data-ttu-id="fa122-112">`COR_HEAPOBJECT`as instâncias podem ser recuperadas enumerando um objeto de interface [ICorDebugHeapEnum](icordebugheapenum-interface.md) que é populado chamando o método [ICorDebugProcess5:: EnumerateHeap](icordebugprocess5-enumerateheap-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fa122-112">`COR_HEAPOBJECT` instances can be retrieved by enumerating an [ICorDebugHeapEnum](icordebugheapenum-interface.md) interface object that is populated by calling the [ICorDebugProcess5::EnumerateHeap](icordebugprocess5-enumerateheap-method.md) method.</span></span>  
  
 <span data-ttu-id="fa122-113">Uma `COR_HEAPOBJECT` instância do fornece informações sobre um objeto ao vivo no heap gerenciado ou sobre um objeto que não tem raiz por nenhum objeto, mas que ainda não foi coletado pelo coletor de lixo.</span><span class="sxs-lookup"><span data-stu-id="fa122-113">A `COR_HEAPOBJECT` instance provides information either about a live object on the managed heap, or about an object that is not rooted by any object but has not yet been collected by the garbage collector.</span></span>  
  
 <span data-ttu-id="fa122-114">Para obter um melhor desempenho `COR_HEAPOBJECT.address` , o campo `CORDB_ADDRESS` é um valor em vez do valor da interface ICorDebugValue usado em grande parte da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="fa122-114">For better performance, the `COR_HEAPOBJECT.address` field is a `CORDB_ADDRESS` value rather than the ICorDebugValue interface value used in much of the debugging API.</span></span> <span data-ttu-id="fa122-115">Para obter um objeto ICorDebugValue para um determinado endereço de objeto, você pode passar `CORDB_ADDRESS` o valor para o método [ICorDebugProcess5:: GetObject](icordebugprocess5-getobject-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fa122-115">To obtain an ICorDebugValue object for a given object address, you can pass the `CORDB_ADDRESS` value to the [ICorDebugProcess5::GetObject](icordebugprocess5-getobject-method.md) method.</span></span>  
  
 <span data-ttu-id="fa122-116">Para obter um melhor desempenho `COR_HEAPOBJECT.type` , o campo `COR_TYPEID` é um valor em vez do valor da interface ICorDebugType usado em grande parte da API de depuração.</span><span class="sxs-lookup"><span data-stu-id="fa122-116">For better performance, the `COR_HEAPOBJECT.type` field is a `COR_TYPEID` value rather than the ICorDebugType interface value used in much of the debugging API.</span></span> <span data-ttu-id="fa122-117">Para obter um objeto ICorDebugType para uma determinada ID de tipo, você pode passar `COR_TYPEID` o valor para o método [ICorDebugProcess5:: GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) .</span><span class="sxs-lookup"><span data-stu-id="fa122-117">To obtain an ICorDebugType object for a given type ID, you can pass the `COR_TYPEID` value to the [ICorDebugProcess5::GetTypeForTypeID](icordebugprocess5-gettypefortypeid-method.md) method.</span></span>  
  
 <span data-ttu-id="fa122-118">A `COR_HEAPOBJECT` estrutura inclui uma interface com contada com referência.</span><span class="sxs-lookup"><span data-stu-id="fa122-118">The `COR_HEAPOBJECT` structure includes a reference-counted COM interface.</span></span> <span data-ttu-id="fa122-119">Se você recuperar uma `COR_HEAPOBJECT` instância do enumerador chamando o método [ICorDebugHeapEnum:: Next](icordebugheapenum-next-method.md) , você deverá liberar a referência posteriormente.</span><span class="sxs-lookup"><span data-stu-id="fa122-119">If you retrieve a `COR_HEAPOBJECT` instance from the enumerator by calling the [ICorDebugHeapEnum::Next](icordebugheapenum-next-method.md) method, you must subsequently release the reference.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fa122-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fa122-120">Requirements</span></span>  
 <span data-ttu-id="fa122-121">**Compatíveis** Confira [Requisitos de sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="fa122-121">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="fa122-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="fa122-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="fa122-123">**Biblioteca** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="fa122-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="fa122-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="fa122-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa122-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fa122-125">See also</span></span>

- [<span data-ttu-id="fa122-126">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="fa122-126">Debugging Structures</span></span>](debugging-structures.md)
- [<span data-ttu-id="fa122-127">Depuração</span><span class="sxs-lookup"><span data-stu-id="fa122-127">Debugging</span></span>](index.md)
