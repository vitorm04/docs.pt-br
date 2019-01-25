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
ms.openlocfilehash: d1c214918b4a41ac989a3804c9146c4a54c5909f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54738203"
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="6ea7d-102">Método ISymUnmanagedWriter::DefineDocument</span><span class="sxs-lookup"><span data-stu-id="6ea7d-102">ISymUnmanagedWriter::DefineDocument Method</span></span>
<span data-ttu-id="6ea7d-103">Define um documento de origem.</span><span class="sxs-lookup"><span data-stu-id="6ea7d-103">Defines a source document.</span></span> <span data-ttu-id="6ea7d-104">GUIDs são fornecidos para linguagens mais conhecidas, fornecedores e tipos de documento.</span><span class="sxs-lookup"><span data-stu-id="6ea7d-104">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6ea7d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6ea7d-105">Syntax</span></span>  
  
```  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6ea7d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6ea7d-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="6ea7d-107">[in] Um ponteiro para um `WCHAR` que define o localizador recursos uniforme (URL) que identifica o documento.</span><span class="sxs-lookup"><span data-stu-id="6ea7d-107">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="6ea7d-108">[in] Um ponteiro para um GUID que define o idioma do documento.</span><span class="sxs-lookup"><span data-stu-id="6ea7d-108">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="6ea7d-109">[in] Um ponteiro para um GUID que define a identidade do fornecedor para o idioma do documento.</span><span class="sxs-lookup"><span data-stu-id="6ea7d-109">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="6ea7d-110">[in] Um ponteiro para um GUID que define o tipo do documento.</span><span class="sxs-lookup"><span data-stu-id="6ea7d-110">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="6ea7d-111">[out] Um ponteiro para retornado [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="6ea7d-111">[out] A pointer to the returned [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6ea7d-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6ea7d-112">Return Value</span></span>  
 <span data-ttu-id="6ea7d-113">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="6ea7d-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6ea7d-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6ea7d-114">Requirements</span></span>  
 <span data-ttu-id="6ea7d-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6ea7d-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ea7d-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6ea7d-116">See also</span></span>
- [<span data-ttu-id="6ea7d-117">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="6ea7d-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
