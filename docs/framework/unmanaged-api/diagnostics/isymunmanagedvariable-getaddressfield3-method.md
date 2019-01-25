---
title: Método ISymUnmanagedVariable::GetAddressField3
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField3
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField3
helpviewer_keywords:
- ISymUnmanagedVariable::GetAddressField3 method [.NET Framework debugging]
- GetAddressField3 method [.NET Framework debugging]
ms.assetid: 4d834721-ad8d-439d-b356-c6b4aef022fc
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5c2695fb6fcd0f4bba3576f2331c80961e9a444d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54649174"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="babd0-102">Método ISymUnmanagedVariable::GetAddressField3</span><span class="sxs-lookup"><span data-stu-id="babd0-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>
<span data-ttu-id="babd0-103">Obtém o terceiro campo de endereço para essa variável.</span><span class="sxs-lookup"><span data-stu-id="babd0-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="babd0-104">Seu significado depende do tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="babd0-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="babd0-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="babd0-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="babd0-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="babd0-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="babd0-107">[out] Um ponteiro para um `ULONG32` que recebe o terceiro campo de endereço.</span><span class="sxs-lookup"><span data-stu-id="babd0-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="babd0-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="babd0-108">Return Value</span></span>  
 <span data-ttu-id="babd0-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="babd0-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="babd0-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="babd0-110">Requirements</span></span>  
 <span data-ttu-id="babd0-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="babd0-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="babd0-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="babd0-112">See also</span></span>
- [<span data-ttu-id="babd0-113">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="babd0-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="babd0-114">Método GetAddressField1</span><span class="sxs-lookup"><span data-stu-id="babd0-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="babd0-115">Método GetAddressField2</span><span class="sxs-lookup"><span data-stu-id="babd0-115">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="babd0-116">Método GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="babd0-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
