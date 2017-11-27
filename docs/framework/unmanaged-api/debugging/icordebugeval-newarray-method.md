---
title: "Método ICorDebugEval::NewArray"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugEval.NewArray
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugEval::NewArray
helpviewer_keywords:
- NewArray method [.NET Framework debugging]
- ICorDebugEval::NewArray method [.NET Framework debugging]
ms.assetid: cc79a67d-5368-434d-a943-209db90491b9
topic_type: apiref
caps.latest.revision: "19"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: db9b5f7241e2be53cfbc2c6cea3da1b0182c3eb6
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugevalnewarray-method"></a><span data-ttu-id="78fd5-102">Método ICorDebugEval::NewArray</span><span class="sxs-lookup"><span data-stu-id="78fd5-102">ICorDebugEval::NewArray Method</span></span>
<span data-ttu-id="78fd5-103">Aloca uma nova matriz do tipo de elemento especificado e dimensões.</span><span class="sxs-lookup"><span data-stu-id="78fd5-103">Allocates a new array of the specified element type and dimensions.</span></span>  
  
 <span data-ttu-id="78fd5-104">Este método está obsoleto no .NET Framework versão 2.0.</span><span class="sxs-lookup"><span data-stu-id="78fd5-104">This method is obsolete in the .NET Framework version 2.0.</span></span> <span data-ttu-id="78fd5-105">Use [Icordebugeval2](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) em vez disso.</span><span class="sxs-lookup"><span data-stu-id="78fd5-105">Use [ICorDebugEval2::NewParameterizedArray](../../../../docs/framework/unmanaged-api/debugging/icordebugeval2-newparameterizedarray-method.md) instead.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="78fd5-106">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="78fd5-106">Syntax</span></span>  
  
```  
HRESULT NewArray (  
    [in] CorElementType     elementType,  
    [in] ICorDebugClass     *pElementClass,  
    [in] ULONG32            rank,  
    [in, size_is(rank)] ULONG32 dims[],  
    [in, size_is(rank)] ULONG32 lowBounds[]  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="78fd5-107">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="78fd5-107">Parameters</span></span>  
 `elementType`  
 <span data-ttu-id="78fd5-108">[in] Um valor da enumeração CorElementType que especifica o tipo de elemento da matriz.</span><span class="sxs-lookup"><span data-stu-id="78fd5-108">[in] A value of the CorElementType enumeration that specifies the element type of the array.</span></span>  
  
 `pElementClass`  
 <span data-ttu-id="78fd5-109">[in] Um ponteiro para um objeto de ICorDebugClass que especifica a classe do elemento.</span><span class="sxs-lookup"><span data-stu-id="78fd5-109">[in] A pointer to a ICorDebugClass object that specifies the class of the element.</span></span> <span data-ttu-id="78fd5-110">Esse valor pode ser null se o tipo de elemento é um tipo primitivo.</span><span class="sxs-lookup"><span data-stu-id="78fd5-110">This value may be null if the element type is a primitive type.</span></span>  
  
 `rank`  
 <span data-ttu-id="78fd5-111">[in] O número de dimensões da matriz.</span><span class="sxs-lookup"><span data-stu-id="78fd5-111">[in] The number of dimensions of the array.</span></span> <span data-ttu-id="78fd5-112">No .NET Framework 2.0, esse valor deve ser 1.</span><span class="sxs-lookup"><span data-stu-id="78fd5-112">In the .NET Framework 2.0, this value must be 1.</span></span>  
  
 `dims`  
 <span data-ttu-id="78fd5-113">[in] O tamanho, em bytes, de cada dimensão da matriz.</span><span class="sxs-lookup"><span data-stu-id="78fd5-113">[in] The size, in bytes, of each dimension of the array.</span></span>  
  
 `lowBounds`  
 <span data-ttu-id="78fd5-114">[in] Opcional.</span><span class="sxs-lookup"><span data-stu-id="78fd5-114">[in] Optional.</span></span> <span data-ttu-id="78fd5-115">O limite inferior de cada dimensão da matriz.</span><span class="sxs-lookup"><span data-stu-id="78fd5-115">The lower bound of each dimension of the array.</span></span> <span data-ttu-id="78fd5-116">Se esse valor for omitido, um limite inferior de zero será assumido para cada dimensão.</span><span class="sxs-lookup"><span data-stu-id="78fd5-116">If this value is omitted, a lower bound of zero is assumed for each dimension.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="78fd5-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="78fd5-117">Remarks</span></span>  
 <span data-ttu-id="78fd5-118">A matriz sempre é criada no domínio do aplicativo no qual o thread está em execução no momento.</span><span class="sxs-lookup"><span data-stu-id="78fd5-118">The array is always created in the application domain in which the thread is currently executing.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="78fd5-119">Requisitos</span><span class="sxs-lookup"><span data-stu-id="78fd5-119">Requirements</span></span>  
 <span data-ttu-id="78fd5-120">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="78fd5-120">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="78fd5-121">**Cabeçalho:** CorDebug.idl, CorDebug.h</span><span class="sxs-lookup"><span data-stu-id="78fd5-121">**Header:** CorDebug.idl, CorDebug.h</span></span>  
  
 <span data-ttu-id="78fd5-122">**Biblioteca:** CorGuids.lib</span><span class="sxs-lookup"><span data-stu-id="78fd5-122">**Library:** CorGuids.lib</span></span>  
  
 <span data-ttu-id="78fd5-123">**Versões do .NET framework:** 1.1 e 1.0</span><span class="sxs-lookup"><span data-stu-id="78fd5-123">**.NET Framework Versions:** 1.1, 1.0</span></span>
