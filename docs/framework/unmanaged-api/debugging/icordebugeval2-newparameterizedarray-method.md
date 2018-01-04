---
title: "Método ICorDebugEval2::NewParameterizedArray"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval2.NewParameterizedArray
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval2::NewParameterizedArray
helpviewer_keywords:
- ICorDebugEval2::NewParameterizedArray method [.NET Framework debugging]
- NewParameterizedArray method [.NET Framework debugging]
ms.assetid: 45efb8ba-c4de-4109-945f-e734d376b43c
topic_type: apiref
caps.latest.revision: "15"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a605276fac66e395d5663bacff727c235981a868
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugeval2newparameterizedarray-method"></a><span data-ttu-id="de799-102">Método ICorDebugEval2::NewParameterizedArray</span><span class="sxs-lookup"><span data-stu-id="de799-102">ICorDebugEval2::NewParameterizedArray Method</span></span>
<span data-ttu-id="de799-103">Aloca uma nova matriz do tipo de elemento especificado e dimensões.</span><span class="sxs-lookup"><span data-stu-id="de799-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="de799-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="de799-104">Syntax</span></span>  
  
```  
HRESULT NewParameterizedArray(  
    [in] ICorDebugType          *pElementType,  
    [in] ULONG32                rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="de799-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="de799-105">Parameters</span></span>  
 `pElementType`  
 <span data-ttu-id="de799-106">[in] Um ponteiro para um objeto ICorDebugType que representa o tipo de elemento armazenado na matriz.</span><span class="sxs-lookup"><span data-stu-id="de799-106">[in] A pointer to an ICorDebugType object that represents the type of element stored in the array.</span></span>  
  
 `rank`  
 <span data-ttu-id="de799-107">[in] O número de dimensões da matriz.</span><span class="sxs-lookup"><span data-stu-id="de799-107">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="de799-108">No .NET Framework versão 2.0, esse valor deve ser 1.</span><span class="sxs-lookup"><span data-stu-id="de799-108">In the .NET Framework version 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="de799-109">[in] O tamanho, em bytes, de cada dimensão da matriz.</span><span class="sxs-lookup"><span data-stu-id="de799-109">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="de799-110">[in] Opcional.</span><span class="sxs-lookup"><span data-stu-id="de799-110">[in] Optional.</span></span> <span data-ttu-id="de799-111">O limite inferior de cada dimensão da matriz.</span><span class="sxs-lookup"><span data-stu-id="de799-111">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="de799-112">Se esse valor for omitido, um limite inferior de zero será assumido para cada dimensão.</span><span class="sxs-lookup"><span data-stu-id="de799-112">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="de799-113">Comentários</span><span class="sxs-lookup"><span data-stu-id="de799-113">Remarks</span></span>  
 <span data-ttu-id="de799-114">Os elementos da matriz podem ser instâncias de um tipo genérico.</span><span class="sxs-lookup"><span data-stu-id="de799-114">The elements of the array may be instances of a generic type.</span></span> <span data-ttu-id="de799-115">A matriz sempre é criada no domínio do aplicativo no qual o thread está sendo executado.</span><span class="sxs-lookup"><span data-stu-id="de799-115">The array is always created in the application domain in which the thread is currently running.</span></span> <span data-ttu-id="de799-116">No .NET Framework 2.0, o valor de `rank` deve ser 1.</span><span class="sxs-lookup"><span data-stu-id="de799-116">In the .NET Framework 2.0, the value of `rank` must be 1.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="de799-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="de799-117">Requirements</span></span>  
 <span data-ttu-id="de799-118">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="de799-118">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="de799-119">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="de799-119">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="de799-120">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="de799-120">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="de799-121">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="de799-121">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>
