---
title: ICorDebugArrayValue Interface1
ms.date: 03/30/2017
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b8e9e9c9f43b45bf4f5d65bf80394c0fcd71325
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559262"
---
# <a name="icordebugarrayvalue-interface1"></a><span data-ttu-id="74a7f-102">ICorDebugArrayValue Interface1</span><span class="sxs-lookup"><span data-stu-id="74a7f-102">ICorDebugArrayValue Interface1</span></span>
<span data-ttu-id="74a7f-103">Uma subclasse de ICorDebugHeapValue que representa uma matriz unidimensional ou multidimensional.</span><span class="sxs-lookup"><span data-stu-id="74a7f-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="74a7f-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="74a7f-104">Methods</span></span>  
  
|<span data-ttu-id="74a7f-105">Método</span><span class="sxs-lookup"><span data-stu-id="74a7f-105">Method</span></span>|<span data-ttu-id="74a7f-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="74a7f-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="74a7f-107">Método GetBaseIndicies</span><span class="sxs-lookup"><span data-stu-id="74a7f-107">GetBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="74a7f-108">Obtém o índice de base de cada dimensão da matriz.</span><span class="sxs-lookup"><span data-stu-id="74a7f-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="74a7f-109">Método GetCount</span><span class="sxs-lookup"><span data-stu-id="74a7f-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="74a7f-110">Obtém o número total de elementos na matriz.</span><span class="sxs-lookup"><span data-stu-id="74a7f-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="74a7f-111">Método GetDimensions</span><span class="sxs-lookup"><span data-stu-id="74a7f-111">GetDimensions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="74a7f-112">Obtém as dimensões da matriz.</span><span class="sxs-lookup"><span data-stu-id="74a7f-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="74a7f-113">Método GetElement</span><span class="sxs-lookup"><span data-stu-id="74a7f-113">GetElement Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="74a7f-114">Obtém um valor que representa o elemento especificado na matriz.</span><span class="sxs-lookup"><span data-stu-id="74a7f-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="74a7f-115">Método GetElementAtPosition</span><span class="sxs-lookup"><span data-stu-id="74a7f-115">GetElementAtPosition Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="74a7f-116">Obtém o elemento na posição determinada, tratando da matriz como uma matriz unidimensional de base zero.</span><span class="sxs-lookup"><span data-stu-id="74a7f-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="74a7f-117">Método GetElementType</span><span class="sxs-lookup"><span data-stu-id="74a7f-117">GetElementType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="74a7f-118">Obtém o tipo simples dos elementos na matriz.</span><span class="sxs-lookup"><span data-stu-id="74a7f-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="74a7f-119">Método GetRank</span><span class="sxs-lookup"><span data-stu-id="74a7f-119">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="74a7f-120">Obtém o número de dimensões na matriz.</span><span class="sxs-lookup"><span data-stu-id="74a7f-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="74a7f-121">Método HasBaseIndicies</span><span class="sxs-lookup"><span data-stu-id="74a7f-121">HasBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="74a7f-122">Determina se a matriz tem índices de base.</span><span class="sxs-lookup"><span data-stu-id="74a7f-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="74a7f-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="74a7f-123">Remarks</span></span>  
 <span data-ttu-id="74a7f-124">`ICorDebugArrayValue` dá suporte a matrizes unidimensionais e multidimensionais.</span><span class="sxs-lookup"><span data-stu-id="74a7f-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="74a7f-125">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="74a7f-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="74a7f-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="74a7f-126">Requirements</span></span>  
 <span data-ttu-id="74a7f-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="74a7f-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="74a7f-128">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="74a7f-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="74a7f-129">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="74a7f-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="74a7f-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="74a7f-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="74a7f-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="74a7f-131">See also</span></span>
- [<span data-ttu-id="74a7f-132">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="74a7f-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
