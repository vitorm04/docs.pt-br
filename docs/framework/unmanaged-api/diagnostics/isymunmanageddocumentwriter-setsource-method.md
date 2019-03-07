---
title: Método ISymUnmanagedDocumentWriter::SetSource
ms.date: 03/30/2017
api_name:
- ISymUnmanagedDocumentWriter.SetSource
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedDocumentWriter::SetSource
helpviewer_keywords:
- ISymUnmanagedDocumentWriter::SetSource method [.NET Framework debugging]
- SetSource method [.NET Framework debugging]
ms.assetid: ea5b9d9f-ff06-4bd3-8de5-6435343aba59
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bcdda6f8cdd0fc0b333b81d58a8bff7c21aa1fef
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57486401"
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="08fa1-102">Método ISymUnmanagedDocumentWriter::SetSource</span><span class="sxs-lookup"><span data-stu-id="08fa1-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>
<span data-ttu-id="08fa1-103">Conjuntos de inserido o código-fonte para um documento que está sendo gravado.</span><span class="sxs-lookup"><span data-stu-id="08fa1-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="08fa1-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="08fa1-104">Syntax</span></span>  
  
```  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="08fa1-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="08fa1-105">Parameters</span></span>  
 `sourceSize`  
 <span data-ttu-id="08fa1-106">[in] Um `ULONG32` que contém o tamanho do `source` buffer.</span><span class="sxs-lookup"><span data-stu-id="08fa1-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="08fa1-107">[in] O buffer que armazena a origem inserida.</span><span class="sxs-lookup"><span data-stu-id="08fa1-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="08fa1-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="08fa1-108">Return Value</span></span>  
 <span data-ttu-id="08fa1-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="08fa1-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="08fa1-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="08fa1-110">Requirements</span></span>  
 <span data-ttu-id="08fa1-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="08fa1-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="08fa1-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="08fa1-112">See also</span></span>
- [<span data-ttu-id="08fa1-113">Interface ISymUnmanagedDocumentWriter</span><span class="sxs-lookup"><span data-stu-id="08fa1-113">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
