---
title: Interface ISymUnmanagedDocument
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument
helpviewer_keywords:
- ISymUnmanagedDocument interface [.NET Framework debugging]
ms.assetid: 5c26b366-6e81-467c-9dd0-02dd26fee0a3
topic_type:
- apiref
ms.openlocfilehash: 3fa7b6b19d81e374cdb09b07ec181a7f4249a5eb
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449098"
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="ffd95-102">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="ffd95-102">ISymUnmanagedDocument Interface</span></span>
<span data-ttu-id="ffd95-103">Representa um documento referenciado por um repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="ffd95-103">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="ffd95-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span><span class="sxs-lookup"><span data-stu-id="ffd95-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="ffd95-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span><span class="sxs-lookup"><span data-stu-id="ffd95-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="ffd95-106">You can store the document source in the symbol store and retrieve it through this interface.</span><span class="sxs-lookup"><span data-stu-id="ffd95-106">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="ffd95-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="ffd95-107">Methods</span></span>  
  
|<span data-ttu-id="ffd95-108">Método</span><span class="sxs-lookup"><span data-stu-id="ffd95-108">Method</span></span>|<span data-ttu-id="ffd95-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="ffd95-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="ffd95-110">Método FindClosestLine</span><span class="sxs-lookup"><span data-stu-id="ffd95-110">FindClosestLine Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="ffd95-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span><span class="sxs-lookup"><span data-stu-id="ffd95-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="ffd95-112">Método GetCheckSum</span><span class="sxs-lookup"><span data-stu-id="ffd95-112">GetCheckSum Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="ffd95-113">Obtém a soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="ffd95-113">Gets the checksum.</span></span>|  
|[<span data-ttu-id="ffd95-114">Método GetCheckSumAlgorithmId</span><span class="sxs-lookup"><span data-stu-id="ffd95-114">GetCheckSumAlgorithmId Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="ffd95-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span><span class="sxs-lookup"><span data-stu-id="ffd95-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="ffd95-116">Método GetDocumentType</span><span class="sxs-lookup"><span data-stu-id="ffd95-116">GetDocumentType Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="ffd95-117">Gets the document type of this document.</span><span class="sxs-lookup"><span data-stu-id="ffd95-117">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="ffd95-118">Método GetLanguage</span><span class="sxs-lookup"><span data-stu-id="ffd95-118">GetLanguage Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="ffd95-119">Gets the language identifier of this document.</span><span class="sxs-lookup"><span data-stu-id="ffd95-119">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="ffd95-120">Método GetLanguageVendor</span><span class="sxs-lookup"><span data-stu-id="ffd95-120">GetLanguageVendor Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="ffd95-121">Gets the language vendor of this document.</span><span class="sxs-lookup"><span data-stu-id="ffd95-121">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="ffd95-122">Método GetSourceLength</span><span class="sxs-lookup"><span data-stu-id="ffd95-122">GetSourceLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="ffd95-123">Obtém o comprimento, em bytes, da origem inserida.</span><span class="sxs-lookup"><span data-stu-id="ffd95-123">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="ffd95-124">Método GetSourceRange</span><span class="sxs-lookup"><span data-stu-id="ffd95-124">GetSourceRange Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="ffd95-125">Returns the specified range of the embedded source into the given buffer.</span><span class="sxs-lookup"><span data-stu-id="ffd95-125">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="ffd95-126">Método GetURL</span><span class="sxs-lookup"><span data-stu-id="ffd95-126">GetURL Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|<span data-ttu-id="ffd95-127">Returns the URL for this document.</span><span class="sxs-lookup"><span data-stu-id="ffd95-127">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="ffd95-128">Método HasEmbeddedSource</span><span class="sxs-lookup"><span data-stu-id="ffd95-128">HasEmbeddedSource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="ffd95-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span><span class="sxs-lookup"><span data-stu-id="ffd95-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="ffd95-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="ffd95-130">See also</span></span>

- [<span data-ttu-id="ffd95-131">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="ffd95-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
