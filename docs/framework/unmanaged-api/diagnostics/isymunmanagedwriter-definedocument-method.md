---
title: "Método ISymUnmanagedWriter::DefineDocument"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 522cc3a63101ec7ebe47e8e23878b9d1b12bca1e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedwriterdefinedocument-method"></a><span data-ttu-id="29a4c-102">Método ISymUnmanagedWriter::DefineDocument</span><span class="sxs-lookup"><span data-stu-id="29a4c-102">ISymUnmanagedWriter::DefineDocument Method</span></span>
<span data-ttu-id="29a4c-103">Define um documento de origem.</span><span class="sxs-lookup"><span data-stu-id="29a4c-103">Defines a source document.</span></span> <span data-ttu-id="29a4c-104">GUIDs são fornecidos para idiomas conhecidos, fornecedores e tipos de documento.</span><span class="sxs-lookup"><span data-stu-id="29a4c-104">GUIDs are provided for known languages, vendors, and document types.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29a4c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29a4c-105">Syntax</span></span>  
  
```  
HRESULT DefineDocument(  
    [in]  const WCHAR  *url,  
    [in]  const GUID   *language,  
    [in]  const GUID   *languageVendor,  
    [in]  const GUID   *documentType,  
    [out, retval] ISymUnmanagedDocumentWriter**  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="29a4c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="29a4c-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="29a4c-107">[in] Um ponteiro para um `WCHAR` que define o uniform resource locator (URL) que identifica o documento.</span><span class="sxs-lookup"><span data-stu-id="29a4c-107">[in] A pointer to a `WCHAR` that defines the uniform resource locator (URL) that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="29a4c-108">[in] Um ponteiro para um GUID que define o idioma do documento.</span><span class="sxs-lookup"><span data-stu-id="29a4c-108">[in] A pointer to a GUID that defines the document language.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="29a4c-109">[in] Um ponteiro para um GUID que define a identidade do fornecedor para o idioma do documento.</span><span class="sxs-lookup"><span data-stu-id="29a4c-109">[in] A pointer to a GUID that defines the identity of the vendor for the document language.</span></span>  
  
 `documentType`  
 <span data-ttu-id="29a4c-110">[in] Um ponteiro para um GUID que define o tipo do documento.</span><span class="sxs-lookup"><span data-stu-id="29a4c-110">[in] A pointer to a GUID that defines the type of the document.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="29a4c-111">[out] Um ponteiro para retornado [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="29a4c-111">[out] A pointer to the returned [ISymUnmanagedWriter](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29a4c-112">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="29a4c-112">Return Value</span></span>  
 <span data-ttu-id="29a4c-113">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="29a4c-113">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29a4c-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="29a4c-114">Requirements</span></span>  
 <span data-ttu-id="29a4c-115">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="29a4c-115">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29a4c-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29a4c-116">See Also</span></span>  
 [<span data-ttu-id="29a4c-117">Interface ISymUnmanagedWriter</span><span class="sxs-lookup"><span data-stu-id="29a4c-117">ISymUnmanagedWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedwriter-interface.md)
