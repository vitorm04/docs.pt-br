---
title: Interface ICorDebugArrayValue
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
ms.openlocfilehash: 67fd1a9174b04e42b53f2b866a1dfdd504362aa9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61645611"
---
# <a name="icordebugarrayvalue-interface"></a><span data-ttu-id="73279-102">Interface ICorDebugArrayValue</span><span class="sxs-lookup"><span data-stu-id="73279-102">ICorDebugArrayValue Interface</span></span>

<span data-ttu-id="73279-103">Uma subclasse de ICorDebugHeapValue que representa uma matriz unidimensional ou multidimensional.</span><span class="sxs-lookup"><span data-stu-id="73279-103">A subclass of ICorDebugHeapValue that represents a single-dimensional or multi-dimensional array.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="73279-104">Métodos</span><span class="sxs-lookup"><span data-stu-id="73279-104">Methods</span></span>  
  
|<span data-ttu-id="73279-105">Método</span><span class="sxs-lookup"><span data-stu-id="73279-105">Method</span></span>|<span data-ttu-id="73279-106">Descrição</span><span class="sxs-lookup"><span data-stu-id="73279-106">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="73279-107">Método GetBaseIndicies</span><span class="sxs-lookup"><span data-stu-id="73279-107">GetBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|<span data-ttu-id="73279-108">Obtém o índice de base de cada dimensão da matriz.</span><span class="sxs-lookup"><span data-stu-id="73279-108">Gets the base index of each dimension in the array.</span></span>|  
|[<span data-ttu-id="73279-109">Método GetCount</span><span class="sxs-lookup"><span data-stu-id="73279-109">GetCount Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|<span data-ttu-id="73279-110">Obtém o número total de elementos na matriz.</span><span class="sxs-lookup"><span data-stu-id="73279-110">Gets the total number of elements in the array.</span></span>|  
|[<span data-ttu-id="73279-111">Método GetDimensions</span><span class="sxs-lookup"><span data-stu-id="73279-111">GetDimensions Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|<span data-ttu-id="73279-112">Obtém as dimensões da matriz.</span><span class="sxs-lookup"><span data-stu-id="73279-112">Gets the dimensions of the array.</span></span>|  
|[<span data-ttu-id="73279-113">Método GetElement</span><span class="sxs-lookup"><span data-stu-id="73279-113">GetElement Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|<span data-ttu-id="73279-114">Obtém um valor que representa o elemento especificado na matriz.</span><span class="sxs-lookup"><span data-stu-id="73279-114">Gets a value representing the given element in the array.</span></span>|  
|[<span data-ttu-id="73279-115">Método GetElementAtPosition</span><span class="sxs-lookup"><span data-stu-id="73279-115">GetElementAtPosition Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|<span data-ttu-id="73279-116">Obtém o elemento na posição determinada, tratando da matriz como uma matriz unidimensional de base zero.</span><span class="sxs-lookup"><span data-stu-id="73279-116">Gets the element at the given position, treating the array as a zero-based, single-dimensional array.</span></span>|  
|[<span data-ttu-id="73279-117">Método GetElementType</span><span class="sxs-lookup"><span data-stu-id="73279-117">GetElementType Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|<span data-ttu-id="73279-118">Obtém o tipo simples dos elementos na matriz.</span><span class="sxs-lookup"><span data-stu-id="73279-118">Gets the simple type of the elements in the array.</span></span>|  
|[<span data-ttu-id="73279-119">Método GetRank</span><span class="sxs-lookup"><span data-stu-id="73279-119">GetRank Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|<span data-ttu-id="73279-120">Obtém o número de dimensões na matriz.</span><span class="sxs-lookup"><span data-stu-id="73279-120">Gets the number of dimensions in the array.</span></span>|  
|[<span data-ttu-id="73279-121">Método HasBaseIndicies</span><span class="sxs-lookup"><span data-stu-id="73279-121">HasBaseIndicies Method</span></span>](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|<span data-ttu-id="73279-122">Determina se a matriz tem índices de base.</span><span class="sxs-lookup"><span data-stu-id="73279-122">Determines whether the array has base indexes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="73279-123">Comentários</span><span class="sxs-lookup"><span data-stu-id="73279-123">Remarks</span></span>  
 <span data-ttu-id="73279-124">`ICorDebugArrayValue` dá suporte a matrizes unidimensionais e multidimensionais.</span><span class="sxs-lookup"><span data-stu-id="73279-124">`ICorDebugArrayValue` supports both single-dimensional and multi-dimensional arrays.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="73279-125">Essa interface não dá suporte a ser chamada remotamente, entre computadores ou entre processos.</span><span class="sxs-lookup"><span data-stu-id="73279-125">This interface does not support being called remotely, either cross-machine or cross-process.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="73279-126">Requisitos</span><span class="sxs-lookup"><span data-stu-id="73279-126">Requirements</span></span>  
 <span data-ttu-id="73279-127">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="73279-127">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="73279-128">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="73279-128">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="73279-129">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="73279-129">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="73279-130">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="73279-130">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73279-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73279-131">See also</span></span>

- [<span data-ttu-id="73279-132">Depurando interfaces</span><span class="sxs-lookup"><span data-stu-id="73279-132">Debugging Interfaces</span></span>](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
