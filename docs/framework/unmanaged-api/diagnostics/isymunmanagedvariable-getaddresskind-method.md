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
ms.openlocfilehash: 4d2de38e5e506873a6db262dcec19c7af9d8a0d0
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74446100"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="44e4b-102">Método ISymUnmanagedVariable::GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="44e4b-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="44e4b-103">Obtém o tipo de endereço dessa variável.</span><span class="sxs-lookup"><span data-stu-id="44e4b-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="44e4b-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="44e4b-104">Syntax</span></span>  
  
```cpp  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="44e4b-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="44e4b-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="44e4b-106">fora Um ponteiro para um `ULONG32` que recebe o valor.</span><span class="sxs-lookup"><span data-stu-id="44e4b-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="44e4b-107">Os valores possíveis são definidos na enumeração [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) .</span><span class="sxs-lookup"><span data-stu-id="44e4b-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="44e4b-108">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="44e4b-108">Return Value</span></span>  
 <span data-ttu-id="44e4b-109">S_OK se o método tiver sucesso; caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="44e4b-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="44e4b-110">{1&gt;{2&gt;Requisitos&lt;2}&lt;1}</span><span class="sxs-lookup"><span data-stu-id="44e4b-110">Requirements</span></span>  
 <span data-ttu-id="44e4b-111">**Cabeçalho:** CorSym. idl, CorSym. h</span><span class="sxs-lookup"><span data-stu-id="44e4b-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="44e4b-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="44e4b-112">See also</span></span>

- [<span data-ttu-id="44e4b-113">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="44e4b-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
