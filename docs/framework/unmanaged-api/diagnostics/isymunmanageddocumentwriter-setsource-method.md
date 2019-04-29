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
ms.openlocfilehash: 64982308c6eb7e9df4b94b4e123857c65939f044
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61939744"
---
# <a name="isymunmanageddocumentwritersetsource-method"></a><span data-ttu-id="0f5a6-102">Método ISymUnmanagedDocumentWriter::SetSource</span><span class="sxs-lookup"><span data-stu-id="0f5a6-102">ISymUnmanagedDocumentWriter::SetSource Method</span></span>
<span data-ttu-id="0f5a6-103">Conjuntos de inserido o código-fonte para um documento que está sendo gravado.</span><span class="sxs-lookup"><span data-stu-id="0f5a6-103">Sets embedded source for a document that is being written.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0f5a6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0f5a6-104">Syntax</span></span>  
  
```  
HRESULT SetSource(  
    [in]  ULONG32  sourceSize,  
    [in, size_is(sourceSize)] BYTE  source[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0f5a6-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0f5a6-105">Parameters</span></span>  
 `sourceSize`  
 <span data-ttu-id="0f5a6-106">[in] Um `ULONG32` que contém o tamanho do `source` buffer.</span><span class="sxs-lookup"><span data-stu-id="0f5a6-106">[in] A `ULONG32` that contains the size of the `source` buffer.</span></span>  
  
 `source`  
 <span data-ttu-id="0f5a6-107">[in] O buffer que armazena a origem inserida.</span><span class="sxs-lookup"><span data-stu-id="0f5a6-107">[in] The buffer that stores the embedded source.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0f5a6-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0f5a6-108">Return Value</span></span>  
 <span data-ttu-id="0f5a6-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="0f5a6-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0f5a6-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0f5a6-110">Requirements</span></span>  
 <span data-ttu-id="0f5a6-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0f5a6-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0f5a6-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0f5a6-112">See also</span></span>

- [<span data-ttu-id="0f5a6-113">Interface ISymUnmanagedDocumentWriter</span><span class="sxs-lookup"><span data-stu-id="0f5a6-113">ISymUnmanagedDocumentWriter Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanageddocumentwriter-interface.md)
