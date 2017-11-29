---
title: "Método ISymUnmanagedReader::GetDocument"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedReader.GetDocument
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedReader::GetDocument
helpviewer_keywords:
- ISymUnmanagedReader::GetDocument method [.NET Framework debugging]
- GetDocument method [.NET Framework debugging]
ms.assetid: bb203853-6a6d-4027-b9e9-603a7f28b9d3
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 7fcc18b1441093a3e3a1a0e813ccfb4ba3ad507b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedreadergetdocument-method"></a><span data-ttu-id="0af29-102">Método ISymUnmanagedReader::GetDocument</span><span class="sxs-lookup"><span data-stu-id="0af29-102">ISymUnmanagedReader::GetDocument Method</span></span>
<span data-ttu-id="0af29-103">Localiza um documento.</span><span class="sxs-lookup"><span data-stu-id="0af29-103">Finds a document.</span></span> <span data-ttu-id="0af29-104">O idioma do documento, o fornecedor e o tipo são opcionais.</span><span class="sxs-lookup"><span data-stu-id="0af29-104">The document language, vendor, and type are optional.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0af29-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0af29-105">Syntax</span></span>  
  
```  
HRESULT GetDocument (  
    [in]  WCHAR  *url,  
    [in]  GUID   language,  
    [in]  GUID   languageVendor,  
    [in]  GUID   documentType,  
    [out, retval] ISymUnmanagedDocument** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="0af29-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0af29-106">Parameters</span></span>  
 `url`  
 <span data-ttu-id="0af29-107">[in] A URL que identifica o documento.</span><span class="sxs-lookup"><span data-stu-id="0af29-107">[in] The URL that identifies the document.</span></span>  
  
 `language`  
 <span data-ttu-id="0af29-108">[in] O idioma do documento.</span><span class="sxs-lookup"><span data-stu-id="0af29-108">[in] The document language.</span></span> <span data-ttu-id="0af29-109">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="0af29-109">This parameter is optional.</span></span>  
  
 `languageVendor`  
 <span data-ttu-id="0af29-110">[in] A identidade do fornecedor para o idioma do documento.</span><span class="sxs-lookup"><span data-stu-id="0af29-110">[in] The identity of the vendor for the document language.</span></span> <span data-ttu-id="0af29-111">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="0af29-111">This parameter is optional.</span></span>  
  
 `documentType`  
 <span data-ttu-id="0af29-112">[in] O tipo do documento.</span><span class="sxs-lookup"><span data-stu-id="0af29-112">[in] The type of the document.</span></span> <span data-ttu-id="0af29-113">Esse parâmetro é opcional.</span><span class="sxs-lookup"><span data-stu-id="0af29-113">This parameter is optional.</span></span>  
  
 `pRetVal`  
 <span data-ttu-id="0af29-114">[out] Um ponteiro para a interface retornado.</span><span class="sxs-lookup"><span data-stu-id="0af29-114">[out] A pointer to the returned interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0af29-115">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0af29-115">Return Value</span></span>  
 <span data-ttu-id="0af29-116">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="0af29-116">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0af29-117">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0af29-117">Requirements</span></span>  
 <span data-ttu-id="0af29-118">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0af29-118">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0af29-119">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0af29-119">See Also</span></span>  
 [<span data-ttu-id="0af29-120">Interface ISymUnmanagedReader</span><span class="sxs-lookup"><span data-stu-id="0af29-120">ISymUnmanagedReader Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedreader-interface.md)
