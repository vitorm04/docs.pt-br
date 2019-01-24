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
ms.openlocfilehash: cd294037774721839b0c4f1f09bdc2a6e3b87841
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54562668"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="c6598-102">Método ISymENCUnmanagedMethod::GetDocumentsForMethod</span><span class="sxs-lookup"><span data-stu-id="c6598-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="c6598-103">Obtém os documentos que esse método tem linhas em.</span><span class="sxs-lookup"><span data-stu-id="c6598-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c6598-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c6598-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,   
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="c6598-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c6598-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="c6598-106">[in] O comprimento do buffer apontado por `pcDocs`.</span><span class="sxs-lookup"><span data-stu-id="c6598-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="c6598-107">[out] Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter os documentos.</span><span class="sxs-lookup"><span data-stu-id="c6598-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="c6598-108">[in] O buffer que contém os documentos.</span><span class="sxs-lookup"><span data-stu-id="c6598-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c6598-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="c6598-109">Return Value</span></span>  
 <span data-ttu-id="c6598-110">S_OK se o método for bem-sucedido; Caso contrário, um código de erro.</span><span class="sxs-lookup"><span data-stu-id="c6598-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c6598-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="c6598-111">Requirements</span></span>  
 <span data-ttu-id="c6598-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="c6598-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c6598-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c6598-113">See also</span></span>
- [<span data-ttu-id="c6598-114">Interface ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="c6598-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
