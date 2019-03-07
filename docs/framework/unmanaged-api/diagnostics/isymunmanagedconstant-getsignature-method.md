---
title: Método ISymUnmanagedConstant::GetSignature
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetSignature
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetSignature
helpviewer_keywords:
- GetSignature method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetSignature method [.NET Framework debugging]
ms.assetid: 3eb41151-a228-43e3-ba8f-e6dd3ceb8542
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: eb893f06a5e905b981a408887f1c6bf5718ea79a
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/06/2019
ms.locfileid: "57498556"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="554f7-102">Método ISymUnmanagedConstant::GetSignature</span><span class="sxs-lookup"><span data-stu-id="554f7-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="554f7-103">Obtém a assinatura da constante.</span><span class="sxs-lookup"><span data-stu-id="554f7-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="554f7-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="554f7-104">Syntax</span></span>  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="554f7-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="554f7-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="554f7-106">[in] O comprimento do buffer que o `pcSig` parâmetro aponta.</span><span class="sxs-lookup"><span data-stu-id="554f7-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="554f7-107">[out] Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter a assinatura.</span><span class="sxs-lookup"><span data-stu-id="554f7-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="554f7-108">[out] O buffer que armazena a assinatura.</span><span class="sxs-lookup"><span data-stu-id="554f7-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="554f7-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="554f7-109">Return Value</span></span>  
 <span data-ttu-id="554f7-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="554f7-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="554f7-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="554f7-111">Requirements</span></span>  
 <span data-ttu-id="554f7-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="554f7-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="554f7-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="554f7-113">See also</span></span>
- [<span data-ttu-id="554f7-114">Interface ISymUnmanagedConstant</span><span class="sxs-lookup"><span data-stu-id="554f7-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="554f7-115">Método GetName</span><span class="sxs-lookup"><span data-stu-id="554f7-115">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="554f7-116">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="554f7-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
