---
title: Método ISymUnmanagedVariable::GetAddressField2
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressField2
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressField2
helpviewer_keywords:
- GetAddressField2 method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressField2 method [.NET Framework debugging]
ms.assetid: 1f25b294-72b6-4882-a49b-6c9d364b6008
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fe360a50038f49fdea1528c8c520dc893b258057
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33427080"
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="a8051-102">Método ISymUnmanagedVariable::GetAddressField2</span><span class="sxs-lookup"><span data-stu-id="a8051-102">ISymUnmanagedVariable::GetAddressField2 Method</span></span>
<span data-ttu-id="a8051-103">Obtém o segundo campo de endereço para essa variável.</span><span class="sxs-lookup"><span data-stu-id="a8051-103">Gets the second address field for this variable.</span></span> <span data-ttu-id="a8051-104">Seu significado depende do tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="a8051-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8051-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8051-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a8051-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a8051-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a8051-107">[out] Um ponteiro para um `ULONG32` que recebe o segundo campo de endereço.</span><span class="sxs-lookup"><span data-stu-id="a8051-107">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8051-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a8051-108">Return Value</span></span>  
 <span data-ttu-id="a8051-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="a8051-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8051-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a8051-110">Requirements</span></span>  
 <span data-ttu-id="a8051-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a8051-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8051-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8051-112">See Also</span></span>  
 [<span data-ttu-id="a8051-113">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="a8051-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="a8051-114">Método GetAddressField1</span><span class="sxs-lookup"><span data-stu-id="a8051-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)  
 [<span data-ttu-id="a8051-115">Método GetAddressField3</span><span class="sxs-lookup"><span data-stu-id="a8051-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)  
 [<span data-ttu-id="a8051-116">Método GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="a8051-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
