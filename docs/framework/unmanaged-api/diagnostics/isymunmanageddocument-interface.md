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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b14333235882efb6da1ce011c109c67a1d149bf3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54584513"
---
# <a name="isymunmanageddocument-interface"></a><span data-ttu-id="df215-102">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="df215-102">ISymUnmanagedDocument Interface</span></span>
<span data-ttu-id="df215-103">Representa um documento referenciado por um repositório de símbolos.</span><span class="sxs-lookup"><span data-stu-id="df215-103">Represents a document referenced by a symbol store.</span></span> <span data-ttu-id="df215-104">Um documento é definido por um localizador recursos uniforme (URL) e um GUID de tipo de documento.</span><span class="sxs-lookup"><span data-stu-id="df215-104">A document is defined by a uniform resource locator (URL) and a document type GUID.</span></span> <span data-ttu-id="df215-105">Você pode localizar o documento, independentemente de como ele é armazenado usando a URL e GUID do tipo de documento.</span><span class="sxs-lookup"><span data-stu-id="df215-105">You can locate the document regardless of how it is stored by using the URL and document type GUID.</span></span> <span data-ttu-id="df215-106">Você pode armazenar a origem do documento no repositório de símbolos e recuperá-lo por meio dessa interface.</span><span class="sxs-lookup"><span data-stu-id="df215-106">You can store the document source in the symbol store and retrieve it through this interface.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="df215-107">Métodos</span><span class="sxs-lookup"><span data-stu-id="df215-107">Methods</span></span>  
  
|<span data-ttu-id="df215-108">Método</span><span class="sxs-lookup"><span data-stu-id="df215-108">Method</span></span>|<span data-ttu-id="df215-109">Descrição</span><span class="sxs-lookup"><span data-stu-id="df215-109">Description</span></span>|  
|------------|-----------------|  
|[<span data-ttu-id="df215-110">Método FindClosestLine</span><span class="sxs-lookup"><span data-stu-id="df215-110">FindClosestLine Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-findclosestline-method.md)|<span data-ttu-id="df215-111">Retorna a linha mais próxima que é um ponto de sequência, considerando uma linha neste documento que pode ou não ser um ponto de sequência.</span><span class="sxs-lookup"><span data-stu-id="df215-111">Returns the closest line that is a sequence point, given a line in this document that may or may not be a sequence point.</span></span>|  
|[<span data-ttu-id="df215-112">Método GetCheckSum</span><span class="sxs-lookup"><span data-stu-id="df215-112">GetCheckSum Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksum-method.md)|<span data-ttu-id="df215-113">Obtém a soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="df215-113">Gets the checksum.</span></span>|  
|[<span data-ttu-id="df215-114">Método GetCheckSumAlgorithmId</span><span class="sxs-lookup"><span data-stu-id="df215-114">GetCheckSumAlgorithmId Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getchecksumalgorithmid-method.md)|<span data-ttu-id="df215-115">Obtém o identificador de algoritmo de soma de verificação ou retorna um GUID de todos os zeros se não houver nenhuma soma de verificação.</span><span class="sxs-lookup"><span data-stu-id="df215-115">Gets the checksum algorithm identifier, or returns a GUID of all zeros if there is no checksum.</span></span>|  
|[<span data-ttu-id="df215-116">Método GetDocumentType</span><span class="sxs-lookup"><span data-stu-id="df215-116">GetDocumentType Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getdocumenttype-method.md)|<span data-ttu-id="df215-117">Obtém o tipo de documento deste documento.</span><span class="sxs-lookup"><span data-stu-id="df215-117">Gets the document type of this document.</span></span>|  
|[<span data-ttu-id="df215-118">Método GetLanguage</span><span class="sxs-lookup"><span data-stu-id="df215-118">GetLanguage Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguage-method.md)|<span data-ttu-id="df215-119">Obtém o identificador de idioma deste documento.</span><span class="sxs-lookup"><span data-stu-id="df215-119">Gets the language identifier of this document.</span></span>|  
|[<span data-ttu-id="df215-120">Método GetLanguageVendor</span><span class="sxs-lookup"><span data-stu-id="df215-120">GetLanguageVendor Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getlanguagevendor-method.md)|<span data-ttu-id="df215-121">Obtém o fornecedor de idioma deste documento.</span><span class="sxs-lookup"><span data-stu-id="df215-121">Gets the language vendor of this document.</span></span>|  
|[<span data-ttu-id="df215-122">Método GetSourceLength</span><span class="sxs-lookup"><span data-stu-id="df215-122">GetSourceLength Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcelength-method.md)|<span data-ttu-id="df215-123">Obtém o comprimento, em bytes, da origem inserida.</span><span class="sxs-lookup"><span data-stu-id="df215-123">Gets the length, in bytes, of the embedded source.</span></span>|  
|[<span data-ttu-id="df215-124">Método GetSourceRange</span><span class="sxs-lookup"><span data-stu-id="df215-124">GetSourceRange Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-getsourcerange-method.md)|<span data-ttu-id="df215-125">Retorna o intervalo especificado da origem inserida para o buffer fornecido.</span><span class="sxs-lookup"><span data-stu-id="df215-125">Returns the specified range of the embedded source into the given buffer.</span></span>|  
|[<span data-ttu-id="df215-126">Método GetURL</span><span class="sxs-lookup"><span data-stu-id="df215-126">GetURL Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-geturl-method.md)|<span data-ttu-id="df215-127">Retorna a URL deste documento.</span><span class="sxs-lookup"><span data-stu-id="df215-127">Returns the URL for this document.</span></span>|  
|[<span data-ttu-id="df215-128">Método HasEmbeddedSource</span><span class="sxs-lookup"><span data-stu-id="df215-128">HasEmbeddedSource Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-hasembeddedsource-method.md)|<span data-ttu-id="df215-129">Retorna `true` se o documento tem o código-fonte inserido em símbolos de depuração; caso contrário, retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="df215-129">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="df215-130">Consulte também</span><span class="sxs-lookup"><span data-stu-id="df215-130">See also</span></span>
- [<span data-ttu-id="df215-131">Interfaces do repositório de símbolos de diagnóstico</span><span class="sxs-lookup"><span data-stu-id="df215-131">Diagnostics Symbol Store Interfaces</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/diagnostics-symbol-store-interfaces.md)
