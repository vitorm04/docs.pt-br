---
title: Método ISymUnmanagedConstant::GetValue
ms.date: 03/30/2017
api_name:
- ISymUnmanagedConstant.GetValue
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedConstant::GetValue
helpviewer_keywords:
- GetValue method, ISymUnmanagedConstant interface [.NET Framework debugging]
- ISymUnmanagedConstant::GetValue method [.NET Framework debugging]
ms.assetid: 0036fc10-e768-47a8-b9cf-bf47faf8d194
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1043a7efe70798fbbc52ce6d1d0e16510e7c0503
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54499139"
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="a7055-102">Método ISymUnmanagedConstant::GetValue</span><span class="sxs-lookup"><span data-stu-id="a7055-102">ISymUnmanagedConstant::GetValue Method</span></span>
<span data-ttu-id="a7055-103">Obtém o valor da constante.</span><span class="sxs-lookup"><span data-stu-id="a7055-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a7055-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a7055-104">Syntax</span></span>  
  
```  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a7055-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a7055-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="a7055-106">[out] Um ponteiro para uma variável que recebe o valor.</span><span class="sxs-lookup"><span data-stu-id="a7055-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a7055-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a7055-107">Return Value</span></span>  
 <span data-ttu-id="a7055-108">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="a7055-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a7055-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a7055-109">Requirements</span></span>  
 <span data-ttu-id="a7055-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a7055-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a7055-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a7055-111">See also</span></span>
- [<span data-ttu-id="a7055-112">Interface ISymUnmanagedConstant</span><span class="sxs-lookup"><span data-stu-id="a7055-112">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)
- [<span data-ttu-id="a7055-113">Método GetName</span><span class="sxs-lookup"><span data-stu-id="a7055-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)
- [<span data-ttu-id="a7055-114">Método GetSignature</span><span class="sxs-lookup"><span data-stu-id="a7055-114">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
