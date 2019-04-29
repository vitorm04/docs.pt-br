---
title: Método ISymUnmanagedVariable::GetSignature
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedVariable interface [.NET Framework debugging]
- ISymUnmanagedVariable::GetSignature method [.NET Framework debugging]
ms.assetid: 78c1ba28-a410-4360-805c-23a95408964a
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 3cc616246812bb9643388d8ad57cf84bc387b55e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61797495"
---
# <a name="isymunmanagedvariablegetsignature-method"></a><span data-ttu-id="074fa-102">Método ISymUnmanagedVariable::GetSignature</span><span class="sxs-lookup"><span data-stu-id="074fa-102">ISymUnmanagedVariable::GetSignature Method</span></span>
<span data-ttu-id="074fa-103">Obtém a assinatura dessa variável.</span><span class="sxs-lookup"><span data-stu-id="074fa-103">Gets the signature of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="074fa-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="074fa-104">Syntax</span></span>  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="074fa-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="074fa-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="074fa-106">[in] O comprimento do buffer apontado pelo `sig` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="074fa-106">[in] The length of the buffer pointed to by the `sig` parameter.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="074fa-107">[out] Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter a assinatura.</span><span class="sxs-lookup"><span data-stu-id="074fa-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="074fa-108">[out] O buffer que armazena a assinatura.</span><span class="sxs-lookup"><span data-stu-id="074fa-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="074fa-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="074fa-109">Return Value</span></span>  
 <span data-ttu-id="074fa-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="074fa-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="074fa-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="074fa-111">Requirements</span></span>  
 <span data-ttu-id="074fa-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="074fa-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="074fa-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="074fa-113">See also</span></span>

- [<span data-ttu-id="074fa-114">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="074fa-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
