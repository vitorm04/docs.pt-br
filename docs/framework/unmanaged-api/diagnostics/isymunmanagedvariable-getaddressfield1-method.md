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
ms.openlocfilehash: 253fd17178c03bc0c4d8ea031888a404ad56f876
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83615274"
---
# <a name="isymunmanagedvariablegetaddressfield1-method"></a><span data-ttu-id="57488-102">Método ISymUnmanagedVariable::GetAddressField1</span><span class="sxs-lookup"><span data-stu-id="57488-102">ISymUnmanagedVariable::GetAddressField1 Method</span></span>
<span data-ttu-id="57488-103">Obtém o primeiro campo de endereço para essa variável.</span><span class="sxs-lookup"><span data-stu-id="57488-103">Gets the first address field for this variable.</span></span> <span data-ttu-id="57488-104">Seu significado depende do tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="57488-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="57488-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="57488-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField1(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="57488-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="57488-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="57488-107">fora Um ponteiro para um `ULONG32` que recebe o primeiro campo de endereço.</span><span class="sxs-lookup"><span data-stu-id="57488-107">[out] A pointer to a `ULONG32` that receives the first address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="57488-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="57488-108">Return Value</span></span>  
 <span data-ttu-id="57488-109">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="57488-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="57488-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="57488-110">Requirements</span></span>  
 <span data-ttu-id="57488-111">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="57488-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="57488-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="57488-112">See also</span></span>

- [<span data-ttu-id="57488-113">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="57488-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="57488-114">Método GetAddressField2</span><span class="sxs-lookup"><span data-stu-id="57488-114">GetAddressField2 Method</span></span>](isymunmanagedvariable-getaddressfield2-method.md)
- [<span data-ttu-id="57488-115">Método GetAddressField3</span><span class="sxs-lookup"><span data-stu-id="57488-115">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="57488-116">Método GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="57488-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
