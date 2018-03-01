---
title: "Método ISymUnmanagedConstant::GetValue"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 15ae3e9f2e680c7e85d3b8daa0d6010773797258
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedconstantgetvalue-method"></a><span data-ttu-id="a885d-102">Método ISymUnmanagedConstant::GetValue</span><span class="sxs-lookup"><span data-stu-id="a885d-102">ISymUnmanagedConstant::GetValue Method</span></span>
<span data-ttu-id="a885d-103">Obtém o valor da constante.</span><span class="sxs-lookup"><span data-stu-id="a885d-103">Gets the value of the constant.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a885d-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a885d-104">Syntax</span></span>  
  
```  
HRESULT GetValue(  
    [out]  VARIANT* pValue  
);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a885d-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a885d-105">Parameters</span></span>  
 `pValue`  
 <span data-ttu-id="a885d-106">[out] Um ponteiro para uma variável que recebe o valor.</span><span class="sxs-lookup"><span data-stu-id="a885d-106">[out] A pointer to a variable that receives the value.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a885d-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a885d-107">Return Value</span></span>  
 <span data-ttu-id="a885d-108">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="a885d-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a885d-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a885d-109">Requirements</span></span>  
 <span data-ttu-id="a885d-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a885d-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a885d-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a885d-111">See Also</span></span>  
 [<span data-ttu-id="a885d-112">Interface ISymUnmanagedConstant</span><span class="sxs-lookup"><span data-stu-id="a885d-112">ISymUnmanagedConstant Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-interface.md)  
 [<span data-ttu-id="a885d-113">Método GetName</span><span class="sxs-lookup"><span data-stu-id="a885d-113">GetName Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getname-method.md)  
 [<span data-ttu-id="a885d-114">Método GetSignature</span><span class="sxs-lookup"><span data-stu-id="a885d-114">GetSignature Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedconstant-getsignature-method.md)
