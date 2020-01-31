---
title: Enumeração CorGCReferenceType
ms.date: 03/30/2017
api_name:
- CorGCReferenceType
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorGCReferenceType
helpviewer_keywords:
- CorGCReferenceType
ms.assetid: d9f16439-5a36-4474-8ffd-4f0b2c2bb686
topic_type:
- apiref
ms.openlocfilehash: 17d47b6242bb12ff5ca3cfbde3e4ec183b9c19fc
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/28/2020
ms.locfileid: "76793870"
---
# <a name="corgcreferencetype-enumeration"></a><span data-ttu-id="6f249-102">Enumeração CorGCReferenceType</span><span class="sxs-lookup"><span data-stu-id="6f249-102">CorGCReferenceType Enumeration</span></span>
<span data-ttu-id="6f249-103">Identifica a fonte de um objeto para ser coletado do lixo.</span><span class="sxs-lookup"><span data-stu-id="6f249-103">Identifies the source of an object to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f249-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6f249-104">Syntax</span></span>  
  
```cpp  
typedef enum {  
    CorHandleStrong = 1,  
    CorHandleStrongPinning = 2,  
    CorHandleWeakShort = 4,  
    CorHandleWeakRefCount = 8,  
    CorHandleStrongRefCount = 32,  
    CorHandleStrongDependent = 64,  
    CorHandleStrongAsyncPinned = 128,  
    CorHandleStrongSizedByref = 256,  
  
    CorReferenceStack = 0x80000001,  
    CorReferenceFinalizer = 0x80000002,  
  
    CorHandleStrongOnly = 0x1E3,  
    CorHandleWeakOnly = 0xC,  
    CorHandleAll = 0x7FFFFFFF  
} CorGCReferenceType  
```  
  
## <a name="members"></a><span data-ttu-id="6f249-105">Membros</span><span class="sxs-lookup"><span data-stu-id="6f249-105">Members</span></span>  
  
|<span data-ttu-id="6f249-106">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="6f249-106">Member name</span></span>|<span data-ttu-id="6f249-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f249-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorHandleStrong`|<span data-ttu-id="6f249-108">Uma alça para uma referência forte da tabela de identificador de objeto.</span><span class="sxs-lookup"><span data-stu-id="6f249-108">A handle to a strong reference from the object handle table.</span></span>|  
|`CorHandleStrongPinning`|<span data-ttu-id="6f249-109">Um identificador para uma referência forte fixada da tabela de identificadores de objeto.</span><span class="sxs-lookup"><span data-stu-id="6f249-109">A handle to a pinned strong reference from the object handle table.</span></span>|  
|`CorHandleWeakShort`|<span data-ttu-id="6f249-110">Um identificador para uma referência fraca da tabela de identificadores de objeto.</span><span class="sxs-lookup"><span data-stu-id="6f249-110">A handle to a weak reference from the object handle table.</span></span>|  
|`CorHandleWeakRefCount`|<span data-ttu-id="6f249-111">Um identificador para um objeto de referência fraca contada da tabela de identificadores de objeto.</span><span class="sxs-lookup"><span data-stu-id="6f249-111">A handle to a weak reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongRefCount`|<span data-ttu-id="6f249-112">Um identificador para um objeto de referência contado da tabela de identificadores de objeto.</span><span class="sxs-lookup"><span data-stu-id="6f249-112">A handle to a reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongDependent`|<span data-ttu-id="6f249-113">Um identificador para um objeto dependente da tabela de identificadores de objeto.</span><span class="sxs-lookup"><span data-stu-id="6f249-113">A handle to a dependent object from the object handle table.</span></span>|  
|`CorHandleStrongAsyncPinned`|<span data-ttu-id="6f249-114">Um objeto fixo assíncrono da tabela de identificador de objeto.</span><span class="sxs-lookup"><span data-stu-id="6f249-114">An asynchronous pinned object from the object handle table.</span></span>|  
|`CorHandleStrongSizedByref`|<span data-ttu-id="6f249-115">Uma alça forte que mantém um tamanho aproximado do fechamento coletivo de todos os objetos e raízes de objeto no momento da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="6f249-115">A strong handle that keeps an approximate size of the collective closure of all objects and object roots at garbage collection time.</span></span>|  
|`CorReferenceStack`|<span data-ttu-id="6f249-116">Uma referência da pilha gerenciada.</span><span class="sxs-lookup"><span data-stu-id="6f249-116">A reference from the managed stack.</span></span>|  
|`CorReferenceFinalizer`|<span data-ttu-id="6f249-117">Uma referência da fila do finalizador.</span><span class="sxs-lookup"><span data-stu-id="6f249-117">A reference from the finalizer queue.</span></span>|  
|<span data-ttu-id="6f249-118">CorHandleStrongOnly</span><span class="sxs-lookup"><span data-stu-id="6f249-118">CorHandleStrongOnly</span></span>|<span data-ttu-id="6f249-119">Retornar apenas referências fortes da tabela de identificadores.</span><span class="sxs-lookup"><span data-stu-id="6f249-119">Return only strong references from the handle table.</span></span> <span data-ttu-id="6f249-120">Esse valor é usado apenas pelo método [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6f249-120">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleWeakOnly`|<span data-ttu-id="6f249-121">Retornar apenas referências fracas da tabela de identificadores.</span><span class="sxs-lookup"><span data-stu-id="6f249-121">Return only weak references from the handle table.</span></span> <span data-ttu-id="6f249-122">Esse valor é usado apenas pelo método [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6f249-122">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleAll`|<span data-ttu-id="6f249-123">Retorna todas as referências da tabela de identificador.</span><span class="sxs-lookup"><span data-stu-id="6f249-123">Return all references from the handle table.</span></span> <span data-ttu-id="6f249-124">Esse valor é usado apenas pelo método [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) .</span><span class="sxs-lookup"><span data-stu-id="6f249-124">This value is used by the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="6f249-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="6f249-125">Remarks</span></span>  
 <span data-ttu-id="6f249-126">A enumeração `CorGCReferenceType` é usada da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="6f249-126">The `CorGCReferenceType` enumeration is used as follows:</span></span>  
  
- <span data-ttu-id="6f249-127">Como o valor do campo `type` da estrutura de [COR_GC_REFERENCE](cor-gc-reference-structure.md) , ele indica a origem de uma referência ou um identificador.</span><span class="sxs-lookup"><span data-stu-id="6f249-127">As the value of the `type` field of the [COR_GC_REFERENCE](cor-gc-reference-structure.md) structure, it indicates the source of a reference or handle.</span></span>  
  
- <span data-ttu-id="6f249-128">Como o argumento `types` para o método [ICorDebugProcess5:: EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) , ele especifica os tipos de identificadores a serem incluídos na enumeração.</span><span class="sxs-lookup"><span data-stu-id="6f249-128">As the `types` argument to the [ICorDebugProcess5::EnumerateHandles](icordebugprocess5-enumeratehandles-method.md) method, it specifies the types of handles to include in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f249-129">Requisitos do</span><span class="sxs-lookup"><span data-stu-id="6f249-129">Requirements</span></span>  
 <span data-ttu-id="6f249-130">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="6f249-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="6f249-131">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="6f249-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="6f249-132">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="6f249-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="6f249-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="6f249-133">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f249-134">Veja também</span><span class="sxs-lookup"><span data-stu-id="6f249-134">See also</span></span>

- [<span data-ttu-id="6f249-135">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="6f249-135">Debugging Enumerations</span></span>](debugging-enumerations.md)
