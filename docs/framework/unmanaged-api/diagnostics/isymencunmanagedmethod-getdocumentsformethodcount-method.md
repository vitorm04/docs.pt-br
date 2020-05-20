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
ms.openlocfilehash: d096101189d52401c407a4108c9c81e201d3f30d
ms.sourcegitcommit: 7b1497c1927cb449cefd313bc5126ae37df30746
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/16/2020
ms.locfileid: "83441936"
---
# <a name="isymencunmanagedmethodgetdocumentsformethodcount-method"></a><span data-ttu-id="2cf62-102">Método ISymENCUnmanagedMethod::GetDocumentsForMethodCount</span><span class="sxs-lookup"><span data-stu-id="2cf62-102">ISymENCUnmanagedMethod::GetDocumentsForMethodCount Method</span></span>
<span data-ttu-id="2cf62-103">Obtém o número de documentos em que esse método tem linhas.</span><span class="sxs-lookup"><span data-stu-id="2cf62-103">Gets the number of documents that this method has lines in.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cf62-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="2cf62-104">Syntax</span></span>  
  
```cpp  
HRESULT GetDocumentsForMethodCount(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="2cf62-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="2cf62-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="2cf62-106">fora Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os documentos.</span><span class="sxs-lookup"><span data-stu-id="2cf62-106">[out] A pointer to a `ULONG32` that receives the size of the buffer required to contain the documents.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="2cf62-107">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="2cf62-107">Return Value</span></span>  
 <span data-ttu-id="2cf62-108">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="2cf62-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="2cf62-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="2cf62-109">Requirements</span></span>  
 <span data-ttu-id="2cf62-110">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="2cf62-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2cf62-111">Confira também</span><span class="sxs-lookup"><span data-stu-id="2cf62-111">See also</span></span>

- [<span data-ttu-id="2cf62-112">Interface ISymENCUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="2cf62-112">ISymENCUnmanagedMethod Interface</span></span>](isymencunmanagedmethod-interface.md)
