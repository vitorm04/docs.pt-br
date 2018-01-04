---
title: Interface ICorDebugGCReferenceEnum
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugGCReferenceEnum
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugGCReferenceEnum
helpviewer_keywords: ICorDebugGCReferenceEnum interface [.NET Framework debugging]
ms.assetid: 5f3c91c9-c035-454f-96cc-011cab1ea06b
topic_type: apiref
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 1afe52c3df8f61b234b3c68ee819ba8389593c82
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebuggcreferenceenum-interface"></a><span data-ttu-id="0215b-102">Interface ICorDebugGCReferenceEnum</span><span class="sxs-lookup"><span data-stu-id="0215b-102">ICorDebugGCReferenceEnum Interface</span></span>
<span data-ttu-id="0215b-103">Fornece um enumerador para objetos que serão coletados do lixo.</span><span class="sxs-lookup"><span data-stu-id="0215b-103">Provides an enumerator for objects that will be garbage-collected.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="0215b-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="0215b-104">Methods</span></span>  
  
|<span data-ttu-id="0215b-105">Método</span><span class="sxs-lookup"><span data-stu-id="0215b-105">Method</span></span>|<span data-ttu-id="0215b-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="0215b-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="0215b-107">Método Next</span><span class="sxs-lookup"><span data-stu-id="0215b-107">Next Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md)|<span data-ttu-id="0215b-108">Obtém o número especificado de [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instâncias que contêm informações sobre os objetos que serão coletados como lixo.</span><span class="sxs-lookup"><span data-stu-id="0215b-108">Gets the specified number of [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances that contain information about objects that will be garbage-collected.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0215b-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="0215b-109">Remarks</span></span>  
 <span data-ttu-id="0215b-110">O `ICorDebugGCReferenceEnum` interface implementa a interface de "ICorDebugEnum".</span><span class="sxs-lookup"><span data-stu-id="0215b-110">The `ICorDebugGCReferenceEnum` interface implements the "ICorDebugEnum" interface.</span></span>  
  
 <span data-ttu-id="0215b-111">Um `ICorDebugGCReferenceEnum` instância é populada com [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instâncias chamando o [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="0215b-111">An `ICorDebugGCReferenceEnum` instance is populated with [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) instances by calling the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method.</span></span> <span data-ttu-id="0215b-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objetos podem ser enumerados chamando o [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="0215b-112">[COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects can be enumerated by calling the [ICorDebugGCReference::Next](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-next-method.md) method.</span></span>  
  
 <span data-ttu-id="0215b-113">O [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objetos na coleção preenchida por este método representam três tipos de objetos:</span><span class="sxs-lookup"><span data-stu-id="0215b-113">The [COR_GC_REFERENCE](../../../../docs/framework/unmanaged-api/debugging/cor-gc-reference-structure.md) objects in the collection populated by this method represent three kinds of objects:</span></span>  
  
-   <span data-ttu-id="0215b-114">Objetos de todas as pilhas gerenciadas.</span><span class="sxs-lookup"><span data-stu-id="0215b-114">Objects from all managed stacks.</span></span> <span data-ttu-id="0215b-115">Isso inclui referências ao vivo em código gerenciado, bem como os objetos criados pelo common language runtime.</span><span class="sxs-lookup"><span data-stu-id="0215b-115">This includes live references in managed code as well as objects created by the common language runtime.</span></span>  
  
-   <span data-ttu-id="0215b-116">Objetos da tabela de identificador.</span><span class="sxs-lookup"><span data-stu-id="0215b-116">Objects from the handle table.</span></span> <span data-ttu-id="0215b-117">Isso inclui referências fortes (`HNDTYPE_STRONG` e `HNDTYPE_REFCOUNT`) e variáveis estáticas em um módulo.</span><span class="sxs-lookup"><span data-stu-id="0215b-117">This includes strong references (`HNDTYPE_STRONG` and `HNDTYPE_REFCOUNT`) and static variables in a module.</span></span>  
  
-   <span data-ttu-id="0215b-118">Objetos de fila do finalizador.</span><span class="sxs-lookup"><span data-stu-id="0215b-118">Objects from the finalizer queue.</span></span> <span data-ttu-id="0215b-119">Fila do finalizador raízes objetos até que tenha executado o finalizador.</span><span class="sxs-lookup"><span data-stu-id="0215b-119">The finalizer queue roots objects until the finalizer has run.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0215b-120">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0215b-120">Requirements</span></span>  
 <span data-ttu-id="0215b-121">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="0215b-121">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="0215b-122">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="0215b-122">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="0215b-123">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="0215b-123">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="0215b-124">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="0215b-124">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0215b-125">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0215b-125">See Also</span></span>  
 [<span data-ttu-id="0215b-126">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="0215b-126">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
