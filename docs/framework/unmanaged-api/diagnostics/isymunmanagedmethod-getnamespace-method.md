---
title: "Método ISymUnmanagedMethod::GetNamespace"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ISymUnmanagedMethod.GetNamespace
api_location: diasymreader.dll
api_type: COM
f1_keywords: ISymUnmanagedMethod::GetNamespace
helpviewer_keywords:
- ISymUnmanagedMethod::GetNamespace method [.NET Framework debugging]
- GetNamespace method [.NET Framework debugging]
ms.assetid: 7fbbac42-b966-406d-9ae9-67bf3aea74ce
topic_type: apiref
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 5aff1bcd98e67f381340ed81a187db591c0986be
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="isymunmanagedmethodgetnamespace-method"></a><span data-ttu-id="6f523-102">Método ISymUnmanagedMethod::GetNamespace</span><span class="sxs-lookup"><span data-stu-id="6f523-102">ISymUnmanagedMethod::GetNamespace Method</span></span>
<span data-ttu-id="6f523-103">Obtém o namespace no qual esse método é definido.</span><span class="sxs-lookup"><span data-stu-id="6f523-103">Gets the namespace within which this method is defined.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f523-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="6f523-104">Syntax</span></span>  
  
```  
HRESULT GetNamespace(  
   [out] ISymUnmanagedNamespace  **pRetVal);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="6f523-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="6f523-105">Parameters</span></span>  
 `pRetVal`  
 <span data-ttu-id="6f523-106">[out] Um ponteiro que está definido para retornado [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span><span class="sxs-lookup"><span data-stu-id="6f523-106">[out] A pointer that is set to the returned [ISymUnmanagedNamespace](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagednamespace-interface.md) interface.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="6f523-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="6f523-107">Return Value</span></span>  
 <span data-ttu-id="6f523-108">S_OK se o método for bem-sucedido; Caso contrário, E_FAIL ou algum outro código de erro.</span><span class="sxs-lookup"><span data-stu-id="6f523-108">S_OK if the method succeeds; otherwise, E_FAIL or some other error code.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="6f523-109">Requisitos</span><span class="sxs-lookup"><span data-stu-id="6f523-109">Requirements</span></span>  
 <span data-ttu-id="6f523-110">**Cabeçalho:** CorSym.idl, CorSym.h</span><span class="sxs-lookup"><span data-stu-id="6f523-110">**Header:** CorSym.idl, CorSym.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6f523-111">Consulte também</span><span class="sxs-lookup"><span data-stu-id="6f523-111">See Also</span></span>  
 [<span data-ttu-id="6f523-112">Interface ISymUnmanagedMethod</span><span class="sxs-lookup"><span data-stu-id="6f523-112">ISymUnmanagedMethod Interface</span></span>](../../../../docs/framework/unmanaged-api/diagnostics/isymunmanagedmethod-interface.md)
