---
title: Método ICorDebugBlockingObjectEnum::Next
ms.date: 03/30/2017
api_name:
- ICorDebugBlockingObjectEnum.Next Method
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugBlockingObjectEnum::Next
helpviewer_keywords:
- Next method, ICorDebugBlockingObjectEnum interface [.NET Framework debugging]
- ICorDebugBlockingObjectEnum::Next method [.NET Framework debugging]
ms.assetid: 0121753f-ebea-48d0-aeb2-ed7fda76dc60
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 889c3bb2d5e0cd1feb9e592e667d47dedd4ede36
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59171139"
---
# <a name="icordebugblockingobjectenumnext-method"></a><span data-ttu-id="63354-102">Método ICorDebugBlockingObjectEnum::Next</span><span class="sxs-lookup"><span data-stu-id="63354-102">ICorDebugBlockingObjectEnum::Next Method</span></span>
<span data-ttu-id="63354-103">Obtém o número especificado de [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objetos de enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="63354-103">Gets the specified number of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="63354-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="63354-104">Syntax</span></span>  
  
```  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
## <a name="parameters"></a><span data-ttu-id="63354-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="63354-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="63354-106">[in] O número de objetos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="63354-106">[in] The number of objects to retrieve.</span></span>  
  
 `values`  
 <span data-ttu-id="63354-107">[out] Uma matriz de ponteiros para [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objetos.</span><span class="sxs-lookup"><span data-stu-id="63354-107">[out] An array of pointers to [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="63354-108">[out] Um ponteiro para o número de objetos que foram recuperados.</span><span class="sxs-lookup"><span data-stu-id="63354-108">[out] A pointer to the number of objects that were retrieved.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="63354-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="63354-109">Return Value</span></span>  
 <span data-ttu-id="63354-110">Esse método retorna os HRESULTs específicos a seguir.</span><span class="sxs-lookup"><span data-stu-id="63354-110">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="63354-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="63354-111">HRESULT</span></span>|<span data-ttu-id="63354-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="63354-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="63354-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="63354-113">S_OK</span></span>|<span data-ttu-id="63354-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="63354-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="63354-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="63354-115">S_FALSE</span></span>|<span data-ttu-id="63354-116">`pceltFetched` não é igual a `celt`.</span><span class="sxs-lookup"><span data-stu-id="63354-116">`pceltFetched` does not equal `celt`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="63354-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="63354-117">Remarks</span></span>  
 <span data-ttu-id="63354-118">Este método funciona como um enumerador COM típico.</span><span class="sxs-lookup"><span data-stu-id="63354-118">This method functions like a typical COM enumerator.</span></span>  
  
 <span data-ttu-id="63354-119">Os valores da matriz de entrada devem ter pelo menos do tamanho `celt`.</span><span class="sxs-lookup"><span data-stu-id="63354-119">The input array values must be at least of size `celt`.</span></span> <span data-ttu-id="63354-120">A matriz será preenchida com qualquer um na próxima `celt` valores na enumeração ou com todos os valores restantes se menos de `celt` permanecem.</span><span class="sxs-lookup"><span data-stu-id="63354-120">The array will be filled with either the next `celt` values in the enumeration or with all remaining values if fewer than `celt` remain.</span></span> <span data-ttu-id="63354-121">Quando este método retorna, `pceltFetched` será preenchido com o número de valores que foram recuperados.</span><span class="sxs-lookup"><span data-stu-id="63354-121">When this method returns, `pceltFetched` will be filled with the number of values that were retrieved.</span></span> <span data-ttu-id="63354-122">Se `values` contém ponteiros inválidos ou aponta para um buffer que é menor do que `celt`, ou se `pceltFetched` é um ponteiro inválido, o resultado será indefinido.</span><span class="sxs-lookup"><span data-stu-id="63354-122">If `values` contains invalid pointers or points to a buffer that is smaller than `celt`, or if `pceltFetched` is an invalid pointer, the result is undefined.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="63354-123">Embora o [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) estrutura não precisa ser liberado, a interface "ICorDebugValue" dentro dele precisam ser liberados.</span><span class="sxs-lookup"><span data-stu-id="63354-123">Although the [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure does not need to be released, the "ICorDebugValue" interface inside of it does need to be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="63354-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="63354-124">Requirements</span></span>  
 <span data-ttu-id="63354-125">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="63354-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="63354-126">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="63354-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="63354-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="63354-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="63354-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="63354-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="63354-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="63354-129">See also</span></span>

- [<span data-ttu-id="63354-130">Interface ICorDebugDataTarget</span><span class="sxs-lookup"><span data-stu-id="63354-130">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="63354-131">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="63354-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="63354-132">Depuração</span><span class="sxs-lookup"><span data-stu-id="63354-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
