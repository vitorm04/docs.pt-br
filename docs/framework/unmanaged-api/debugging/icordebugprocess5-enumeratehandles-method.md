---
title: Método ICorDebugProcess5::EnumerateHandles
ms.date: 03/30/2017
api_name:
- ICorDebugProcess5.EnumerateHandles
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess5::EnumerateHandles
helpviewer_keywords:
- EnumerateHandles method, ICorDebugProcess5 interface [.NET Framework debugging]
- ICorDebugProcess5::EnumerateHandles method [.NET Framework debugging]
ms.assetid: 7d7fa796-0dc6-4ee8-9d56-40166246d91d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2b3cc158c48e8bb9f833429bbddaa74ed459f1b6
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59108817"
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="13c5c-102">Método ICorDebugProcess5::EnumerateHandles</span><span class="sxs-lookup"><span data-stu-id="13c5c-102">ICorDebugProcess5::EnumerateHandles Method</span></span>
<span data-ttu-id="13c5c-103">Obtém um enumerador para os identificadores de objeto em um processo.</span><span class="sxs-lookup"><span data-stu-id="13c5c-103">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13c5c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13c5c-104">Syntax</span></span>  
  
```  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13c5c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="13c5c-105">Parameters</span></span>  
 `types`  
 <span data-ttu-id="13c5c-106">[in] Uma combinação bit a bit de [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) valores que especifica o tipo de identificadores para incluir na coleção.</span><span class="sxs-lookup"><span data-stu-id="13c5c-106">[in] A bitwise combination of [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="13c5c-107">[out] Um ponteiro para o endereço de um [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) que é um enumerador para os objetos a ser coletado como lixo.</span><span class="sxs-lookup"><span data-stu-id="13c5c-107">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="13c5c-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="13c5c-108">Remarks</span></span>  
 `EnumerateHandles` <span data-ttu-id="13c5c-109">é uma função auxiliar que dá suporte a inspeção da tabela de identificador.</span><span class="sxs-lookup"><span data-stu-id="13c5c-109">is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="13c5c-110">É semelhante ao [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) método, exceto que, em vez de preencher uma [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) coleção com todos os objetos a ser coletado como lixo, ele inclui apenas os objetos que têm identificadores da tabela de identificador.</span><span class="sxs-lookup"><span data-stu-id="13c5c-110">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="13c5c-111">O `types` parâmetro especifica os tipos de identificador para incluir na coleção.</span><span class="sxs-lookup"><span data-stu-id="13c5c-111">The `types` parameter specifies the handle types to include in the collection.</span></span> `types` <span data-ttu-id="13c5c-112">pode ser qualquer um dos seguintes três membros do [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeração:</span><span class="sxs-lookup"><span data-stu-id="13c5c-112">can be any of the following three members of the [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
-   `CorHandleStrongOnly` <span data-ttu-id="13c5c-113">(as alças para apenas referências fortes).</span><span class="sxs-lookup"><span data-stu-id="13c5c-113">(handles to strong references only).</span></span>  
  
-   `CorHandleWeakOnly` <span data-ttu-id="13c5c-114">(as alças para referências fracas apenas).</span><span class="sxs-lookup"><span data-stu-id="13c5c-114">(handles to weak references only).</span></span>  
  
-   `CorHandleAll` <span data-ttu-id="13c5c-115">(todos os identificadores).</span><span class="sxs-lookup"><span data-stu-id="13c5c-115">(all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13c5c-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="13c5c-116">Requirements</span></span>  
 <span data-ttu-id="13c5c-117">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="13c5c-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="13c5c-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="13c5c-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="13c5c-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="13c5c-119">**Library:** CorGuids.lib</span></span>  
  
 **<span data-ttu-id="13c5c-120">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="13c5c-120">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="13c5c-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="13c5c-121">See also</span></span>

- [<span data-ttu-id="13c5c-122">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="13c5c-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="13c5c-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="13c5c-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
