---
title: Método ISymUnmanagedDocument::GetDocumentType
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetDocumentType
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetDocumentType
helpviewer_keywords:
- ISymUnmanagedDocument::GetDocumentType method [.NET Framework debugging]
- GetDocumentType method [.NET Framework debugging]
ms.assetid: 2d381ab1-7e7c-4281-af2b-e54d879b3ef8
topic_type:
- apiref
ms.openlocfilehash: 3def5db8912bc7e27c0c76898b7bafc8eb3ebbd1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449195"
---
# <a name="isymunmanageddocumentgetdocumenttype-method"></a><span data-ttu-id="b5e24-102">Método ISymUnmanagedDocument::GetDocumentType</span><span class="sxs-lookup"><span data-stu-id="b5e24-102">ISymUnmanagedDocument::GetDocumentType Method</span></span>
<span data-ttu-id="b5e24-103">Obtém o tipo de documento deste documento.</span><span class="sxs-lookup"><span data-stu-id="b5e24-103">Gets the document type of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b5e24-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b5e24-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentType(  
    [out, retval] GUID*  pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="b5e24-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b5e24-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="b5e24-106">fora Ponteiro para uma variável que recebe o tipo de documento.</span><span class="sxs-lookup"><span data-stu-id="b5e24-106">[out] Pointer to a variable that receives the document type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b5e24-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b5e24-107">Return Value</span></span>  
 <span data-ttu-id="b5e24-108">S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="b5e24-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b5e24-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b5e24-109">See also</span></span>

- [<span data-ttu-id="b5e24-110">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="b5e24-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
