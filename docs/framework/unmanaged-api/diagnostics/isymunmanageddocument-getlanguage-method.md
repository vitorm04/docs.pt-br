---
title: "Método ISymUnmanagedDocument::GetLanguage"
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
- ISymUnmanagedDocument.GetLanguage
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetLanguage
helpviewer_keywords:
- ISymUnmanagedDocument::GetLanguage method [.NET Framework debugging]
- GetLanguage method [.NET Framework debugging]
ms.assetid: c6639418-e9f2-4a99-8ce2-ec9876e0bc79
topic_type:
- apiref
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 31fdd2caaf877372fa28693cdc5b09ddf601427c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanageddocumentgetlanguage-method"></a><span data-ttu-id="9a859-102">Método ISymUnmanagedDocument::GetLanguage</span><span class="sxs-lookup"><span data-stu-id="9a859-102">ISymUnmanagedDocument::GetLanguage Method</span></span>
<span data-ttu-id="9a859-103">Obtém o identificador de idioma deste documento</span><span class="sxs-lookup"><span data-stu-id="9a859-103">Gets the language identifier of this document</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9a859-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="9a859-104">Syntax</span></span>  
  
```  
HRESULT GetLanguage(  
    [out, retval]  GUID*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="9a859-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="9a859-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="9a859-106">[out] Um ponteiro para uma variável que recebe o identificador de idioma.</span><span class="sxs-lookup"><span data-stu-id="9a859-106">[out] A pointer to a variable that receives the language identifier.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="9a859-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="9a859-107">Return Value</span></span>  
 <span data-ttu-id="9a859-108">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="9a859-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9a859-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="9a859-109">See Also</span></span>  
 [<span data-ttu-id="9a859-110">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="9a859-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
