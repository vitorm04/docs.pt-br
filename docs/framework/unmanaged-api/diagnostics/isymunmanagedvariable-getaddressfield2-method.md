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
ms.openlocfilehash: 6256d052780b1c610e61267be2517954d722a42d
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610594"
---
# <a name="isymunmanagedvariablegetaddressfield2-method"></a><span data-ttu-id="aedba-102">Método ISymUnmanagedVariable::GetAddressField2</span><span class="sxs-lookup"><span data-stu-id="aedba-102">ISymUnmanagedVariable::GetAddressField2 Method</span></span>
<span data-ttu-id="aedba-103">Obtém o segundo campo de endereço para essa variável.</span><span class="sxs-lookup"><span data-stu-id="aedba-103">Gets the second address field for this variable.</span></span> <span data-ttu-id="aedba-104">Seu significado depende do tipo de endereço.</span><span class="sxs-lookup"><span data-stu-id="aedba-104">Its meaning depends on the kind of address.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aedba-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="aedba-105">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressField2(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="aedba-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="aedba-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="aedba-107">fora Um ponteiro para um `ULONG32` que recebe o segundo campo de endereço.</span><span class="sxs-lookup"><span data-stu-id="aedba-107">[out] A pointer to a `ULONG32` that receives the second address field.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="aedba-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="aedba-108">Return Value</span></span>  
 <span data-ttu-id="aedba-109">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="aedba-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="aedba-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="aedba-110">Requirements</span></span>  
 <span data-ttu-id="aedba-111">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="aedba-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aedba-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="aedba-112">See also</span></span>

- [<span data-ttu-id="aedba-113">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="aedba-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
- [<span data-ttu-id="aedba-114">Método GetAddressField1</span><span class="sxs-lookup"><span data-stu-id="aedba-114">GetAddressField1 Method</span></span>](isymunmanagedvariable-getaddressfield1-method.md)
- [<span data-ttu-id="aedba-115">Método GetAddressField3</span><span class="sxs-lookup"><span data-stu-id="aedba-115">GetAddressField3 Method</span></span>](isymunmanagedvariable-getaddressfield3-method.md)
- [<span data-ttu-id="aedba-116">Método GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="aedba-116">GetAddressKind Method</span></span>](isymunmanagedvariable-getaddresskind-method.md)
