---
title: Interface ICorDebugGCReferenceEnum
ms.date: 03/30/2017
api_name:
- ICorDebugGCReferenceEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugGCReferenceEnum
helpviewer_keywords:
- ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2d228e548255cd70f34f6609aff613789f94fe5d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54507519"
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="bb084-102">Interface ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="bb084-102">ICorDebugGCReferenceEnum Interface</span></span>
<span data-ttu-id="bb084-103">Fornece um enumerador para objetos que serão coletados do lixo.</span><span class="sxs-lookup"><span data-stu-id="bb084-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="bb084-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="bb084-104">Methods</span></span>  
  
|<span data-ttu-id="bb084-105">Método</span><span class="sxs-lookup"><span data-stu-id="bb084-105">Method</span></span>|<span data-ttu-id="bb084-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="bb084-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="bb084-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="bb084-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="bb084-108">Obtém o número especificado de [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instâncias que contêm informações sobre os objetos que serão coletados pelo lixo.</span><span class="sxs-lookup"><span data-stu-id="bb084-108">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="bb084-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="bb084-109">Remarks</span></span>  
 <span data-ttu-id="bb084-110">O `ICorDebugGCReferenceEnum` interface implementa a interface "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="bb084-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="bb084-111">Uma `ICorDebugGCReferenceEnum` instância é preenchida com [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instâncias chamando o [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="bb084-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="bb084-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objetos que podem ser enumerados chamando o [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="bb084-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="bb084-113">O [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objetos na coleção populado por esse método representam três tipos de objetos:</span><span class="sxs-lookup"><span data-stu-id="bb084-113">The [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
-   <span data-ttu-id="bb084-114">Objetos de todas as pilhas gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="bb084-114">Objects from all managed stacks.</span></span> <span data-ttu-id="bb084-115">Isso inclui referências ao vivo em código gerenciado, bem como os objetos criados pelo common language runtime.</span><span class="sxs-lookup"><span data-stu-id="bb084-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
-   <span data-ttu-id="bb084-116">Objetos da tabela de identificador.</span><span class="sxs-lookup"><span data-stu-id="bb084-116">Objects from the handle table.</span></span> <span data-ttu-id="bb084-117">Isso inclui referências fortes (`HNDTYPE_STRONG` e `HNDTYPE_REFCOUNT`) e as variáveis estáticas em um módulo.</span><span class="sxs-lookup"><span data-stu-id="bb084-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
-   <span data-ttu-id="bb084-118">Objetos de fila do finalizador.</span><span class="sxs-lookup"><span data-stu-id="bb084-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="bb084-119">A fila de finalizadores raízes objetos até que o finalizador foi executado.</span><span class="sxs-lookup"><span data-stu-id="bb084-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bb084-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bb084-120">Requirements</span></span>  
 <span data-ttu-id="bb084-121">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="bb084-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="bb084-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="bb084-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="bb084-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="bb084-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="bb084-124">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="bb084-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb084-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bb084-125">See also</span></span>
- [<span data-ttu-id="bb084-126">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="bb084-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
