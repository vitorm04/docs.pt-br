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
ms.openlocfilehash: 533d8a5481fe9ba7e7e65775229156a9cc3cf4d7
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449114"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="344f2-102">Método ISymUnmanagedDocument::HasEmbeddedSource</span><span class="sxs-lookup"><span data-stu-id="344f2-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="344f2-103">Retorna `true` se o documento tem origem inserida nos símbolos de depuração; caso contrário, retorna `false`.</span><span class="sxs-lookup"><span data-stu-id="344f2-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="344f2-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="344f2-104">Syntax</span></span>  
  
```cpp  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="344f2-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="344f2-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="344f2-106">fora Um ponteiro para uma variável que indica se o documento tem origem inserida nos símbolos de depuração.</span><span class="sxs-lookup"><span data-stu-id="344f2-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="344f2-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="344f2-107">Return Value</span></span>  
 <span data-ttu-id="344f2-108">S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="344f2-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="344f2-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="344f2-109">See also</span></span>

- [<span data-ttu-id="344f2-110">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="344f2-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
