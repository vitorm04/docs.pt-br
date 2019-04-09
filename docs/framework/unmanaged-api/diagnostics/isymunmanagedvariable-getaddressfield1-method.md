---
title: Método ISymUnmanagedVariable::GetAddressField1
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField1
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField1
helpviewer_keywords:
- GetAddressField1 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField1 method [.NET Framework debugging]
ms.assetid: 25788ed1-0ce3-4b97-96fc-88f8997812a3
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 67634024b04e82aa3a3c0b96dc260114c4c16371
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59179693"
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="29781-102">Método ISymUnmanagedVariable::GetAddressField1</span><span class="sxs-lookup"><span data-stu-id="29781-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>
<span data-ttu-id="29781-103">Obtém o primeiro campo de endereço para essa variável.</span><span class="sxs-lookup"><span data-stu-id="29781-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="29781-104">Seu significado depende do tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="29781-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29781-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="29781-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="29781-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="29781-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="29781-107">[out] Um ponteiro para um `ULONG32` que recebe o primeiro campo de endereço.</span><span class="sxs-lookup"><span data-stu-id="29781-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="29781-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="29781-108">Return Value</span></span>  
 <span data-ttu-id="29781-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="29781-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="29781-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="29781-110">Requirements</span></span>  
 <span data-ttu-id="29781-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="29781-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="29781-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="29781-112">See also</span></span>

- [<span data-ttu-id="29781-113">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="29781-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="29781-114">Método GetAddressField2</span><span class="sxs-lookup"><span data-stu-id="29781-114">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="29781-115">Método GetAddressField3</span><span class="sxs-lookup"><span data-stu-id="29781-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="29781-116">Método GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="29781-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
