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
ms.openlocfilehash: dd474c7f149b8eff542b674c2ba6527b6a0cbcb7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33426992"
---
# <a name="isymunmanagedvariablegetaddressfield3-method"></a><span data-ttu-id="a8072-102">Método ISymUnmanagedVariable::GetAddressField3</span><span class="sxs-lookup"><span data-stu-id="a8072-102">ISymUnmanagedVariable::GetAddressField3 Method</span></span>
<span data-ttu-id="a8072-103">Obtém o terceiro campo de endereço para essa variável.</span><span class="sxs-lookup"><span data-stu-id="a8072-103">Gets the third address field for this variable.</span></span> <span data-ttu-id="a8072-104">Seu significado depende do tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="a8072-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a8072-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a8072-105">Syntax</span></span>  
  
```  
HRESULT GetAddressField3(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="a8072-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a8072-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="a8072-107">[out] Um ponteiro para um `ULONG32` que recebe o terceiro campo de endereço.</span><span class="sxs-lookup"><span data-stu-id="a8072-107">[out] A pointer to a `ULONG32` that receives the third address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a8072-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="a8072-108">Return Value</span></span>  
 <span data-ttu-id="a8072-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="a8072-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a8072-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a8072-110">Requirements</span></span>  
 <span data-ttu-id="a8072-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="a8072-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a8072-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a8072-112">See Also</span></span>  
 [<span data-ttu-id="a8072-113">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="a8072-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)  
 [<span data-ttu-id="a8072-114">Método GetAddressField1</span><span class="sxs-lookup"><span data-stu-id="a8072-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)  
 [<span data-ttu-id="a8072-115">Método GetAddressField2</span><span class="sxs-lookup"><span data-stu-id="a8072-115">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)  
 [<span data-ttu-id="a8072-116">Método GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="a8072-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
