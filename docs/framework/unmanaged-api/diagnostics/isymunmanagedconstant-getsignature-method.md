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
ms.openlocfilehash: ce9ce768e32434e0a1acd2fad67a0cdc99f49e18
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33430140"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="b3289-102">Método ISymUnmanagedConstant::GetSignature</span><span class="sxs-lookup"><span data-stu-id="b3289-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="b3289-103">Obtém a assinatura da constante.</span><span class="sxs-lookup"><span data-stu-id="b3289-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b3289-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b3289-104">Syntax</span></span>  
  
```  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b3289-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b3289-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="b3289-106">[in] O comprimento do buffer que o `pcSig` parâmetro aponta para.</span><span class="sxs-lookup"><span data-stu-id="b3289-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="b3289-107">[out] Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter a assinatura.</span><span class="sxs-lookup"><span data-stu-id="b3289-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="b3289-108">[out] O buffer que armazena a assinatura.</span><span class="sxs-lookup"><span data-stu-id="b3289-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b3289-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b3289-109">Return Value</span></span>  
 <span data-ttu-id="b3289-110">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="b3289-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b3289-111">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b3289-111">Requirements</span></span>  
 <span data-ttu-id="b3289-112">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="b3289-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3289-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b3289-113">See Also</span></span>  
 [<span data-ttu-id="b3289-114">Interface ISymUnmanagedConstant</span><span class="sxs-lookup"><span data-stu-id="b3289-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [<span data-ttu-id="b3289-115">Método GetName</span><span class="sxs-lookup"><span data-stu-id="b3289-115">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)  
 [<span data-ttu-id="b3289-116">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="b3289-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
