---
title: Método ISymENCUnmanagedMethod::GetDocumentsForMethod
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethod
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethod
helpviewer_keywords:
- GetDocumentsForMethod method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethod method [.NET Framework debugging]
ms.assetid: bd6ccde5-d578-48d8-abed-b474fbd48d13
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: db119a94cb7df29697836ffda240c29a86922d60
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59214764"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="c066e-102">Método ISymENCUnmanagedMethod::GetDocumentsForMethod</span><span class="sxs-lookup"><span data-stu-id="c066e-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="c066e-103">Obtém os documentos que esse método tem linhas em.</span><span class="sxs-lookup"><span data-stu-id="c066e-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c066e-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c066e-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,   
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c066e-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c066e-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="c066e-106">[in] O comprimento do buffer apontado por `pcDocs`.</span><span class="sxs-lookup"><span data-stu-id="c066e-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="c066e-107">[out] Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter os documentos.</span><span class="sxs-lookup"><span data-stu-id="c066e-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="c066e-108">[in] O buffer que contém os documentos.</span><span class="sxs-lookup"><span data-stu-id="c066e-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c066e-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c066e-109">Return Value</span></span>  
 <span data-ttu-id="c066e-110">S_OK se o método for bem-sucedido; Caso contrário, um código de erro.</span><span class="sxs-lookup"><span data-stu-id="c066e-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c066e-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c066e-111">Requirements</span></span>  
 <span data-ttu-id="c066e-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c066e-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c066e-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c066e-113">See also</span></span>

- [<span data-ttu-id="c066e-114">Interface ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="c066e-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
