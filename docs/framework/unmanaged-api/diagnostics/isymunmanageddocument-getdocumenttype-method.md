---
title: "Método ISymUnmanagedDocument::GetDocumentType"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedDocument.GetDocumentType
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedDocument::GetDocumentType
helpviewer_keywords:
- ISymUnmanagedDocument::GetDocumentType method [.NET Framework debugging]
- GetDocumentType method [.NET Framework debugging]
ms.assetid: 2d381ab1-7e7c-4281-af2b-e54d879b3ef8
topic_type: apiref
caps.latest.revision: "7"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 71b173562412a185b562e86045456a3ce781f4c9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanageddocumentgetdocumenttype-method"></a><span data-ttu-id="e04aa-102">Método ISymUnmanagedDocument::GetDocumentType</span><span class="sxs-lookup"><span data-stu-id="e04aa-102">ISymUnmanagedDocument::GetDocumentType Method</span></span>
<span data-ttu-id="e04aa-103">Obtém o tipo de documento deste documento.</span><span class="sxs-lookup"><span data-stu-id="e04aa-103">Gets the document type of this document.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e04aa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e04aa-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentType(  
    [out, retval] GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e04aa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e04aa-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="e04aa-106">[out] Ponteiro para uma variável que recebe o tipo de documento.</span><span class="sxs-lookup"><span data-stu-id="e04aa-106">[out] Pointer to a variable that receives the document type.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e04aa-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e04aa-107">Return Value</span></span>  
 <span data-ttu-id="e04aa-108">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="e04aa-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e04aa-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e04aa-109">See Also</span></span>  
 [<span data-ttu-id="e04aa-110">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="e04aa-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
