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
ms.openlocfilehash: 3a1c4a931a61186c4737aada47ceb861e7848e7b
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122838"
---
# <a name="icordebugblockingobjectenumnext-method"></a><span data-ttu-id="96774-102">Método ICorDebugBlockingObjectEnum::Next</span><span class="sxs-lookup"><span data-stu-id="96774-102">ICorDebugBlockingObjectEnum::Next Method</span></span>
<span data-ttu-id="96774-103">Obtém o número especificado de objetos [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) da enumeração, começando na posição atual.</span><span class="sxs-lookup"><span data-stu-id="96774-103">Gets the specified number of [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects from the enumeration, starting at the current position.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96774-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96774-104">Syntax</span></span>  
  
```cpp  
HRESULT Next([in] ULONG  celt,  
             [out, size_is(celt), length_is(*pceltFetched)]  
                           CorDebugBlockingObject values[],  
             [out] ULONG *pceltFetched;  
```  
  
## <a name="parameters"></a><span data-ttu-id="96774-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="96774-105">Parameters</span></span>  
 `celt`  
 <span data-ttu-id="96774-106">no O número de objetos a serem recuperados.</span><span class="sxs-lookup"><span data-stu-id="96774-106">[in] The number of objects to retrieve.</span></span>  
  
 `values`  
 <span data-ttu-id="96774-107">fora Uma matriz de ponteiros para objetos [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) .</span><span class="sxs-lookup"><span data-stu-id="96774-107">[out] An array of pointers to [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) objects.</span></span>  
  
 `pceltFetched`  
 <span data-ttu-id="96774-108">fora Um ponteiro para o número de objetos que foram recuperados.</span><span class="sxs-lookup"><span data-stu-id="96774-108">[out] A pointer to the number of objects that were retrieved.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96774-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="96774-109">Return Value</span></span>  
 <span data-ttu-id="96774-110">Esse método retorna os HRESULTs específicos a seguir.</span><span class="sxs-lookup"><span data-stu-id="96774-110">This method returns the following specific HRESULTs.</span></span>  
  
|<span data-ttu-id="96774-111">HRESULT</span><span class="sxs-lookup"><span data-stu-id="96774-111">HRESULT</span></span>|<span data-ttu-id="96774-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="96774-112">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="96774-113">S_OK</span><span class="sxs-lookup"><span data-stu-id="96774-113">S_OK</span></span>|<span data-ttu-id="96774-114">O método foi concluído com êxito.</span><span class="sxs-lookup"><span data-stu-id="96774-114">The method completed successfully.</span></span>|  
|<span data-ttu-id="96774-115">S_FALSE</span><span class="sxs-lookup"><span data-stu-id="96774-115">S_FALSE</span></span>|<span data-ttu-id="96774-116">`pceltFetched` não é igual a `celt`.</span><span class="sxs-lookup"><span data-stu-id="96774-116">`pceltFetched` does not equal `celt`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="96774-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="96774-117">Remarks</span></span>  
 <span data-ttu-id="96774-118">Esse método funciona como um enumerador COM típico.</span><span class="sxs-lookup"><span data-stu-id="96774-118">This method functions like a typical COM enumerator.</span></span>  
  
 <span data-ttu-id="96774-119">Os valores de matriz de entrada devem ter pelo menos `celt`de tamanho.</span><span class="sxs-lookup"><span data-stu-id="96774-119">The input array values must be at least of size `celt`.</span></span> <span data-ttu-id="96774-120">A matriz será preenchida com os valores de `celt` seguintes na enumeração ou com todos os valores restantes se menos de `celt` permanecerem.</span><span class="sxs-lookup"><span data-stu-id="96774-120">The array will be filled with either the next `celt` values in the enumeration or with all remaining values if fewer than `celt` remain.</span></span> <span data-ttu-id="96774-121">Quando esse método retornar, `pceltFetched` será preenchido com o número de valores que foram recuperados.</span><span class="sxs-lookup"><span data-stu-id="96774-121">When this method returns, `pceltFetched` will be filled with the number of values that were retrieved.</span></span> <span data-ttu-id="96774-122">Se `values` contiver ponteiros ou pontos inválidos para um buffer menor do que `celt`ou se `pceltFetched` for um ponteiro inválido, o resultado será indefinido.</span><span class="sxs-lookup"><span data-stu-id="96774-122">If `values` contains invalid pointers or points to a buffer that is smaller than `celt`, or if `pceltFetched` is an invalid pointer, the result is undefined.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="96774-123">Embora a estrutura [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) não precise ser liberada, a interface "ICorDebugValue" dentro dela precisa ser liberada.</span><span class="sxs-lookup"><span data-stu-id="96774-123">Although the [CorDebugBlockingObject](../../../../docs/framework/unmanaged-api/debugging/cordebugblockingobject-structure.md) structure does not need to be released, the "ICorDebugValue" interface inside of it does need to be released.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96774-124">Requisitos</span><span class="sxs-lookup"><span data-stu-id="96774-124">Requirements</span></span>  
 <span data-ttu-id="96774-125">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="96774-125">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="96774-126">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="96774-126">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="96774-127">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="96774-127">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="96774-128">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="96774-128">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96774-129">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96774-129">See also</span></span>

- [<span data-ttu-id="96774-130">Interface ICorDebugDataTarget</span><span class="sxs-lookup"><span data-stu-id="96774-130">ICorDebugDataTarget Interface</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-interface.md)
- [<span data-ttu-id="96774-131">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="96774-131">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [<span data-ttu-id="96774-132">Depuração</span><span class="sxs-lookup"><span data-stu-id="96774-132">Debugging</span></span>](../../../../docs/framework/unmanaged-api/debugging/index.md)
