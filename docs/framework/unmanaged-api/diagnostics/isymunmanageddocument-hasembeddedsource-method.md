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
ms.openlocfilehash: 459a24e2ed9b97a67dc0266231fdfc32a9c853a6
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67776655"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="267ad-102">Método ISymUnmanagedDocument::HasEmbeddedSource</span><span class="sxs-lookup"><span data-stu-id="267ad-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="267ad-103">Retorna `true` se o documento tem o código-fonte inserido em símbolos de depuração; caso contrário, retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="267ad-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="267ad-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="267ad-104">Syntax</span></span>  
  
```cpp  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="267ad-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="267ad-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="267ad-106">[out] Um ponteiro para uma variável que indica se o documento tem incorporado os símbolos de depuração de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="267ad-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="267ad-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="267ad-107">Return Value</span></span>  
 <span data-ttu-id="267ad-108">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="267ad-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="267ad-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="267ad-109">See also</span></span>

- [<span data-ttu-id="267ad-110">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="267ad-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
