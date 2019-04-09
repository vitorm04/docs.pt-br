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
ms.openlocfilehash: cfd466f48a55f8b8905f6c76cf876fb8a32d4a8f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59151392"
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="90edd-102">Método ISymUnmanagedMethod::GetNamespace</span><span class="sxs-lookup"><span data-stu-id="90edd-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="90edd-103">Obtém o namespace no qual este método é definido.</span><span class="sxs-lookup"><span data-stu-id="90edd-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90edd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="90edd-104">Syntax</span></span>  
  
```  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
## <a name="parameters"></a><span data-ttu-id="90edd-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="90edd-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="90edd-106">[out] Um ponteiro que é definido para retornado [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="90edd-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="90edd-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="90edd-107">Return Value</span></span>  
 <span data-ttu-id="90edd-108">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="90edd-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="90edd-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="90edd-109">Requirements</span></span>  
 <span data-ttu-id="90edd-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="90edd-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="90edd-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="90edd-111">See also</span></span>

- [<span data-ttu-id="90edd-112">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="90edd-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
