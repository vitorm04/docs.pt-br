---
title: Método ISymUnmanagedMethod::GetNamespace
ms.date: 03/30/2017
api_name:
- ISymUnmanagedMethod.GetNamespace
api_location:
- diasymreader.dll
api_type:
- COM
f1_keywords:
- ISymUnmanagedMethod::GetNamespace
helpviewer_keywords:
- ISymUnmanagedMethod::GetNamespace method [.NET Framework debugging]
- GetNamespace method [.NET Framework debugging]
ms.assetid: 7fbbac42-b966-406d-9ae9-67bf3aea74ce
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: a2bba44af50607772f2a52203a47e21d8699f78b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54716138"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="27d12-102">Método ISymUnmanagedMethod::GetNamespace</span><span class="sxs-lookup"><span data-stu-id="27d12-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="27d12-103">Obtém o namespace no qual este método é definido.</span><span class="sxs-lookup"><span data-stu-id="27d12-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="27d12-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="27d12-104">Syntax</span></span>  
  
```  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="27d12-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="27d12-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="27d12-106">[out] Um ponteiro que é definido para retornado [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="27d12-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="27d12-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="27d12-107">Return Value</span></span>  
 <span data-ttu-id="27d12-108">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="27d12-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="27d12-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="27d12-109">Requirements</span></span>  
 <span data-ttu-id="27d12-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="27d12-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="27d12-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="27d12-111">See also</span></span>
- [<span data-ttu-id="27d12-112">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="27d12-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
