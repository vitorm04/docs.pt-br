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
ms.openlocfilehash: cd01dcbd45ecae84ccccffb510c20f580ae8c598
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939822"
---
# <a name="isymunmanageddocumentgetlanguagevendor-method"></a><span data-ttu-id="9f9ea-102">Método ISymUnmanagedDocument::GetLanguageVendor</span><span class="sxs-lookup"><span data-stu-id="9f9ea-102">ISymUnmanagedDocument::GetLanguageVendor Method</span></span>
<span data-ttu-id="9f9ea-103">Obtém o fornecedor de idioma deste documento.</span><span class="sxs-lookup"><span data-stu-id="9f9ea-103">Gets the language vendor of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9f9ea-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9f9ea-104">Syntax</span></span>  
  
```  
HRESULT GetLanguageVendor(  
    [out, retval]  GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="9f9ea-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9f9ea-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="9f9ea-106">[out] Um ponteiro para uma variável que recebe o fornecedor de idioma.</span><span class="sxs-lookup"><span data-stu-id="9f9ea-106">[out] A pointer to a variable that receives the language vendor.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9f9ea-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9f9ea-107">Return Value</span></span>  
 <span data-ttu-id="9f9ea-108">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="9f9ea-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f9ea-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9f9ea-109">See also</span></span>

- [<span data-ttu-id="9f9ea-110">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="9f9ea-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
