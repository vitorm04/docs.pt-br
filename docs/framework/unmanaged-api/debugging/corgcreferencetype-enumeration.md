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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8a673c98b11fbca5f66e9e1ae61f224448c20797
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59207143"
---
# <a name="corgcreferencetype-enumeration"></a><span data-ttu-id="88e53-102">Enumeração CorGCReferenceType</span><span class="sxs-lookup"><span data-stu-id="88e53-102">CorGCReferenceType Enumeration</span></span>
<span data-ttu-id="88e53-103">Identifica a fonte de um objeto para ser coletado do lixo.</span><span class="sxs-lookup"><span data-stu-id="88e53-103">Identifies the source of an object to be garbage-collected.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88e53-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="88e53-104">Syntax</span></span>  
  
```  
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
  
## <a name="members"></a><span data-ttu-id="88e53-105">Membros</span><span class="sxs-lookup"><span data-stu-id="88e53-105">Members</span></span>  
  
|<span data-ttu-id="88e53-106">Nome do membro</span><span class="sxs-lookup"><span data-stu-id="88e53-106">Member name</span></span>|<span data-ttu-id="88e53-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="88e53-107">Description</span></span>|  
|-----------------|-----------------|  
|`CorHandleStrong`|<span data-ttu-id="88e53-108">Uma alça para uma referência forte da tabela de identificador de objeto.</span><span class="sxs-lookup"><span data-stu-id="88e53-108">A handle to a strong reference from the object handle table.</span></span>|  
|`CorHandleStrongPinning`|<span data-ttu-id="88e53-109">Um identificador para uma referência forte fixa da tabela de identificador de objeto.</span><span class="sxs-lookup"><span data-stu-id="88e53-109">A handle to a pinned strong reference from the object handle table.</span></span>|  
|`CorHandleWeakShort`|<span data-ttu-id="88e53-110">Um identificador para uma referência fraca da tabela de identificador de objeto.</span><span class="sxs-lookup"><span data-stu-id="88e53-110">A handle to a weak reference from the object handle table.</span></span>|  
|`CorHandleWeakRefCount`|<span data-ttu-id="88e53-111">Um identificador para um objeto de contagem de referência fraco da tabela de identificador de objeto.</span><span class="sxs-lookup"><span data-stu-id="88e53-111">A handle to a weak reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongRefCount`|<span data-ttu-id="88e53-112">Um identificador para um objeto contado por referência da tabela de identificador de objeto.</span><span class="sxs-lookup"><span data-stu-id="88e53-112">A handle to a reference-counted object from the object handle table.</span></span>|  
|`CorHandleStrongDependent`|<span data-ttu-id="88e53-113">Um identificador para um objeto dependente da tabela de identificador de objeto.</span><span class="sxs-lookup"><span data-stu-id="88e53-113">A handle to a dependent object from the object handle table.</span></span>|  
|`CorHandleStrongAsyncPinned`|<span data-ttu-id="88e53-114">Um objeto fixo assíncrono da tabela de identificador de objeto.</span><span class="sxs-lookup"><span data-stu-id="88e53-114">An asynchronous pinned object from the object handle table.</span></span>|  
|`CorHandleStrongSizedByref`|<span data-ttu-id="88e53-115">Uma alça forte que mantém um tamanho aproximado do fechamento coletivo de todos os objetos e raízes de objeto no momento da coleta de lixo.</span><span class="sxs-lookup"><span data-stu-id="88e53-115">A strong handle that keeps an approximate size of the collective closure of all objects and object roots at garbage collection time.</span></span>|  
|`CorReferenceStack`|<span data-ttu-id="88e53-116">Uma referência da pilha gerenciada.</span><span class="sxs-lookup"><span data-stu-id="88e53-116">A reference from the managed stack.</span></span>|  
|`CorReferenceFinalizer`|<span data-ttu-id="88e53-117">Uma referência da fila do finalizador.</span><span class="sxs-lookup"><span data-stu-id="88e53-117">A reference from the finalizer queue.</span></span>|  
|<span data-ttu-id="88e53-118">CorHandleStrongOnly</span><span class="sxs-lookup"><span data-stu-id="88e53-118">CorHandleStrongOnly</span></span>|<span data-ttu-id="88e53-119">Retorne apenas as referências fortes da tabela de identificador.</span><span class="sxs-lookup"><span data-stu-id="88e53-119">Return only strong references from the handle table.</span></span> <span data-ttu-id="88e53-120">Esse valor é usado o [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) somente no método.</span><span class="sxs-lookup"><span data-stu-id="88e53-120">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleWeakOnly`|<span data-ttu-id="88e53-121">Retorne apenas as referências fracas da tabela de identificador.</span><span class="sxs-lookup"><span data-stu-id="88e53-121">Return only weak references from the handle table.</span></span> <span data-ttu-id="88e53-122">Esse valor é usado o [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) somente no método.</span><span class="sxs-lookup"><span data-stu-id="88e53-122">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
|`CorHandleAll`|<span data-ttu-id="88e53-123">Retorne todas as referências de tabela de identificador.</span><span class="sxs-lookup"><span data-stu-id="88e53-123">Return all references from the handle table.</span></span> <span data-ttu-id="88e53-124">Esse valor é usado o [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) somente no método.</span><span class="sxs-lookup"><span data-stu-id="88e53-124">This value is used by the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method only.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88e53-125">Comentários</span><span class="sxs-lookup"><span data-stu-id="88e53-125">Remarks</span></span>  
 <span data-ttu-id="88e53-126">O `CorGCReferenceType` enumeração é usada da seguinte maneira:</span><span class="sxs-lookup"><span data-stu-id="88e53-126">The `CorGCReferenceType` enumeration is used as follows:</span></span>  
  
-   <span data-ttu-id="88e53-127">Como o valor da `type` campo do [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) estrutura, ele indica que a fonte de uma referência ou um identificador.</span><span class="sxs-lookup"><span data-stu-id="88e53-127">As the value of the `type` field of the [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) structure, it indicates the source of a reference or handle.</span></span>  
  
-   <span data-ttu-id="88e53-128">Como o `types` argumento para o [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) método, ele especifica os tipos de identificadores para incluir na enumeração.</span><span class="sxs-lookup"><span data-stu-id="88e53-128">As the `types` argument to the [ICorDebugProcess5::EnumerateHandles](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumeratehandles-method.md) method, it specifies the types of handles to include in the enumeration.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="88e53-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="88e53-129">Requirements</span></span>  
 <span data-ttu-id="88e53-130">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="88e53-130">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="88e53-131">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="88e53-131">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="88e53-132">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="88e53-132">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="88e53-133">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="88e53-133">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="88e53-134">Consulte também</span><span class="sxs-lookup"><span data-stu-id="88e53-134">See also</span></span>

- [<span data-ttu-id="88e53-135">Declarando enumerações</span><span class="sxs-lookup"><span data-stu-id="88e53-135">Debugging Enumerations</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
