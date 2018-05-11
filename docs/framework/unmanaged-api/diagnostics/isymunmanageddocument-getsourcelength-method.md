---
title: Método ISymUnmanagedDocument::GetSourceLength
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.GetSourceLength
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::GetSourceLength
helpviewer_keywords:
- GetSourceLength method [.NET Framework debugging]
- ISymUnmanagedDocument::GetSourceLength method [.NET Framework debugging]
ms.assetid: e087dbbb-f4fb-4fbe-8292-e4f1a14d0df2
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3341159600c85915cd3c1a138265dc386edbb766
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="isymunmanageddocumentgetsourcelength-method"></a><span data-ttu-id="6d4fd-102">Método ISymUnmanagedDocument::GetSourceLength</span><span class="sxs-lookup"><span data-stu-id="6d4fd-102">ISymUnmanagedDocument::GetSourceLength Method</span></span>
<span data-ttu-id="6d4fd-103">Obtém o comprimento, em bytes, da origem inserida.</span><span class="sxs-lookup"><span data-stu-id="6d4fd-103">Gets the length, in bytes, of the embedded source.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6d4fd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6d4fd-104">Syntax</span></span>  
  
```  
HRESULT GetSourceLength(  
    [out, retval]  ULONG32*  pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6d4fd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6d4fd-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="6d4fd-106">[out] Um ponteiro para uma variável que indica o comprimento, em bytes, da fonte incorporada.</span><span class="sxs-lookup"><span data-stu-id="6d4fd-106">[out] A pointer to a variable that indicates the length, in bytes, of the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6d4fd-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6d4fd-107">Return Value</span></span>  
 <span data-ttu-id="6d4fd-108">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="6d4fd-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6d4fd-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6d4fd-109">See Also</span></span>  
 [<span data-ttu-id="6d4fd-110">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="6d4fd-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
