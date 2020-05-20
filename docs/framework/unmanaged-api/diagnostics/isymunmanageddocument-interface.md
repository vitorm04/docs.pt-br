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
ms.openlocfilehash: a8ff6d3a925773e58e0713a87b167420c246f85b
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615560"
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="9e939-102">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="9e939-102">ISymUnmanagedDocument Interface</span></span>
<span data-ttu-id="9e939-103">Representa um documento referenciado por um repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="9e939-103">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="9e939-104">Um documento é definido por um Uniform Resource Locator (URL) e um GUID de tipo de documento.</span><span class="sxs-lookup"><span data-stu-id="9e939-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="9e939-105">Você pode localizar o documento independentemente de como ele é armazenado usando a URL e o tipo de documento GUID.</span><span class="sxs-lookup"><span data-stu-id="9e939-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="9e939-106">Você pode armazenar a origem do documento no repositório de símbolos e recuperá-lo por meio desta interface.</span><span class="sxs-lookup"><span data-stu-id="9e939-106">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="9e939-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="9e939-107">Methods</span></span>  
  
|<span data-ttu-id="9e939-108">Método</span><span class="sxs-lookup"><span data-stu-id="9e939-108">Method</span></span>|<span data-ttu-id="9e939-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="9e939-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="9e939-110">Método FindClosestLine</span><span class="sxs-lookup"><span data-stu-id="9e939-110">FindClosestLine Method</span></span>](isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="9e939-111">Retorna a linha mais próxima que é um ponto de sequência, dada uma linha neste documento que pode ou não ser um ponto de sequência.</span><span class="sxs-lookup"><span data-stu-id="9e939-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="9e939-112">Método GetCheckSum</span><span class="sxs-lookup"><span data-stu-id="9e939-112">GetCheckSum Method</span></span>](isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="9e939-113">Obtém a soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="9e939-113">Gets the checksum.</span></span>|  
|[<span data-ttu-id="9e939-114">Método GetCheckSumAlgorithmId</span><span class="sxs-lookup"><span data-stu-id="9e939-114">GetCheckSumAlgorithmId Method</span></span>](isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="9e939-115">Obtém o identificador de algoritmo de soma de verificação ou retorna um GUID de todos os zeros se não houver nenhuma soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="9e939-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="9e939-116">Método GetDocumentType</span><span class="sxs-lookup"><span data-stu-id="9e939-116">GetDocumentType Method</span></span>](isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="9e939-117">Obtém o tipo de documento deste documento.</span><span class="sxs-lookup"><span data-stu-id="9e939-117">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="9e939-118">Método GetLanguage</span><span class="sxs-lookup"><span data-stu-id="9e939-118">GetLanguage Method</span></span>](isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="9e939-119">Obtém o identificador de idioma deste documento.</span><span class="sxs-lookup"><span data-stu-id="9e939-119">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="9e939-120">Método GetLanguageVendor</span><span class="sxs-lookup"><span data-stu-id="9e939-120">GetLanguageVendor Method</span></span>](isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="9e939-121">Obtém o fornecedor do idioma deste documento.</span><span class="sxs-lookup"><span data-stu-id="9e939-121">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="9e939-122">Método GetSourceLength</span><span class="sxs-lookup"><span data-stu-id="9e939-122">GetSourceLength Method</span></span>](isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="9e939-123">Obtém o comprimento, em bytes, da origem inserida.</span><span class="sxs-lookup"><span data-stu-id="9e939-123">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="9e939-124">Método GetSourceRange</span><span class="sxs-lookup"><span data-stu-id="9e939-124">GetSourceRange Method</span></span>](isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="9e939-125">Retorna o intervalo especificado da fonte inserida para o buffer fornecido.</span><span class="sxs-lookup"><span data-stu-id="9e939-125">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="9e939-126">Método GetURL</span><span class="sxs-lookup"><span data-stu-id="9e939-126">GetURL Method</span></span>](isymunmanageddocument-geturl-method.md)|<span data-ttu-id="9e939-127">Retorna a URL deste documento.</span><span class="sxs-lookup"><span data-stu-id="9e939-127">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="9e939-128">Método HasEmbeddedSource</span><span class="sxs-lookup"><span data-stu-id="9e939-128">HasEmbeddedSource Method</span></span>](isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="9e939-129">Retorna `true` se o documento tem origem inserida nos símbolos de depuração; caso contrário, retorna `false` .</span><span class="sxs-lookup"><span data-stu-id="9e939-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9e939-130">Confira também</span><span class="sxs-lookup"><span data-stu-id="9e939-130">See also</span></span>

- [<span data-ttu-id="9e939-131">Interfaces de armazenamento de símbolo de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="9e939-131">Diagnostics Symbol Store Interfaces</span></span>](diagnostics-symbol-store-interfaces.md)
