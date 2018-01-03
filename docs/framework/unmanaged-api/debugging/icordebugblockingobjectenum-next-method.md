---
title: "Método ICorDebugBlockingObjectEnum::Next"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugBlockingObjectEnum.Next Method
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugBlockingObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
- ICorDebugBlockingObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 0121753f-ebea-48d0-aeb2-ed7fda76dc60
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 3f2e2168ea1b03e5a2339baf019da59f1e83a71a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugblockingobjectenumnext-method"></a><span data-ttu-id="195f4-102">Método ICorDebugBlockingObjectEnum::Next</span><span class="sxs-lookup"><span data-stu-id="195f4-102">ICorDebugBlockingObjectEnum::Next Method</span></span>
<span data-ttu-id="195f4-103">Obtém o número especificado de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objetos de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="195f4-103">Gets the specified number of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="195f4-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="195f4-104">Syntax</span></span>  
  
```  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="195f4-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="195f4-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="195f4-106">[in] O número de objetos para recuperar.</span><span class="sxs-lookup"><span data-stu-id="195f4-106">[in] The number of objects to retrieve.</span></span>  
  
 `values`  
 <span data-ttu-id="195f4-107">[out] Uma matriz de ponteiros para [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objetos.</span><span class="sxs-lookup"><span data-stu-id="195f4-107">[out] An array of pointers to [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="195f4-108">[out] Um ponteiro para o número de objetos que foram recuperados.</span><span class="sxs-lookup"><span data-stu-id="195f4-108">[out] A pointer to the number of objects that were retrieved.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="195f4-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="195f4-109">Return Value</span></span>  
 <span data-ttu-id="195f4-110">Esse método retorna os HRESULTs específicos a seguir.</span><span class="sxs-lookup"><span data-stu-id="195f4-110">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="195f4-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="195f4-111">HRESULT</span></span>|<span data-ttu-id="195f4-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="195f4-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="195f4-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="195f4-113">S_OK</span></span>|<span data-ttu-id="195f4-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="195f4-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="195f4-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="195f4-115">S_FALSE</span></span>|<span data-ttu-id="195f4-116">`pceltFetched`não é igual a `celt`.</span><span class="sxs-lookup"><span data-stu-id="195f4-116">`pceltFetched` does not equal `celt`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="195f4-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="195f4-117">Remarks</span></span>  
 <span data-ttu-id="195f4-118">Essas funções de método como um enumerador COM típico.</span><span class="sxs-lookup"><span data-stu-id="195f4-118">This method functions like a typical COM enumerator.</span></span>  
  
 <span data-ttu-id="195f4-119">Os valores da matriz de entrada devem ser pelo menos do tamanho `celt`.</span><span class="sxs-lookup"><span data-stu-id="195f4-119">The input array values must be at least of size `celt`.</span></span> <span data-ttu-id="195f4-120">A matriz será preenchida com o próximo `celt` valores na enumeração ou com todos os valores restantes se menos de `celt` permanecem.</span><span class="sxs-lookup"><span data-stu-id="195f4-120">The array will be filled with either the next `celt` values in the enumeration or with all remaining values if fewer than `celt` remain.</span></span> <span data-ttu-id="195f4-121">Quando este método retorna, `pceltFetched` será preenchido com o número de valores que foram recuperados.</span><span class="sxs-lookup"><span data-stu-id="195f4-121">When this method returns, `pceltFetched` will be filled with the number of values that were retrieved.</span></span> <span data-ttu-id="195f4-122">Se `values` contém ponteiros inválidos ou aponta para um buffer que é menor do que `celt`, ou se `pceltFetched` é um ponteiro inválido, o resultado é indefinido.</span><span class="sxs-lookup"><span data-stu-id="195f4-122">If `values` contains invalid pointers or points to a buffer that is smaller than `celt`, or if `pceltFetched` is an invalid pointer, the result is undefined.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="195f4-123">Embora o [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) estrutura não precisa ser liberado, a interface "ICorDebugValue" dentro do elemento precisam ser liberados.</span><span class="sxs-lookup"><span data-stu-id="195f4-123">Although the [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure does not need to be released, the "ICorDebugValue" interface inside of it does need to be released.</span></span>  
  
-  
  
## <a name="requirements"></a><span data-ttu-id="195f4-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="195f4-124">Requirements</span></span>  
 <span data-ttu-id="195f4-125">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="195f4-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="195f4-126">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="195f4-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="195f4-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="195f4-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="195f4-128">**Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="195f4-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="195f4-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="195f4-129">See Also</span></span>  
 [<span data-ttu-id="195f4-130">Interface ICorDebugDataTarget</span><span class="sxs-lookup"><span data-stu-id="195f4-130">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)  
 [<span data-ttu-id="195f4-131">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="195f4-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [<span data-ttu-id="195f4-132">Depuração</span><span class="sxs-lookup"><span data-stu-id="195f4-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
