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
ms.openlocfilehash: 0f28d6ec882afb21c3c204e141b1b6d883793004
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57499050"
---
# <a name="isymunmanagedvariablegetsignature-method"></a><span data-ttu-id="6618a-102">Método ISymUnmanagedVariable::GetSignature</span><span class="sxs-lookup"><span data-stu-id="6618a-102">ISymUnmanagedVariable::GetSignature Method</span></span>
<span data-ttu-id="6618a-103">Obtém a assinatura dessa variável.</span><span class="sxs-lookup"><span data-stu-id="6618a-103">Gets the signature of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6618a-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6618a-104">Syntax</span></span>  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6618a-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6618a-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="6618a-106">[in] O comprimento do buffer apontado pelo `sig` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="6618a-106">[in] The length of the buffer pointed to by the `sig` parameter.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="6618a-107">[out] Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter a assinatura.</span><span class="sxs-lookup"><span data-stu-id="6618a-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="6618a-108">[out] O buffer que armazena a assinatura.</span><span class="sxs-lookup"><span data-stu-id="6618a-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6618a-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6618a-109">Return Value</span></span>  
 <span data-ttu-id="6618a-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="6618a-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6618a-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6618a-111">Requirements</span></span>  
 <span data-ttu-id="6618a-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6618a-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6618a-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6618a-113">See also</span></span>
- [<span data-ttu-id="6618a-114">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="6618a-114">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
