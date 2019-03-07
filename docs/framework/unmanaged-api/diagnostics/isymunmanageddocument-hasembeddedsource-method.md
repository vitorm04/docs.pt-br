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
ms.openlocfilehash: 620d303bcd33a4d04155850ec2c1b6293bf788d1
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57493252"
---
# <a name="isymunmanageddocumenthasembeddedsource-method"></a><span data-ttu-id="14cba-102">Método ISymUnmanagedDocument::HasEmbeddedSource</span><span class="sxs-lookup"><span data-stu-id="14cba-102">ISymUnmanagedDocument::HasEmbeddedSource Method</span></span>
<span data-ttu-id="14cba-103">Retorna `true` se o documento tem o código-fonte inserido em símbolos de depuração; caso contrário, retornará `false`.</span><span class="sxs-lookup"><span data-stu-id="14cba-103">Returns `true` if the document has source embedded in the debugging symbols; otherwise, returns `false`.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="14cba-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="14cba-104">Syntax</span></span>  
  
```  
HRESULT HasEmbeddedSource(  
   [out, retval]  BOOL  *pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="14cba-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="14cba-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="14cba-106">[out] Um ponteiro para uma variável que indica se o documento tem incorporado os símbolos de depuração de código-fonte.</span><span class="sxs-lookup"><span data-stu-id="14cba-106">[out] A pointer to a variable that indicates whether the document has source embedded in the debugging symbols.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="14cba-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="14cba-107">Return Value</span></span>  
 <span data-ttu-id="14cba-108">S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="14cba-108">S_OK if the method succeeds.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="14cba-109">Consulte também</span><span class="sxs-lookup"><span data-stu-id="14cba-109">See also</span></span>
- [<span data-ttu-id="14cba-110">Interface ISymUnmanagedDocument</span><span class="sxs-lookup"><span data-stu-id="14cba-110">ISymUnmanagedDocument Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocument-interface.md)
