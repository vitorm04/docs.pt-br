---
title: Método ISymUnmanagedMethod::GetRootScope
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetRootScope
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetRootScope
helpviewer_keywords:
- ISymUnmanagedMethod::GetRootScope method [.NET Framework debugging]
- GetRootScope method [.NET Framework debugging]
ms.assetid: 7d58caac-2e75-4dfa-9249-32d8a624b247
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 8956d72d25f240eff653d3eefb92b68431f4e2ae
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67771774"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="97d98-102">Método ISymUnmanagedMethod::GetRootScope</span><span class="sxs-lookup"><span data-stu-id="97d98-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="97d98-103">Obtém o escopo do léxico raiz dentro desse método.</span><span class="sxs-lookup"><span data-stu-id="97d98-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="97d98-104">Esse escopo abrange todo o método.</span><span class="sxs-lookup"><span data-stu-id="97d98-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="97d98-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="97d98-105">Syntax</span></span>  
  
```cpp  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="97d98-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="97d98-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="97d98-107">[out] Um ponteiro que é definido para retornado [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="97d98-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="97d98-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="97d98-108">Return Value</span></span>  
 <span data-ttu-id="97d98-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="97d98-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="97d98-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="97d98-110">Requirements</span></span>  
 <span data-ttu-id="97d98-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="97d98-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="97d98-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="97d98-112">See also</span></span>

- [<span data-ttu-id="97d98-113">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="97d98-113">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
