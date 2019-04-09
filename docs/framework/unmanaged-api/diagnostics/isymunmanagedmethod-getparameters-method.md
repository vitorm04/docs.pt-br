---
title: Método ISymUnmanagedMethod::GetParameters
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetParameters
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetParameters
helpviewer_keywords:
- ISymUnmanagedMethod::GetParameters method [.NET Framework debugging]
- GetParameters method [.NET Framework debugging]
ms.assetid: 3a8074f1-facc-4a3f-bb9b-d6574fc2fc74
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9a757e3b28a94c96e28a5bab736a6820a83617a3
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59101195"
---
# <a name="isymunmanagedmethodgetparameters-method"></a><span data-ttu-id="099b6-102">Método ISymUnmanagedMethod::GetParameters</span><span class="sxs-lookup"><span data-stu-id="099b6-102">ISymUnmanagedMethod::GetParameters Method</span></span>
<span data-ttu-id="099b6-103">Obtém os parâmetros para esse método.</span><span class="sxs-lookup"><span data-stu-id="099b6-103">Gets the parameters for this method.</span></span> <span data-ttu-id="099b6-104">Os parâmetros são retornados na ordem em que eles são definidos dentro da assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="099b6-104">The parameters are returned in the order in which they are defined within the method's signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="099b6-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="099b6-105">Syntax</span></span>  
  
```  
HRESULT GetParameters(  
    [in]  ULONG32  cParams,  
    [out] ULONG32  *pcParams,  
    [out, size_is(cParams),  
        length_is(*pcParams)] ISymUnmanagedVariable*  params[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="099b6-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="099b6-106">Parameters</span></span>  
 `cParams`  
 <span data-ttu-id="099b6-107">[in] O tamanho do `params` matriz.</span><span class="sxs-lookup"><span data-stu-id="099b6-107">[in] The size of the `params` array.</span></span>  
  
 `pcParams`  
 <span data-ttu-id="099b6-108">[in] Um ponteiro para um `ULONG32` que recebe o tamanho do buffer que é necessário para conter os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="099b6-108">[in] A pointer to a `ULONG32` that receives the size of the buffer that is required to contain the parameters.</span></span>  
  
 `params`  
 <span data-ttu-id="099b6-109">[out] Um ponteiro para o buffer que recebe os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="099b6-109">[out] A pointer to the buffer that receives the parameters.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="099b6-110">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="099b6-110">Return Value</span></span>  
 <span data-ttu-id="099b6-111">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="099b6-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="099b6-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="099b6-112">Requirements</span></span>  
 <span data-ttu-id="099b6-113">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="099b6-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="099b6-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="099b6-114">See also</span></span>

- [<span data-ttu-id="099b6-115">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="099b6-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
