---
title: Método ISymUnmanagedDocument::HasEmbeddedSource
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocument.HasEmbeddedSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocument::HasEmbeddedSource
helpviewer_keywords:
- HasEmbeddedSource method [.NET Framework debugging]
- ISymUnmanagedDocument::HasEmbeddedSource method [.NET Framework debugging]
ms.assetid: 385fc4d3-365c-4645-b7b0-6c4c5344b79f
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 350aecb9f9c99c9aa44ae6df6d31c7cb69ae5760
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430339"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="90112-102">Método ISymUnmanagedDocument::HasEmbeddedSource</span><span class="sxs-lookup"><span data-stu-id="90112-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="90112-103">Retorna `true` se o documento tem origem inserida nos símbolos de depuração; caso contrário, retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="90112-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90112-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90112-104">Syntax</span></span>  
  
```  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="90112-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="90112-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="90112-106">[out] Um ponteiro para uma variável que indica se o documento tem origem inserida nos símbolos de depuração.</span><span class="sxs-lookup"><span data-stu-id="90112-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90112-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="90112-107">Return Value</span></span>  
 <span data-ttu-id="90112-108">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="90112-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90112-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90112-109">See Also</span></span>  
 [<span data-ttu-id="90112-110">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="90112-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
