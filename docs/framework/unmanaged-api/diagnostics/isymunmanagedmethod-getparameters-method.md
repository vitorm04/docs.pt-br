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
ms.openlocfilehash: 9e8139a822c877e70731e18ae5a75b83e6b7578e
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74448962"
---
# <a name="isymunmanagedmethodgetparameters-method"></a><span data-ttu-id="17acf-102">Método ISymUnmanagedMethod::GetParameters</span><span class="sxs-lookup"><span data-stu-id="17acf-102">ISymUnmanagedMethod::GetParameters Method</span></span>
<span data-ttu-id="17acf-103">Obtém os parâmetros para este método.</span><span class="sxs-lookup"><span data-stu-id="17acf-103">Gets the parameters for this method.</span></span> <span data-ttu-id="17acf-104">Os parâmetros são retornados na ordem em que são definidos dentro da assinatura do método.</span><span class="sxs-lookup"><span data-stu-id="17acf-104">The parameters are returned in the order in which they are defined within the method's signature.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="17acf-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="17acf-105">Syntax</span></span>  
  
```cpp  
HRESULT GetParameters(  
    [in]  ULONG32  cParams,  
    [out] ULONG32  *pcParams,  
    [out, size_is(cParams),  
        length_is(*pcParams)] ISymUnmanagedVariable*  params[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="17acf-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="17acf-106">Parameters</span></span>  
 `cParams`  
 <span data-ttu-id="17acf-107">no O tamanho da matriz de `params`.</span><span class="sxs-lookup"><span data-stu-id="17acf-107">[in] The size of the `params` array.</span></span>  
  
 `pcParams`  
 <span data-ttu-id="17acf-108">no Um ponteiro para um `ULONG32` que recebe o tamanho do buffer necessário para conter os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="17acf-108">[in] A pointer to a `ULONG32` that receives the size of the buffer that is required to contain the parameters.</span></span>  
  
 `params`  
 <span data-ttu-id="17acf-109">fora Um ponteiro para o buffer que recebe os parâmetros.</span><span class="sxs-lookup"><span data-stu-id="17acf-109">[out] A pointer to the buffer that receives the parameters.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="17acf-110">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="17acf-110">Return Value</span></span>  
 <span data-ttu-id="17acf-111">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="17acf-111">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="17acf-112">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="17acf-112">Requirements</span></span>  
 <span data-ttu-id="17acf-113">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="17acf-113">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17acf-114">Consulte também</span><span class="sxs-lookup"><span data-stu-id="17acf-114">See also</span></span>

- [<span data-ttu-id="17acf-115">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="17acf-115">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
