---
title: Interface ISymUnmanagedMethod
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod
helpviewer_keywords:
- ISymUnmanagedMethod interface [.NET Framework debugging]
ms.assetid: f204d74c-cc79-4092-83bb-60654be95649
topic_type:
- apiref
ms.openlocfilehash: 1d3ccb2265f056d5776199d997dc067c8d5513e5
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448791"
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="73596-102">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="73596-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="73596-103">Represents a method within the symbol store.</span><span class="sxs-lookup"><span data-stu-id="73596-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="73596-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span><span class="sxs-lookup"><span data-stu-id="73596-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="73596-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="73596-105">Methods</span></span>  
  
|<span data-ttu-id="73596-106">Método</span><span class="sxs-lookup"><span data-stu-id="73596-106">Method</span></span>|<span data-ttu-id="73596-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="73596-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="73596-108">Método GetNamespace</span><span class="sxs-lookup"><span data-stu-id="73596-108">GetNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="73596-109">Gets the namespace within which this method is defined.</span><span class="sxs-lookup"><span data-stu-id="73596-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="73596-110">Método GetOffset</span><span class="sxs-lookup"><span data-stu-id="73596-110">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="73596-111">Returns the offset within this method that corresponds to a given position within a document.</span><span class="sxs-lookup"><span data-stu-id="73596-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="73596-112">Método GetParameters</span><span class="sxs-lookup"><span data-stu-id="73596-112">GetParameters Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="73596-113">Gets the parameters for this method.</span><span class="sxs-lookup"><span data-stu-id="73596-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="73596-114">Método GetRanges</span><span class="sxs-lookup"><span data-stu-id="73596-114">GetRanges Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="73596-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span><span class="sxs-lookup"><span data-stu-id="73596-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="73596-116">Método GetRootScope</span><span class="sxs-lookup"><span data-stu-id="73596-116">GetRootScope Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="73596-117">Gets the root lexical scope within this method.</span><span class="sxs-lookup"><span data-stu-id="73596-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="73596-118">Esse escopo abrange todo o método.</span><span class="sxs-lookup"><span data-stu-id="73596-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="73596-119">Método GetScopeFromOffset</span><span class="sxs-lookup"><span data-stu-id="73596-119">GetScopeFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="73596-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span><span class="sxs-lookup"><span data-stu-id="73596-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="73596-121">Método GetSequencePointCount</span><span class="sxs-lookup"><span data-stu-id="73596-121">GetSequencePointCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="73596-122">Gets the count of sequence points within this method.</span><span class="sxs-lookup"><span data-stu-id="73596-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="73596-123">Método GetSequencePoints</span><span class="sxs-lookup"><span data-stu-id="73596-123">GetSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="73596-124">Gets all the sequence points within this method.</span><span class="sxs-lookup"><span data-stu-id="73596-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="73596-125">Método GetSourceStartEnd</span><span class="sxs-lookup"><span data-stu-id="73596-125">GetSourceStartEnd Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="73596-126">Gets the start and end document positions for the source of this method.</span><span class="sxs-lookup"><span data-stu-id="73596-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="73596-127">Método GetToken</span><span class="sxs-lookup"><span data-stu-id="73596-127">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="73596-128">Retorna o token de metadados para esse método.</span><span class="sxs-lookup"><span data-stu-id="73596-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="73596-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="73596-129">Requirements</span></span>  
 <span data-ttu-id="73596-130">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="73596-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="73596-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="73596-131">See also</span></span>

- [<span data-ttu-id="73596-132">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="73596-132">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
