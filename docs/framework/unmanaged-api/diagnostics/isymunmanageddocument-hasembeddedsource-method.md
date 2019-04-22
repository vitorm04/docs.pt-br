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
ms.openlocfilehash: 1d6c79be95ff80c8de9b07cb33be46a5f5db22b1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59094262"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="49cad-102">Método ISymUnmanagedDocument::HasEmbeddedSource</span><span class="sxs-lookup"><span data-stu-id="49cad-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="49cad-103">Retorna `true` se o documento tem o código-fonte inserido em símbolos de depuração; caso contrário, retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="49cad-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="49cad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="49cad-104">Syntax</span></span>  
  
```  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="49cad-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="49cad-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="49cad-106">[out] Um ponteiro para uma variável que indica se o documento tem incorporado os símbolos de depuração de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="49cad-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="49cad-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="49cad-107">Return Value</span></span>  
 <span data-ttu-id="49cad-108">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="49cad-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="49cad-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="49cad-109">See also</span></span>

- [<span data-ttu-id="49cad-110">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="49cad-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
