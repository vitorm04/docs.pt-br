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
ms.openlocfilehash: e0e68dba1f4d9ac5fa618aa842b823dcc046e70e
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73129673"
---
# <a name="icordebugprocess5enumeratehandles-method"></a><span data-ttu-id="445a7-102">Método ICorDebugProcess5::EnumerateHandles</span><span class="sxs-lookup"><span data-stu-id="445a7-102">ICorDebugProcess5::EnumerateHandles Method</span></span>
<span data-ttu-id="445a7-103">Obtém um enumerador para identificadores de objeto em um processo.</span><span class="sxs-lookup"><span data-stu-id="445a7-103">Gets an enumerator for object handles in a process.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="445a7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="445a7-104">Syntax</span></span>  
  
```cpp  
HRESULT EnumerateHandles(     [in] CorGCReferenceType types,  
    [out] ICorDebugGCReferenceEnum **ppEnum);  
```  
  
## <a name="parameters"></a><span data-ttu-id="445a7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="445a7-105">Parameters</span></span>  
 `types`  
 <span data-ttu-id="445a7-106">no Uma combinação bits de valores [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) que especifica o tipo de identificadores a serem incluídos na coleção.</span><span class="sxs-lookup"><span data-stu-id="445a7-106">[in] A bitwise combination of [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) values that specifies the type of handles to include in the collection.</span></span>  
  
 `ppENum`  
 <span data-ttu-id="445a7-107">fora Um ponteiro para o endereço de um [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) que é um enumerador para os objetos a serem coletados como lixo.</span><span class="sxs-lookup"><span data-stu-id="445a7-107">[out] A pointer to the address of an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) that is an enumerator for the objects to be garbage-collected.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="445a7-108">Comentários</span><span class="sxs-lookup"><span data-stu-id="445a7-108">Remarks</span></span>  
 <span data-ttu-id="445a7-109">`EnumerateHandles` é uma função auxiliar que dá suporte à inspeção da tabela de identificadores.</span><span class="sxs-lookup"><span data-stu-id="445a7-109">`EnumerateHandles` is a helper function that supports inspection of the handle table.</span></span> <span data-ttu-id="445a7-110">Ele é semelhante ao método [ICorDebugProcess5:: EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) , exceto que, em vez de preencher uma coleção [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) com todos os objetos a serem coletados pelo lixo, ele inclui somente objetos que têm identificadores de a tabela de identificadores.</span><span class="sxs-lookup"><span data-stu-id="445a7-110">It is similar to the [ICorDebugProcess5::EnumerateGCReferences](../../../../docs/framework/unmanaged-api/debugging/icordebugprocess5-enumerategcreferences-method.md) method, except that rather than populating an [ICorDebugGCReferenceEnum](../../../../docs/framework/unmanaged-api/debugging/icordebuggcreferenceenum-interface.md) collection with all objects to be garbage-collected, it includes only objects that have handles from the handle table.</span></span>  
  
 <span data-ttu-id="445a7-111">O parâmetro `types` especifica os tipos de identificador a serem incluídos na coleção.</span><span class="sxs-lookup"><span data-stu-id="445a7-111">The `types` parameter specifies the handle types to include in the collection.</span></span> <span data-ttu-id="445a7-112">`types` pode ser qualquer um dos três seguintes membros da enumeração [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) :</span><span class="sxs-lookup"><span data-stu-id="445a7-112">`types` can be any of the following three members of the [CorGCReferenceType](../../../../docs/framework/unmanaged-api/debugging/corgcreferencetype-enumeration.md) enumeration:</span></span>  
  
- <span data-ttu-id="445a7-113">`CorHandleStrongOnly` (trata apenas de referências fortes).</span><span class="sxs-lookup"><span data-stu-id="445a7-113">`CorHandleStrongOnly` (handles to strong references only).</span></span>  
  
- <span data-ttu-id="445a7-114">`CorHandleWeakOnly` (trata apenas de referências fracas).</span><span class="sxs-lookup"><span data-stu-id="445a7-114">`CorHandleWeakOnly` (handles to weak references only).</span></span>  
  
- <span data-ttu-id="445a7-115">`CorHandleAll` (todos os identificadores).</span><span class="sxs-lookup"><span data-stu-id="445a7-115">`CorHandleAll` (all handles).</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="445a7-116">Requisitos</span><span class="sxs-lookup"><span data-stu-id="445a7-116">Requirements</span></span>  
 <span data-ttu-id="445a7-117">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="445a7-117">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="445a7-118">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="445a7-118">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="445a7-119">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="445a7-119">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="445a7-120">**Versões do .NET Framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="445a7-120">**.NET Framework Versions:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="445a7-121">Consulte também</span><span class="sxs-lookup"><span data-stu-id="445a7-121">See also</span></span>

- [<span data-ttu-id="445a7-122">Estruturas de depuração</span><span class="sxs-lookup"><span data-stu-id="445a7-122">Debugging Structures</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
- [<span data-ttu-id="445a7-123">Depuração</span><span class="sxs-lookup"><span data-stu-id="445a7-123">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
