---
title: "Método ISymUnmanagedDocument::GetDocumentType"
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3b6e2d81680c2aa5973c0095a6a3ba7cfa158031
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocumentgetdocumenttype-method"></a><span data-ttu-id="38287-102">Método ISymUnmanagedDocument::GetDocumentType</span><span class="sxs-lookup"><span data-stu-id="38287-102">ISymUnmanagedDocument::GetDocumentType Method</span></span>
<span data-ttu-id="38287-103">Obtém o tipo de documento deste documento.</span><span class="sxs-lookup"><span data-stu-id="38287-103">Gets the document type of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="38287-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="38287-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentType(  
    [out, retval] GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="38287-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="38287-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="38287-106">[out] Ponteiro para uma variável que recebe o tipo de documento.</span><span class="sxs-lookup"><span data-stu-id="38287-106">[out] Pointer to a variable that receives the document type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="38287-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="38287-107">Return Value</span></span>  
 <span data-ttu-id="38287-108">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="38287-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="38287-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="38287-109">See Also</span></span>  
 [<span data-ttu-id="38287-110">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="38287-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
