---
title: "Método ICorDebugProcess5::EnumerateHandles"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugProcess5.EnumerateHandles
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type: apiref
caps.latest.revision: "6"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 5377f4ce0571cdb1de6c338f4bbb87d6a589aaf7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="c9ab4-102">Método ICorDebugProcess5::EnumerateHandles</span><span class="sxs-lookup"><span data-stu-id="c9ab4-102">ICorDebugProcess5::EnumerateHandles Method</span></span>
<span data-ttu-id="c9ab4-103">Obtém um enumerador para identificadores de objeto em um processo.</span><span class="sxs-lookup"><span data-stu-id="c9ab4-103">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9ab4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c9ab4-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c9ab4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c9ab4-105">Parameters</span></span>  
 `types`  
 <span data-ttu-id="c9ab4-106">[in] Uma combinação bit a bit de [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) valores que especifica o tipo de identificadores para incluir na coleção.</span><span class="sxs-lookup"><span data-stu-id="c9ab4-106">[in] A bitwise combination of [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="c9ab4-107">[out] Um ponteiro para o endereço de um [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) que é um enumerador para os objetos a ser coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="c9ab4-107">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="c9ab4-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="c9ab4-108">Remarks</span></span>  
 <span data-ttu-id="c9ab4-109">`EnumerateHandles`é uma função auxiliar que dá suporte à inspeção da tabela de identificador.</span><span class="sxs-lookup"><span data-stu-id="c9ab4-109">`EnumerateHandles` is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="c9ab4-110">É semelhante de [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) método, exceto que, em vez de preencher um [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) coleção com todos os objetos a serem coletados como lixo, ele inclui apenas os objetos que têm identificadores da tabela de identificador.</span><span class="sxs-lookup"><span data-stu-id="c9ab4-110">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="c9ab4-111">O `types` parâmetro especifica os tipos de identificador para incluir na coleção.</span><span class="sxs-lookup"><span data-stu-id="c9ab4-111">The `types` parameter specifies the handle types to include in the collection.</span></span> <span data-ttu-id="c9ab4-112">`types`pode ser qualquer um dos seguintes três membros do [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeração:</span><span class="sxs-lookup"><span data-stu-id="c9ab4-112">`types` can be any of the following three members of the [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
-   <span data-ttu-id="c9ab4-113">`CorHandleStrongOnly`(as alças para referências fortes somente).</span><span class="sxs-lookup"><span data-stu-id="c9ab4-113">`CorHandleStrongOnly` (handles to strong references only).</span></span>  
  
-   <span data-ttu-id="c9ab4-114">`CorHandleWeakOnly`(as alças para referências fracas somente).</span><span class="sxs-lookup"><span data-stu-id="c9ab4-114">`CorHandleWeakOnly` (handles to weak references only).</span></span>  
  
-   <span data-ttu-id="c9ab4-115">`CorHandleAll`(todos os identificadores).</span><span class="sxs-lookup"><span data-stu-id="c9ab4-115">`CorHandleAll` (all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c9ab4-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c9ab4-116">Requirements</span></span>  
 <span data-ttu-id="c9ab4-117">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="c9ab4-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="c9ab4-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="c9ab4-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="c9ab4-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="c9ab4-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="c9ab4-120">**Versões do .NET framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="c9ab4-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9ab4-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c9ab4-121">See Also</span></span>  
 [<span data-ttu-id="c9ab4-122">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="c9ab4-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)  
 [<span data-ttu-id="c9ab4-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="c9ab4-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
