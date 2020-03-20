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
ms.openlocfilehash: 97f0d81c389ffd0bd8a69df2ca39322d726f98bc
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79176624"
---
# <a name="isymencunmanagedmethodgetdocumentsformethod-method"></a><span data-ttu-id="13eb6-102">Método ISymENCUnmanagedMethod::GetDocumentsForMethod</span><span class="sxs-lookup"><span data-stu-id="13eb6-102">ISymENCUnmanagedMethod::GetDocumentsForMethod Method</span></span>
<span data-ttu-id="13eb6-103">Obtém os documentos que este método tem linhas dentro</span><span class="sxs-lookup"><span data-stu-id="13eb6-103">Gets the documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="13eb6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="13eb6-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethod(  
    [in]  ULONG32  cDocs,  
    [out] ULONG32  *pcDocs,
    [in, size_is(cDocs)] ISymUnmanagedDocument* documents[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="13eb6-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="13eb6-105">Parameters</span></span>  
 `cDocs`  
 <span data-ttu-id="13eb6-106">[em] O comprimento do tampão `pcDocs`apontado por .</span><span class="sxs-lookup"><span data-stu-id="13eb6-106">[in] The length of the buffer pointed to by `pcDocs`.</span></span>  
  
 `pcDocs`  
 <span data-ttu-id="13eb6-107">[fora] Um ponteiro `ULONG32` para um que recebe o tamanho, em caracteres, do buffer necessário para conter os documentos.</span><span class="sxs-lookup"><span data-stu-id="13eb6-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the documents.</span></span>  
  
 `documents`  
 <span data-ttu-id="13eb6-108">[em] O buffer que contém os documentos.</span><span class="sxs-lookup"><span data-stu-id="13eb6-108">[in] The buffer that contains the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="13eb6-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="13eb6-109">Return Value</span></span>  
 <span data-ttu-id="13eb6-110">S_OK se o método for bem sucedido; caso contrário, um código de erro.</span><span class="sxs-lookup"><span data-stu-id="13eb6-110">S_OK if the method succeeds; otherwise, an error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="13eb6-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="13eb6-111">Requirements</span></span>  
 <span data-ttu-id="13eb6-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="13eb6-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="13eb6-113">Confira também</span><span class="sxs-lookup"><span data-stu-id="13eb6-113">See also</span></span>

- [<span data-ttu-id="13eb6-114">Interface ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="13eb6-114">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
