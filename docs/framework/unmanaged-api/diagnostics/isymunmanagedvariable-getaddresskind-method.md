---
title: Método ISymUnmanagedVariable::GetAddressKind
ms.date: 03/30/2017
api_name:
- ISymUnmanagedVariable.GetAddressKind
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedVariable::GetAddressKind
helpviewer_keywords:
- GetAddressKind method [.NET Framework debugging]
- ISymUnmanagedVariable::GetAddressKind method [.NET Framework debugging]
ms.assetid: a71563c0-62f2-4eb4-970c-825d61827613
topic_type:
- apiref
ms.openlocfilehash: 093c5e3e64395c8946acd9201990d132e8111fc7
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/19/2020
ms.locfileid: "83610581"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="66c8b-102">Método ISymUnmanagedVariable::GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="66c8b-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="66c8b-103">Obtém o tipo de endereço dessa variável.</span><span class="sxs-lookup"><span data-stu-id="66c8b-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66c8b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="66c8b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="66c8b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="66c8b-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="66c8b-106">fora Um ponteiro para um `ULONG32` que recebe o valor.</span><span class="sxs-lookup"><span data-stu-id="66c8b-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="66c8b-107">Os valores possíveis são definidos na enumeração [CorSymAddrKind](corsymaddrkind-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="66c8b-107">The possible values are defined in the [CorSymAddrKind](corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="66c8b-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="66c8b-108">Return Value</span></span>  
 <span data-ttu-id="66c8b-109">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="66c8b-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="66c8b-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="66c8b-110">Requirements</span></span>  
 <span data-ttu-id="66c8b-111">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="66c8b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="66c8b-112">Confira também</span><span class="sxs-lookup"><span data-stu-id="66c8b-112">See also</span></span>

- [<span data-ttu-id="66c8b-113">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="66c8b-113">ISymUnmanagedVariable Interface</span></span>](isymunmanagedvariable-interface.md)
