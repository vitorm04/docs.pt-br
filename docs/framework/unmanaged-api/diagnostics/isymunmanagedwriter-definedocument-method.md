---
title: Método ISymUnmanagedWriter::DefineDocument
ms.date: 03/30/2017
api_name:
- ISymUnmanagedWriter.DefineDocument
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedWriter::DefineDocument
helpviewer_keywords:
- ISymUnmanagedWriter::DefineDocument method [.NET Framework debugging]
- DefineDocument method [.NET Framework debugging]
ms.assetid: c3bf15b0-3250-4bbe-b9b5-c5d695289b6f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 726ac0e23f739f451e1a0ab66c4c36aa6edbe569
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59132126"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="97fe8-102">Método ISymUnmanagedWriter::DefineDocument</span><span class="sxs-lookup"><span data-stu-id="97fe8-102">ISymUnmanagedWriter::DefineDocument Method</span></span>
<span data-ttu-id="97fe8-103">Define um documento de origem.</span><span class="sxs-lookup"><span data-stu-id="97fe8-103">Defines a source document.</span></span> <span data-ttu-id="97fe8-104">GUIDs são fornecidos para linguagens mais conhecidas, fornecedores e tipos de documento.</span><span class="sxs-lookup"><span data-stu-id="97fe8-104">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97fe8-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="97fe8-105">Syntax</span></span>  
  
```  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97fe8-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="97fe8-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="97fe8-107">[in] Um ponteiro para um `WCHAR` que define o localizador recursos uniforme (URL) que identifica o documento.</span><span class="sxs-lookup"><span data-stu-id="97fe8-107">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="97fe8-108">[in] Um ponteiro para um GUID que define o idioma do documento.</span><span class="sxs-lookup"><span data-stu-id="97fe8-108">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="97fe8-109">[in] Um ponteiro para um GUID que define a identidade do fornecedor para o idioma do documento.</span><span class="sxs-lookup"><span data-stu-id="97fe8-109">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="97fe8-110">[in] Um ponteiro para um GUID que define o tipo do documento.</span><span class="sxs-lookup"><span data-stu-id="97fe8-110">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="97fe8-111">[out] Um ponteiro para retornado [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="97fe8-111">[out] A pointer to the returned [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97fe8-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="97fe8-112">Return Value</span></span>  
 <span data-ttu-id="97fe8-113">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="97fe8-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97fe8-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="97fe8-114">Requirements</span></span>  
 <span data-ttu-id="97fe8-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="97fe8-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97fe8-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97fe8-116">See also</span></span>

- [<span data-ttu-id="97fe8-117">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="97fe8-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
