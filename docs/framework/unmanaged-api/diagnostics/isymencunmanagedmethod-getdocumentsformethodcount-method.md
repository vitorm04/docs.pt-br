---
title: Método ISymENCUnmanagedMethod::GetDocumentsForMethodCount
ms.date: 03/30/2017
api_name:
- ISymENCUnmanagedMethod.GetDocumentsForMethodCount
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount
helpviewer_keywords:
- GetDocumentsForMethodCount method [.NET Framework debugging]
- ISymENCUnmanagedMethod::GetDocumentsForMethodCount method [.NET Framework debugging]
ms.assetid: cc1a823a-3ff3-4a33-b641-96edc93d2b17
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef1b8dce5c84382a9039787d2205f1ac8ccbc5bc
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59166459"
---
# <a name="isymencunmanagedmethodgetdocumentsformethodcount-method"></a><span data-ttu-id="fbc33-102">Método ISymENCUnmanagedMethod::GetDocumentsForMethodCount</span><span class="sxs-lookup"><span data-stu-id="fbc33-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Method</span></span>
<span data-ttu-id="fbc33-103">Obtém o número de documentos que esse método tem linhas em.</span><span class="sxs-lookup"><span data-stu-id="fbc33-103">Gets the number of documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fbc33-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="fbc33-104">Syntax</span></span>  
  
```  
HRESULT GetDocumentsForMethodCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="fbc33-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="fbc33-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="fbc33-106">[out] Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os documentos.</span><span class="sxs-lookup"><span data-stu-id="fbc33-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="fbc33-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="fbc33-107">Return Value</span></span>  
 <span data-ttu-id="fbc33-108">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="fbc33-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="fbc33-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="fbc33-109">Requirements</span></span>  
 <span data-ttu-id="fbc33-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="fbc33-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fbc33-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="fbc33-111">See also</span></span>

- [<span data-ttu-id="fbc33-112">Interface ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="fbc33-112">ISymENCUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymencunmanagedmethod-interface.md)
