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
ms.openlocfilehash: 458f6ab4a6848ce6921542ca62fe6d5c7cf4719f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54704635"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="bbcb3-102">Método ISymUnmanagedMethod::GetRootScope</span><span class="sxs-lookup"><span data-stu-id="bbcb3-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="bbcb3-103">Obtém o escopo do léxico raiz dentro desse método.</span><span class="sxs-lookup"><span data-stu-id="bbcb3-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="bbcb3-104">Esse escopo abrange todo o método.</span><span class="sxs-lookup"><span data-stu-id="bbcb3-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="bbcb3-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="bbcb3-105">Syntax</span></span>  
  
```  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="bbcb3-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="bbcb3-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="bbcb3-107">[out] Um ponteiro que é definido para retornado [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="bbcb3-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="bbcb3-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="bbcb3-108">Return Value</span></span>  
 <span data-ttu-id="bbcb3-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="bbcb3-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="bbcb3-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="bbcb3-110">Requirements</span></span>  
 <span data-ttu-id="bbcb3-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="bbcb3-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bbcb3-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="bbcb3-112">See also</span></span>
- [<span data-ttu-id="bbcb3-113">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="bbcb3-113">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
