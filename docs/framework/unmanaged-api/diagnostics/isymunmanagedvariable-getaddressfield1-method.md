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
ms.openlocfilehash: 8a035e8dd7bd880c4ead500eede5e1b095d701f2
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67778064"
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="0942f-102">Método ISymUnmanagedVariable::GetAddressField1</span><span class="sxs-lookup"><span data-stu-id="0942f-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>
<span data-ttu-id="0942f-103">Obtém o primeiro campo de endereço para essa variável.</span><span class="sxs-lookup"><span data-stu-id="0942f-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="0942f-104">Seu significado depende do tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="0942f-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0942f-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="0942f-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="0942f-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="0942f-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="0942f-107">[out] Um ponteiro para um `ULONG32` que recebe o primeiro campo de endereço.</span><span class="sxs-lookup"><span data-stu-id="0942f-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="0942f-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="0942f-108">Return Value</span></span>  
 <span data-ttu-id="0942f-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="0942f-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0942f-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="0942f-110">Requirements</span></span>  
 <span data-ttu-id="0942f-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="0942f-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="0942f-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="0942f-112">See also</span></span>

- [<span data-ttu-id="0942f-113">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="0942f-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="0942f-114">Método GetAddressField2</span><span class="sxs-lookup"><span data-stu-id="0942f-114">GetAddressField2 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="0942f-115">Método GetAddressField3</span><span class="sxs-lookup"><span data-stu-id="0942f-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="0942f-116">Método GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="0942f-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
