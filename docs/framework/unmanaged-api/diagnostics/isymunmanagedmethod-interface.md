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
ms.openlocfilehash: 728acc09f739fe567fca4a2571cbabf1ba8838a2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427425"
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="df451-102">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="df451-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="df451-103">Representa um método no repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="df451-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="df451-104">Essa interface fornece acesso a apenas os atributos relacionados ao símbolo de um método, em vez dos atributos de tipo.</span><span class="sxs-lookup"><span data-stu-id="df451-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="df451-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="df451-105">Methods</span></span>  
  
|<span data-ttu-id="df451-106">Método</span><span class="sxs-lookup"><span data-stu-id="df451-106">Method</span></span>|<span data-ttu-id="df451-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="df451-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="df451-108">Método GetNamespace</span><span class="sxs-lookup"><span data-stu-id="df451-108">GetNamespace Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="df451-109">Obtém o namespace no qual esse método é definido.</span><span class="sxs-lookup"><span data-stu-id="df451-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="df451-110">Método GetOffset</span><span class="sxs-lookup"><span data-stu-id="df451-110">GetOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="df451-111">Retorna o deslocamento dentro desse método que corresponde à posição especificada dentro de um documento.</span><span class="sxs-lookup"><span data-stu-id="df451-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="df451-112">Método GetParameters</span><span class="sxs-lookup"><span data-stu-id="df451-112">GetParameters Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="df451-113">Obtém os parâmetros para este método.</span><span class="sxs-lookup"><span data-stu-id="df451-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="df451-114">Método GetRanges</span><span class="sxs-lookup"><span data-stu-id="df451-114">GetRanges Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="df451-115">Fornecido uma posição em um documento, retorna uma matriz de pares deslocamentos de início e término que correspondem aos intervalos de Microsoft intermediate language (MSIL) que abrange a posição dentro desse método.</span><span class="sxs-lookup"><span data-stu-id="df451-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="df451-116">Método GetRootScope</span><span class="sxs-lookup"><span data-stu-id="df451-116">GetRootScope Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="df451-117">Obtém o escopo léxico raiz dentro desse método.</span><span class="sxs-lookup"><span data-stu-id="df451-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="df451-118">Esse escopo abrange todo o método.</span><span class="sxs-lookup"><span data-stu-id="df451-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="df451-119">Método GetScopeFromOffset</span><span class="sxs-lookup"><span data-stu-id="df451-119">GetScopeFromOffset Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="df451-120">Obtém o escopo léxico mais delimitador dentro desse método que inclui o deslocamento especificado.</span><span class="sxs-lookup"><span data-stu-id="df451-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="df451-121">Método GetSequencePointCount</span><span class="sxs-lookup"><span data-stu-id="df451-121">GetSequencePointCount Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="df451-122">Obtém a contagem de pontos de sequência dentro desse método.</span><span class="sxs-lookup"><span data-stu-id="df451-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="df451-123">Método GetSequencePoints</span><span class="sxs-lookup"><span data-stu-id="df451-123">GetSequencePoints Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="df451-124">Obtém todos os pontos de sequência dentro desse método.</span><span class="sxs-lookup"><span data-stu-id="df451-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="df451-125">Método GetSourceStartEnd</span><span class="sxs-lookup"><span data-stu-id="df451-125">GetSourceStartEnd Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="df451-126">Obtém as posições de documento de início e término para a fonte deste método.</span><span class="sxs-lookup"><span data-stu-id="df451-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="df451-127">Método GetToken</span><span class="sxs-lookup"><span data-stu-id="df451-127">GetToken Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="df451-128">Retorna o token de metadados para esse método.</span><span class="sxs-lookup"><span data-stu-id="df451-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="df451-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="df451-129">Requirements</span></span>  
 <span data-ttu-id="df451-130">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="df451-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="df451-131">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df451-131">See Also</span></span>  
 [<span data-ttu-id="df451-132">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="df451-132">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
