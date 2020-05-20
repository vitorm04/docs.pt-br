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
ms.openlocfilehash: 031e9d9434bc655ba8947a2bb6aba56a150e9002
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614455"
---
# <a name="isymunmanagedmethodgetparameters-method"></a><span data-ttu-id="6440e-102">Método ISymUnmanagedMethod::GetParameters</span><span class="sxs-lookup"><span data-stu-id="6440e-102">ISymUnmanagedMethod::GetParameters Method</span></span>
<span data-ttu-id="6440e-103">Obtém os parâmetros para este método.</span><span class="sxs-lookup"><span data-stu-id="6440e-103">Gets the parameters for this method.</span></span> <span data-ttu-id="6440e-104">Os parâmetros são retornados na ordem em que são definidos dentro da assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="6440e-104">The parameters are returned in the order in which they are defined within the method's signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6440e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6440e-105">Syntax</span></span>  
  
```cpp  
HRESULT GetParameters(  
    [in]  ULONG32  cParams,  
    [out] ULONG32  *pcParams,  
    [out, size_is(cParams),  
        length_is(*pcParams)] ISymUnmanagedVariable*  params[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="6440e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6440e-106">Parameters</span></span>  
 `cParams`  
 <span data-ttu-id="6440e-107">no O tamanho da `params` matriz.</span><span class="sxs-lookup"><span data-stu-id="6440e-107">[in] The size of the `params` array.</span></span>  
  
 `pcParams`  
 <span data-ttu-id="6440e-108">no Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="6440e-108">[in] A pointer to a `ULONG32` that receives the size of the buffer that is required to contain the parameters.</span></span>  
  
 `params`  
 <span data-ttu-id="6440e-109">fora Um ponteiro para o buffer que recebe os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="6440e-109">[out] A pointer to the buffer that receives the parameters.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6440e-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="6440e-110">Return Value</span></span>  
 <span data-ttu-id="6440e-111">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="6440e-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6440e-112">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6440e-112">Requirements</span></span>  
 <span data-ttu-id="6440e-113">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="6440e-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6440e-114">Veja também</span><span class="sxs-lookup"><span data-stu-id="6440e-114">See also</span></span>

- [<span data-ttu-id="6440e-115">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="6440e-115">ISymUnmanagedMethod Interface</span></span>](isymunmanagedmethod-interface.md)
