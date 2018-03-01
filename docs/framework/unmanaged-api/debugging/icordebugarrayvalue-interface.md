---
title: ICorDebugArrayValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 35169f0dd2ca71400d3aebddf9d5e2ae6b72be07
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugarrayvalue-interface1"></a><span data-ttu-id="d7655-102">ICorDebugArrayValue Interface1</span><span class="sxs-lookup"><span data-stu-id="d7655-102">ICorDebugArrayValue Interface1</span></span>
<span data-ttu-id="d7655-103">Uma subclasse de ICorDebugHeapValue que representa uma matriz unidimensional ou multidimensional.</span><span class="sxs-lookup"><span data-stu-id="d7655-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="d7655-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="d7655-104">Methods</span></span>  
  
|<span data-ttu-id="d7655-105">Método</span><span class="sxs-lookup"><span data-stu-id="d7655-105">Method</span></span>|<span data-ttu-id="d7655-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="d7655-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="d7655-107">Método GetBaseIndicies</span><span class="sxs-lookup"><span data-stu-id="d7655-107">GetBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="d7655-108">Obtém o índice de base de cada dimensão da matriz.</span><span class="sxs-lookup"><span data-stu-id="d7655-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="d7655-109">Método GetCount</span><span class="sxs-lookup"><span data-stu-id="d7655-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="d7655-110">Obtém o número total de elementos na matriz.</span><span class="sxs-lookup"><span data-stu-id="d7655-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="d7655-111">Método GetDimensions</span><span class="sxs-lookup"><span data-stu-id="d7655-111">GetDimensions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="d7655-112">Obtém as dimensões da matriz.</span><span class="sxs-lookup"><span data-stu-id="d7655-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="d7655-113">Método GetElement</span><span class="sxs-lookup"><span data-stu-id="d7655-113">GetElement Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="d7655-114">Obtém um valor que representa o elemento especificado na matriz.</span><span class="sxs-lookup"><span data-stu-id="d7655-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="d7655-115">Método GetElementAtPosition</span><span class="sxs-lookup"><span data-stu-id="d7655-115">GetElementAtPosition Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="d7655-116">Obtém o elemento na posição determinada, tratando a matriz como uma matriz unidimensional com base em zero.</span><span class="sxs-lookup"><span data-stu-id="d7655-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="d7655-117">Método GetElementType</span><span class="sxs-lookup"><span data-stu-id="d7655-117">GetElementType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="d7655-118">Obtém o tipo simple dos elementos na matriz.</span><span class="sxs-lookup"><span data-stu-id="d7655-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="d7655-119">Método GetRank</span><span class="sxs-lookup"><span data-stu-id="d7655-119">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="d7655-120">Obtém o número de dimensões na matriz.</span><span class="sxs-lookup"><span data-stu-id="d7655-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="d7655-121">Método HasBaseIndicies</span><span class="sxs-lookup"><span data-stu-id="d7655-121">HasBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="d7655-122">Determina se a matriz tem índices base.</span><span class="sxs-lookup"><span data-stu-id="d7655-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d7655-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="d7655-123">Remarks</span></span>  
 <span data-ttu-id="d7655-124">`ICorDebugArrayValue`oferece suporte a matrizes unidimensionais e multidimensionais.</span><span class="sxs-lookup"><span data-stu-id="d7655-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7655-125">Esta interface não dá suporte a que está sendo chamado remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="d7655-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="d7655-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="d7655-126">Requirements</span></span>  
 <span data-ttu-id="d7655-127">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="d7655-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="d7655-128">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="d7655-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="d7655-129">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="d7655-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="d7655-130">**Versões do .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="d7655-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7655-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="d7655-131">See Also</span></span>  
 [<span data-ttu-id="d7655-132">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="d7655-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
