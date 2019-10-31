---
title: Método ICorThreadpool::CorUnregisterWait
ms.date: 03/30/2017
api_name:
- ICorThreadpool.CorUnregisterWait
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CorUnregisterWait
helpviewer_keywords:
- CorUnregisterWait method [.NET Framework hosting]
- ICorThreadpool::CorUnregisterWait method [.NET Framework hosting]
ms.assetid: 42c933f1-30a8-4011-bdea-e117f3c3265e
topic_type:
- apiref
ms.openlocfilehash: 431b90f8c5db5f40bf50be0b03fa315c6ea15ef7
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73133196"
---
# <a name="icorthreadpoolcorunregisterwait-method"></a><span data-ttu-id="1432f-102">Método ICorThreadpool::CorUnregisterWait</span><span class="sxs-lookup"><span data-stu-id="1432f-102">ICorThreadpool::CorUnregisterWait Method</span></span>
<span data-ttu-id="1432f-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="1432f-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1432f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1432f-104">Syntax</span></span>  
  
```cpp  
HRESULT CorUnregisterWait (  
    [in] HANDLE hWaitObject,  
    [in] HANDLE CompletionEvent,  
    [out] BOOL* result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="1432f-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1432f-105">Requirements</span></span>  
 <span data-ttu-id="1432f-106">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="1432f-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="1432f-107">**Cabeçalho:** MSCorEE. h</span><span class="sxs-lookup"><span data-stu-id="1432f-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="1432f-108">**Biblioteca:** Incluído como um recurso em MSCorEE. dll</span><span class="sxs-lookup"><span data-stu-id="1432f-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="1432f-109">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="1432f-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1432f-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1432f-110">See also</span></span>

- [<span data-ttu-id="1432f-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="1432f-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
