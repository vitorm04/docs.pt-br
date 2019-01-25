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
ms.openlocfilehash: 86c64f7c56555619ead495e1e935e7bea86ac6ec
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54495442"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="52da0-102">Método ISymUnmanagedConstant::GetSignature</span><span class="sxs-lookup"><span data-stu-id="52da0-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="52da0-103">Obtém a assinatura da constante.</span><span class="sxs-lookup"><span data-stu-id="52da0-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="52da0-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="52da0-104">Syntax</span></span>  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="52da0-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="52da0-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="52da0-106">[in] O comprimento do buffer que o `pcSig` parâmetro aponta.</span><span class="sxs-lookup"><span data-stu-id="52da0-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="52da0-107">[out] Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter a assinatura.</span><span class="sxs-lookup"><span data-stu-id="52da0-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="52da0-108">[out] O buffer que armazena a assinatura.</span><span class="sxs-lookup"><span data-stu-id="52da0-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="52da0-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="52da0-109">Return Value</span></span>  
 <span data-ttu-id="52da0-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="52da0-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="52da0-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="52da0-111">Requirements</span></span>  
 <span data-ttu-id="52da0-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="52da0-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="52da0-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="52da0-113">See also</span></span>
- [<span data-ttu-id="52da0-114">Interface ISymUnmanagedConstant</span><span class="sxs-lookup"><span data-stu-id="52da0-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="52da0-115">Método GetName</span><span class="sxs-lookup"><span data-stu-id="52da0-115">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="52da0-116">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="52da0-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
