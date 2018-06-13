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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1c3c5d4425b4851bbc0dbf1d98a0e3eec40b87a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33436852"
---
# <a name="icorthreadpoolcorunregisterwait-method"></a><span data-ttu-id="7d4bd-102">Método ICorThreadpool::CorUnregisterWait</span><span class="sxs-lookup"><span data-stu-id="7d4bd-102">ICorThreadpool::CorUnregisterWait Method</span></span>
<span data-ttu-id="7d4bd-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="7d4bd-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d4bd-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7d4bd-104">Syntax</span></span>  
  
```  
HRESULT CorUnregisterWait (  
    [in] HANDLE hWaitObject,  
    [in] HANDLE CompletionEvent,  
    [out] BOOL* result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="7d4bd-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7d4bd-105">Requirements</span></span>  
 <span data-ttu-id="7d4bd-106">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d4bd-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d4bd-107">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="7d4bd-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="7d4bd-108">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="7d4bd-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="7d4bd-109">**Versões do .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7d4bd-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d4bd-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7d4bd-110">See Also</span></span>  
 [<span data-ttu-id="7d4bd-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="7d4bd-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
