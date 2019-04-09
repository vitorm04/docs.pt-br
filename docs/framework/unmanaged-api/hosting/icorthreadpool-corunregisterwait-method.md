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
ms.openlocfilehash: af41a20bcdcbfc44a5a4b0b30947ab9093948291
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59122825"
---
# <a name="icorthreadpoolcorunregisterwait-method"></a><span data-ttu-id="5b7e6-102">Método ICorThreadpool::CorUnregisterWait</span><span class="sxs-lookup"><span data-stu-id="5b7e6-102">ICorThreadpool::CorUnregisterWait Method</span></span>
<span data-ttu-id="5b7e6-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="5b7e6-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5b7e6-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5b7e6-104">Syntax</span></span>  
  
```  
HRESULT CorUnregisterWait (  
    [in] HANDLE hWaitObject,  
    [in] HANDLE CompletionEvent,  
    [out] BOOL* result  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="5b7e6-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5b7e6-105">Requirements</span></span>  
 <span data-ttu-id="5b7e6-106">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5b7e6-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5b7e6-107">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5b7e6-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5b7e6-108">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="5b7e6-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 **<span data-ttu-id="5b7e6-109">Versões do .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="5b7e6-109">.NET Framework Versions:</span></span>** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="5b7e6-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5b7e6-110">See also</span></span>

- [<span data-ttu-id="5b7e6-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="5b7e6-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
