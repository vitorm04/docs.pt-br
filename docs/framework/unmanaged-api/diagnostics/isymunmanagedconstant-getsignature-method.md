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
ms.openlocfilehash: 401dfbea0da309db24f3052f462daa66e8bbef4a
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74449273"
---
# <a name="isymunmanagedconstantgetsignature-method"></a><span data-ttu-id="c755b-102">Método ISymUnmanagedConstant::GetSignature</span><span class="sxs-lookup"><span data-stu-id="c755b-102">ISymUnmanagedConstant::GetSignature Method</span></span>
<span data-ttu-id="c755b-103">Obtém a assinatura da constante.</span><span class="sxs-lookup"><span data-stu-id="c755b-103">Gets the signature of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c755b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="c755b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetSignature(  
    [in]  ULONG32  cSig,  
    [out] ULONG32  *pcSig,  
    [out, size_is(cSig),  
        length_is(*pcSig)] BYTE sig[]);  
```  
  
## <a name="parameters"></a><span data-ttu-id="c755b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="c755b-105">Parameters</span></span>  
 `cSig`  
 <span data-ttu-id="c755b-106">no O comprimento do buffer ao qual o parâmetro `pcSig` aponta.</span><span class="sxs-lookup"><span data-stu-id="c755b-106">[in] The length of the buffer that the `pcSig` parameter points to.</span></span>  
  
 `pcSig`  
 <span data-ttu-id="c755b-107">fora Um ponteiro para um `ULONG32` que recebe o tamanho, em caracteres, do buffer necessário para conter a assinatura.</span><span class="sxs-lookup"><span data-stu-id="c755b-107">[out] A pointer to a `ULONG32` that receives the size, in characters, of the buffer required to contain the signature.</span></span>  
  
 `sig`  
 <span data-ttu-id="c755b-108">fora O buffer que armazena a assinatura.</span><span class="sxs-lookup"><span data-stu-id="c755b-108">[out] The buffer that stores the signature.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="c755b-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="c755b-109">Return Value</span></span>  
 <span data-ttu-id="c755b-110">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="c755b-110">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="c755b-111">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="c755b-111">Requirements</span></span>  
 <span data-ttu-id="c755b-112">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="c755b-112">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c755b-113">Consulte também</span><span class="sxs-lookup"><span data-stu-id="c755b-113">See also</span></span>

- [<span data-ttu-id="c755b-114">Interface ISymUnmanagedConstant</span><span class="sxs-lookup"><span data-stu-id="c755b-114">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="c755b-115">Método GetName</span><span class="sxs-lookup"><span data-stu-id="c755b-115">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="c755b-116">Método GetValue</span><span class="sxs-lookup"><span data-stu-id="c755b-116">GetValue Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getvalue-method.md)
