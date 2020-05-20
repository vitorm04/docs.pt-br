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
ms.openlocfilehash: 7a98a0c40f68cef9bab1ea2de0850208aaef77a0
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615118"
---
# <a name="isymunmanagedmethod-interface"></a><span data-ttu-id="a43aa-102">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="a43aa-102">ISymUnmanagedMethod Interface</span></span>
<span data-ttu-id="a43aa-103">Representa um método dentro do repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="a43aa-103">Represents a method within the symbol store.</span></span> <span data-ttu-id="a43aa-104">Essa interface fornece acesso apenas aos atributos relacionados a símbolos de um método, em vez dos atributos relacionados ao tipo.</span><span class="sxs-lookup"><span data-stu-id="a43aa-104">This interface provides access to only the symbol-related attributes of a method, instead of the type-related attributes.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="a43aa-105">Métodos</span><span class="sxs-lookup"><span data-stu-id="a43aa-105">Methods</span></span>  
  
|<span data-ttu-id="a43aa-106">Método</span><span class="sxs-lookup"><span data-stu-id="a43aa-106">Method</span></span>|<span data-ttu-id="a43aa-107">Descrição</span><span class="sxs-lookup"><span data-stu-id="a43aa-107">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="a43aa-108">Método GetNamespace</span><span class="sxs-lookup"><span data-stu-id="a43aa-108">GetNamespace Method</span></span>](isymunmanagedmethod-getnamespace-method.md)|<span data-ttu-id="a43aa-109">Obtém o namespace no qual esse método é definido.</span><span class="sxs-lookup"><span data-stu-id="a43aa-109">Gets the namespace within which this method is defined.</span></span>|  
|[<span data-ttu-id="a43aa-110">Método GetOffset</span><span class="sxs-lookup"><span data-stu-id="a43aa-110">GetOffset Method</span></span>](isymunmanagedmethod-getoffset-method.md)|<span data-ttu-id="a43aa-111">Retorna o deslocamento dentro desse método que corresponde a uma determinada posição dentro de um documento.</span><span class="sxs-lookup"><span data-stu-id="a43aa-111">Returns the offset within this method that corresponds to a given position within a document.</span></span>|  
|[<span data-ttu-id="a43aa-112">Método GetParameters</span><span class="sxs-lookup"><span data-stu-id="a43aa-112">GetParameters Method</span></span>](isymunmanagedmethod-getparameters-method.md)|<span data-ttu-id="a43aa-113">Obtém os parâmetros para este método.</span><span class="sxs-lookup"><span data-stu-id="a43aa-113">Gets the parameters for this method.</span></span>|  
|[<span data-ttu-id="a43aa-114">Método GetRanges</span><span class="sxs-lookup"><span data-stu-id="a43aa-114">GetRanges Method</span></span>](isymunmanagedmethod-getranges-method.md)|<span data-ttu-id="a43aa-115">Dada uma posição em um documento, retorna uma matriz de pares de deslocamento inicial e final que correspondem aos intervalos da MSIL (Microsoft Intermediate Language) que a posição aborda nesse método.</span><span class="sxs-lookup"><span data-stu-id="a43aa-115">Given a position in a document, returns an array of start and end offset pairs that correspond to the ranges of Microsoft intermediate language (MSIL) that the position covers within this method.</span></span>|  
|[<span data-ttu-id="a43aa-116">Método GetRootScope</span><span class="sxs-lookup"><span data-stu-id="a43aa-116">GetRootScope Method</span></span>](isymunmanagedmethod-getrootscope-method.md)|<span data-ttu-id="a43aa-117">Obtém o escopo léxico raiz dentro deste método.</span><span class="sxs-lookup"><span data-stu-id="a43aa-117">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="a43aa-118">Esse escopo abrange todo o método.</span><span class="sxs-lookup"><span data-stu-id="a43aa-118">This scope encloses the entire method.</span></span>|  
|[<span data-ttu-id="a43aa-119">Método GetScopeFromOffset</span><span class="sxs-lookup"><span data-stu-id="a43aa-119">GetScopeFromOffset Method</span></span>](isymunmanagedmethod-getscopefromoffset-method.md)|<span data-ttu-id="a43aa-120">Obtém o escopo léxico mais delimitador dentro desse método que envolve o deslocamento fornecido.</span><span class="sxs-lookup"><span data-stu-id="a43aa-120">Gets the most enclosing lexical scope within this method that encloses the given offset.</span></span>|  
|[<span data-ttu-id="a43aa-121">Método GetSequencePointCount</span><span class="sxs-lookup"><span data-stu-id="a43aa-121">GetSequencePointCount Method</span></span>](isymunmanagedmethod-getsequencepointcount-method.md)|<span data-ttu-id="a43aa-122">Obtém a contagem de pontos de sequência dentro deste método.</span><span class="sxs-lookup"><span data-stu-id="a43aa-122">Gets the count of sequence points within this method.</span></span>|  
|[<span data-ttu-id="a43aa-123">Método GetSequencePoints</span><span class="sxs-lookup"><span data-stu-id="a43aa-123">GetSequencePoints Method</span></span>](isymunmanagedmethod-getsequencepoints-method.md)|<span data-ttu-id="a43aa-124">Obtém todos os pontos de sequência dentro deste método.</span><span class="sxs-lookup"><span data-stu-id="a43aa-124">Gets all the sequence points within this method.</span></span>|  
|[<span data-ttu-id="a43aa-125">Método GetSourceStartEnd</span><span class="sxs-lookup"><span data-stu-id="a43aa-125">GetSourceStartEnd Method</span></span>](isymunmanagedmethod-getsourcestartend-method.md)|<span data-ttu-id="a43aa-126">Obtém as posições do documento inicial e final da origem deste método.</span><span class="sxs-lookup"><span data-stu-id="a43aa-126">Gets the start and end document positions for the source of this method.</span></span>|  
|[<span data-ttu-id="a43aa-127">Método GetToken</span><span class="sxs-lookup"><span data-stu-id="a43aa-127">GetToken Method</span></span>](isymunmanagedmethod-gettoken-method.md)|<span data-ttu-id="a43aa-128">Retorna o token de metadados para esse método.</span><span class="sxs-lookup"><span data-stu-id="a43aa-128">Returns the metadata token for this method.</span></span>|  
  
## <a name="requirements"></a><span data-ttu-id="a43aa-129">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a43aa-129">Requirements</span></span>  
 <span data-ttu-id="a43aa-130">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="a43aa-130">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a43aa-131">Confira também</span><span class="sxs-lookup"><span data-stu-id="a43aa-131">See also</span></span>

- [<span data-ttu-id="a43aa-132">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="a43aa-132">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
