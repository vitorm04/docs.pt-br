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
ms.openlocfilehash: 794615994cd11ee00c2a381b9ba883cebb8233a0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446119"
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="96344-102">Método ISymUnmanagedVariable::GetAddressField2</span><span class="sxs-lookup"><span data-stu-id="96344-102">ISymUnmanagedVariable::GetAddressField2 Method</span></span>
<span data-ttu-id="96344-103">Gets the second address field for this variable.</span><span class="sxs-lookup"><span data-stu-id="96344-103">Gets the second address field for this variable.</span></span> <span data-ttu-id="96344-104">Its meaning depends on the kind of address.</span><span class="sxs-lookup"><span data-stu-id="96344-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="96344-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="96344-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="96344-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="96344-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="96344-107">[out] A pointer to a `ULONG32` that receives the second address field.</span><span class="sxs-lookup"><span data-stu-id="96344-107">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="96344-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="96344-108">Return Value</span></span>  
 <span data-ttu-id="96344-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span><span class="sxs-lookup"><span data-stu-id="96344-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="96344-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="96344-110">Requirements</span></span>  
 <span data-ttu-id="96344-111">**Header:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="96344-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="96344-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="96344-112">See also</span></span>

- [<span data-ttu-id="96344-113">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="96344-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
- [<span data-ttu-id="96344-114">Método GetAddressField1</span><span class="sxs-lookup"><span data-stu-id="96344-114">GetAddressField1 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="96344-115">Método GetAddressField3</span><span class="sxs-lookup"><span data-stu-id="96344-115">GetAddressField3 Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="96344-116">Método GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="96344-116">GetAddressKind Method</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-getaddresskind-method.md)
