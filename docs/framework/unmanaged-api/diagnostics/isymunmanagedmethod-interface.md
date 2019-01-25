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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b19e5ce88ea34188b2757d2a0c313341fbf1e7e6
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604225"
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="6f9f5-102">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="6f9f5-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="6f9f5-103">Representa um método no repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="6f9f5-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="6f9f5-104">Essa interface fornece acesso a somente os atributos relacionados ao símbolo de um método, em vez dos atributos de tipo.</span><span class="sxs-lookup"><span data-stu-id="6f9f5-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="6f9f5-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="6f9f5-105">Methods</span></span>  
  
|<span data-ttu-id="6f9f5-106">Método</span><span class="sxs-lookup"><span data-stu-id="6f9f5-106">Method</span></span>|<span data-ttu-id="6f9f5-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="6f9f5-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="6f9f5-108">Método GetNamespace</span><span class="sxs-lookup"><span data-stu-id="6f9f5-108">GetNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="6f9f5-109">Obtém o namespace no qual este método é definido.</span><span class="sxs-lookup"><span data-stu-id="6f9f5-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="6f9f5-110">Método GetOffset</span><span class="sxs-lookup"><span data-stu-id="6f9f5-110">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="6f9f5-111">Retorna o deslocamento dentro desse método que corresponde a uma determinada posição dentro de um documento.</span><span class="sxs-lookup"><span data-stu-id="6f9f5-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="6f9f5-112">Método GetParameters</span><span class="sxs-lookup"><span data-stu-id="6f9f5-112">GetParameters Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="6f9f5-113">Obtém os parâmetros para esse método.</span><span class="sxs-lookup"><span data-stu-id="6f9f5-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="6f9f5-114">Método GetRanges</span><span class="sxs-lookup"><span data-stu-id="6f9f5-114">GetRanges Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="6f9f5-115">Dado uma posição em um documento, retorna uma matriz de pares de deslocamento inicial e final que correspondem aos intervalos de Microsoft intermediate language (MSIL) que a posição cobre dentro desse método.</span><span class="sxs-lookup"><span data-stu-id="6f9f5-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="6f9f5-116">Método GetRootScope</span><span class="sxs-lookup"><span data-stu-id="6f9f5-116">GetRootScope Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="6f9f5-117">Obtém o escopo do léxico raiz dentro desse método.</span><span class="sxs-lookup"><span data-stu-id="6f9f5-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="6f9f5-118">Esse escopo abrange todo o método.</span><span class="sxs-lookup"><span data-stu-id="6f9f5-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="6f9f5-119">Método GetScopeFromOffset</span><span class="sxs-lookup"><span data-stu-id="6f9f5-119">GetScopeFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="6f9f5-120">Obtém o escopo léxico mais delimitador dentro desse método que inclui o deslocamento especificado.</span><span class="sxs-lookup"><span data-stu-id="6f9f5-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="6f9f5-121">Método GetSequencePointCount</span><span class="sxs-lookup"><span data-stu-id="6f9f5-121">GetSequencePointCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="6f9f5-122">Obtém a contagem de pontos de sequência dentro desse método.</span><span class="sxs-lookup"><span data-stu-id="6f9f5-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="6f9f5-123">Método GetSequencePoints</span><span class="sxs-lookup"><span data-stu-id="6f9f5-123">GetSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="6f9f5-124">Obtém todos os pontos de sequência dentro desse método.</span><span class="sxs-lookup"><span data-stu-id="6f9f5-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="6f9f5-125">Método GetSourceStartEnd</span><span class="sxs-lookup"><span data-stu-id="6f9f5-125">GetSourceStartEnd Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="6f9f5-126">Obtém as posições inicial e final no documento para a fonte deste método.</span><span class="sxs-lookup"><span data-stu-id="6f9f5-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="6f9f5-127">Método GetToken</span><span class="sxs-lookup"><span data-stu-id="6f9f5-127">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="6f9f5-128">Retorna o token de metadados para esse método.</span><span class="sxs-lookup"><span data-stu-id="6f9f5-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="6f9f5-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6f9f5-129">Requirements</span></span>  
 <span data-ttu-id="6f9f5-130">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6f9f5-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f9f5-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f9f5-131">See also</span></span>
- [<span data-ttu-id="6f9f5-132">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="6f9f5-132">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
