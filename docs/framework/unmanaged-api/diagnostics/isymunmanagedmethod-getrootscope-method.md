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
ms.openlocfilehash: 7c77be0dde950693d3943e41c392dcdcd9bc995e
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59096069"
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="05f9d-102">Método ISymUnmanagedMethod::GetRootScope</span><span class="sxs-lookup"><span data-stu-id="05f9d-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="05f9d-103">Obtém o escopo do léxico raiz dentro desse método.</span><span class="sxs-lookup"><span data-stu-id="05f9d-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="05f9d-104">Esse escopo abrange todo o método.</span><span class="sxs-lookup"><span data-stu-id="05f9d-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05f9d-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="05f9d-105">Syntax</span></span>  
  
```  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="05f9d-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="05f9d-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="05f9d-107">[out] Um ponteiro que é definido para retornado [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="05f9d-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="05f9d-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="05f9d-108">Return Value</span></span>  
 <span data-ttu-id="05f9d-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="05f9d-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="05f9d-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="05f9d-110">Requirements</span></span>  
 <span data-ttu-id="05f9d-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="05f9d-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="05f9d-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="05f9d-112">See also</span></span>

- [<span data-ttu-id="05f9d-113">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="05f9d-113">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
