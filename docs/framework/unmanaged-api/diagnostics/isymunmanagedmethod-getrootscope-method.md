---
title: "Método ISymUnmanagedMethod::GetRootScope"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: e7fe3d2934345fbc89b4a2c7747abb867a20df20
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="isymunmanagedmethodgetrootscope-method"></a><span data-ttu-id="e8d97-102">Método ISymUnmanagedMethod::GetRootScope</span><span class="sxs-lookup"><span data-stu-id="e8d97-102">ISymUnmanagedMethod::GetRootScope Method</span></span>
<span data-ttu-id="e8d97-103">Obtém o escopo léxico raiz dentro desse método.</span><span class="sxs-lookup"><span data-stu-id="e8d97-103">Gets the root lexical scope within this method.</span></span> <span data-ttu-id="e8d97-104">Esse escopo abrange todo o método.</span><span class="sxs-lookup"><span data-stu-id="e8d97-104">This scope encloses the entire method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e8d97-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="e8d97-105">Syntax</span></span>  
  
```  
HRESULT GetRootScope(  
    [out, retval] ISymUnmanagedScope** pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="e8d97-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="e8d97-106">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="e8d97-107">[out] Um ponteiro que está definido para retornado [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="e8d97-107">[out] A pointer that is set to the returned [ISymUnmanagedScope](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedscope-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="e8d97-108">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="e8d97-108">Return Value</span></span>  
 <span data-ttu-id="e8d97-109">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="e8d97-109">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="e8d97-110">Requisitos</span><span class="sxs-lookup"><span data-stu-id="e8d97-110">Requirements</span></span>  
 <span data-ttu-id="e8d97-111">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="e8d97-111">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8d97-112">Consulte também</span><span class="sxs-lookup"><span data-stu-id="e8d97-112">See Also</span></span>  
 [<span data-ttu-id="e8d97-113">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="e8d97-113">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
