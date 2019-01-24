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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: f5b4cb07cbc1ea3f8f297b96a124b8f5a04f0fce
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54647264"
---
# <a name="isymunmanagedvariablegetaddresskind-method"></a><span data-ttu-id="09e1c-102">Método ISymUnmanagedVariable::GetAddressKind</span><span class="sxs-lookup"><span data-stu-id="09e1c-102">ISymUnmanagedVariable::GetAddressKind Method</span></span>
<span data-ttu-id="09e1c-103">Obtém o tipo de endereço dessa variável.</span><span class="sxs-lookup"><span data-stu-id="09e1c-103">Gets the kind of address of this variable.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="09e1c-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="09e1c-104">Syntax</span></span>  
  
```  
HRESULT GetAddressKind(  
    [out, retval] ULONG32* pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="09e1c-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="09e1c-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="09e1c-106">[out] Um ponteiro para um `ULONG32` que recebe o valor.</span><span class="sxs-lookup"><span data-stu-id="09e1c-106">[out] A pointer to a `ULONG32` that receives the value.</span></span> <span data-ttu-id="09e1c-107">Os valores possíveis são definidos na [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeração.</span><span class="sxs-lookup"><span data-stu-id="09e1c-107">The possible values are defined in the [CorSymAddrKind](../../../../docs/framework/unmanaged-api/diagnostics/corsymaddrkind-enumeration.md) enumeration.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="09e1c-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="09e1c-108">Return Value</span></span>  
 <span data-ttu-id="09e1c-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="09e1c-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="09e1c-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="09e1c-110">Requirements</span></span>  
 <span data-ttu-id="09e1c-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="09e1c-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09e1c-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="09e1c-112">See also</span></span>
- [<span data-ttu-id="09e1c-113">Interface ISymUnmanagedVariable</span><span class="sxs-lookup"><span data-stu-id="09e1c-113">ISymUnmanagedVariable Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedvariable-interface.md)
