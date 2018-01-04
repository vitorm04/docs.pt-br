---
title: "Método ICorThreadpool::CorBindIoCompletionCallback"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorThreadpool.CorBindIoCompletionCallback
api_location: mscoree.dll
api_type: COM
f1_keywords: CorBindIoCompletionCallback
helpviewer_keywords:
- CorBindIoCompletionCallback method [.NET Framework hosting]
- ICorThreadpool::CorBindIoCompletionCallback method [.NET Framework hosting]
ms.assetid: 2b159225-f09c-42f1-aa7c-44087e121249
topic_type: apiref
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 405fd52eb3354384c85049ab5230b08160144b09
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="icorthreadpoolcorbindiocompletioncallback-method"></a><span data-ttu-id="5e3ef-102">Método ICorThreadpool::CorBindIoCompletionCallback</span><span class="sxs-lookup"><span data-stu-id="5e3ef-102">ICorThreadpool::CorBindIoCompletionCallback Method</span></span>
<span data-ttu-id="5e3ef-103">Esse método oferece suporte a infraestrutura do .NET Framework e não se destina a ser usado diretamente do seu código.</span><span class="sxs-lookup"><span data-stu-id="5e3ef-103">This method supports the .NET Framework infrastructure and is not intended to be used directly from your code.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5e3ef-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="5e3ef-104">Syntax</span></span>  
  
```  
HRESULT CorBindIoCompletionCallback (  
    [in] HANDLE                          fileHandle,  
    [in] LPOVERLAPPED_COMPLETION_ROUTINE callback  
);  
```  
  
## <a name="requirements"></a><span data-ttu-id="5e3ef-105">Requisitos</span><span class="sxs-lookup"><span data-stu-id="5e3ef-105">Requirements</span></span>  
 <span data-ttu-id="5e3ef-106">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="5e3ef-106">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="5e3ef-107">**Cabeçalho:** MSCorEE.h</span><span class="sxs-lookup"><span data-stu-id="5e3ef-107">**Header:** MSCorEE.h</span></span>  
  
 <span data-ttu-id="5e3ef-108">**Biblioteca:** incluído como um recurso no MSCOREE</span><span class="sxs-lookup"><span data-stu-id="5e3ef-108">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="5e3ef-109">**Versões do .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="5e3ef-109">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5e3ef-110">Consulte também</span><span class="sxs-lookup"><span data-stu-id="5e3ef-110">See Also</span></span>  
 [<span data-ttu-id="5e3ef-111">Interface ICorThreadpool</span><span class="sxs-lookup"><span data-stu-id="5e3ef-111">ICorThreadpool Interface</span></span>](../../../../docs/framework/unmanaged-api/hosting/icorthreadpool-interface.md)
