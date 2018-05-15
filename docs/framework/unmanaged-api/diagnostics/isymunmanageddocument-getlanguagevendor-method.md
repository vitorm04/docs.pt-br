---
title: Método ISymUnmanagedDocument::GetLanguageVendor
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetLanguageVendor
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguageVendor
helpviewer_keywords:
- GetLanguageVendor method [.NET Framework debugging]
- ISymUnmanagedDocument::GetLanguageVendor method [.NET Framework debugging]
ms.assetid: 1d4b702e-4922-441d-8b44-03804284f70b
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0a6830f47d5cac2cf9c84144c18486489b0ec581
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanageddocumentgetlanguagevendor-method"></a><span data-ttu-id="3fcd0-102">Método ISymUnmanagedDocument::GetLanguageVendor</span><span class="sxs-lookup"><span data-stu-id="3fcd0-102">ISymUnmanagedDocument::GetLanguageVendor Method</span></span>
<span data-ttu-id="3fcd0-103">Obtém o fornecedor do idioma deste documento.</span><span class="sxs-lookup"><span data-stu-id="3fcd0-103">Gets the language vendor of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3fcd0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3fcd0-104">Syntax</span></span>  
  
```  
HRESULT GetLanguageVendor(  
    [out, retval]  GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="3fcd0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="3fcd0-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="3fcd0-106">[out] Um ponteiro para uma variável que recebe o fornecedor do idioma.</span><span class="sxs-lookup"><span data-stu-id="3fcd0-106">[out] A pointer to a variable that receives the language vendor.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3fcd0-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="3fcd0-107">Return Value</span></span>  
 <span data-ttu-id="3fcd0-108">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="3fcd0-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3fcd0-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="3fcd0-109">See Also</span></span>  
 [<span data-ttu-id="3fcd0-110">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="3fcd0-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
